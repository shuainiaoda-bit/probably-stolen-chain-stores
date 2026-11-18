# 排列逻辑与Mod接入

进入直营店，点击“排布逻辑”。每家店分别保存排列方式，买入、易货和手动搬货后持续使用。原版四种排列始终可选，自动旋转沿用游戏设置。也可以直接在本店仓库的容器排列菜单中选择方式。

## 容器菜单兼容

0.1.4 使用官方 `ModReflect` 和 `ModHelper.Expose/Lookup`，需要游戏 1.0.0.15。菜单中的扩展按钮通过游戏 UI 对象及官方反射接口识别。算法提供下方的完成协程后，可选作持续排列方式。未注册的菜单项显示为不可选，玩家仍可在原版容器菜单手动使用该 Mod。原版撤销排列不作为持续规则。

连续入库会合并排布请求，满仓先检查容量。扩展排序在隐藏容器中的真实物品副本上运行，每帧最多准备或清理8件副本，并按约3毫秒的阶段预算让出主线程；单件复杂物品的原生加载需要完整执行。预览容器保留原版边界掩码，使用轻量背景。副本拥有独立编号，算法完成后核对数量、状态、内容物、固定物品和布局边界，仅将位置与朝向应用到原库存。等待期间原库存变化时，该结果作废，下一次按新库存整理。真实商品、现金和成本不交给扩展算法修改。

旧版通过读取其他 Mod 的私有忙碌字段等待算法结束；官方新权限规则要求可选 Mod 通过协作接口提供完成通知。更好的库存排序等尚未注册完成接口的版本，需要排序 Mod 作者接入后才能持续排列。已有排序 ID 和显示名保留，收货继续使用原版布局；提供相同菜单按钮名称的适配器注册后，旧菜单 ID 可自动恢复。同步算法也需注册，执行后直接结束协程。

算法找不到、超时、抛出异常或返回无效布局时，保留当前真实库存和已选方式。入库容量由原版布局计算，货物完整放入后再交给扩展算法排序；这一步不会使用第三方算法扩大可收购容量。未启用排序Mod时，可以正常开店和收货。

正式包的能力声明为空，游戏原生扫描无额外能力要求。连锁店独立运行，其他排序 Mod 按需启用。

## 官方可选服务接口

排序 Mod 无需引用连锁店 DLL 或建立工坊依赖。双方启用后，通过官方服务注册：

```csharp
var register = ModHelper.Lookup<
    Action<string, string, string, Func<GameGridInventory, IEnumerator>, string>>(
        "chain_stores", "sorting.register");

register?.Invoke("your_mod_id", "arrangement", "我的排列方式",
    inventory => ArrangeAndWait(inventory), "stable_menu_button_name");

// 停用时：
ModHelper.Lookup<Action<string, string>>(
    "chain_stores", "sorting.unregister")?.Invoke("your_mod_id", "arrangement");
```

服务 `sorting.version` 为字符串 `"1"`。最后一个参数用于关联菜单按钮及旧存档；没有按钮时传 `null`。同一 ID 再次注册会更新算法。`Lookup` 由游戏检查双方能力。双方启用顺序不同时，注册方可在服务出现后重试。停用的服务注册方会从可选列表移除。

## 协程接口

Mod在启用时注册，在停用时注销。ID应包含作者或Mod命名空间，保持跨版本稳定。

```csharp
ChainStores.Sorting.Register(
    "author.mod.arrangement",
    "我的排列方式",
    inventory => ArrangeAndWait(inventory));

// 关联原版菜单按钮及旧版保存的菜单选择：
ChainStores.Sorting.RegisterMenu("author.mod.menu", "我的菜单排列",
    "stable_menu_button_name", inventory => ArrangeAndWait(inventory));

// 停用时：
ChainStores.Sorting.Unregister("author.mod.arrangement");
```

`ArrangeAndWait` 返回 `IEnumerator`。传入的是隐藏的副本容器，协程应在算法真正完成后结束。同步算法可在执行后直接 `yield break`；异步算法可以启动任务并等待完成。允许调整根物品的位置和朝向，固定物品保持原位。新增、移除、合并、拆分商品或修改内容物的结果会被拒绝。

连锁店按门店串行安排任务，默认等待上限为60秒。回调使用Unity主线程；后台计算完成后，应回到主线程更新副本容器。注册方负责结束自己的后台任务。

## 存档

`StockOrder` 保存原版保底排列；`StockSorter` 保存扩展方式ID；`StockSorterLabel` 保存显示名。旧档默认采用原版大件优先排列，保持原有已保存坐标。扩展暂时不可用时保留其ID，重新启用后可以继续选择和使用。
