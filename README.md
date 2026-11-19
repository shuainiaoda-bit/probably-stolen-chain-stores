# 深空当铺：连锁店 / Chain Stores

《深空当铺：可能是偷的》的直营连锁经营 Mod，作者：是大帅鸟。

当前版本：**0.1.6 开发预览版**。支持默认公开版 **Build26525552** 和 open_beta **Build26772488 / 1.0.0.16**，使用官方 ModReflect 和可选 Mod 服务接口。

## 0.1.6 兼容更新

同一份安装包支持默认公开版 Build26525552 和 open_beta Build26772488（1.0.0.16）。已完成两个分支的后台静音实机回归。请在游戏原生 Mod 菜单确认本机授权，并在更新前备份存档。

English: The same package supports public Build26525552 and open_beta Build26772488 (1.0.0.16). Silent native runtime checks passed on both branches. Confirm permissions through the native Mod menu and back up saves before updating.

## 下载与安装

从 [Releases](https://github.com/shuainiaoda-bit/probably-stolen-chain-stores/releases) 下载 `ChainStores-0.1.6.zip`。先备份存档并退出游戏，再将包内的 `ChainStores` 文件夹放入游戏目录的 `Mods` 文件夹，在游戏原生 Mod 菜单启用。同一 Mod 只启用一个来源；从工坊版切换时先停用工坊版。更新时替换原安装文件，保留游戏存档。

买下原店后，点击主界面上方“连锁经营”，考察并租赁或买下店面。新店首次转入至少 10000 信用点，招聘一名交易员后开业。进入门店搬货、装修和设置买卖类别，睡前管理后点击“下一天”结算。

每家分店分别保存资金、库存、员工和势力声望。支持原版普通顾客、6 种原创买卖顾客、装修升级及独立展览柜。界面和经营说明支持游戏全部 11 种语言。

## 0.1.5 更新

- 连锁经营 → 设置 → 调整位置，可拖动主店入口，保存、取消或恢复默认；重启后保留位置。
- 成交流水改为表格，按日期和买入、卖出、易货筛选，分页查看物品、数量、成交金额、报价和顾客。详细经营收支和事件仍可展开。
- 递归识别各类容器、背包、储藏设备及其多页、多层内容物，内容物可单独参与交易。购入整箱时一并转移所有权并分配成本。
- 仓库满时尝试使用已有容器的空位，遵守原版容量、物品类型、上锁和取出限制。固定容器可保留本体，内容物仍可交易；固定内容物也会阻止其随外层容器出售。
- 修复取消容器采购时的所有权回滚；内容物成本随跨店搬运和存读档保留。进入门店后，Esc 优先关闭内容物窗口。

## 排列方式

每家店可选择原版四种持续排列。第三方排列通过官方可选服务或 `ChainStores.Sorting.Register` 提供完成通知。旧选择保留；未接入完成接口的排序 Mod 使用原版入库，原版容器菜单中的手动功能仍由对应 Mod 提供。

校验值见随安装包发布的 `SHA256SUMS.txt`。反馈：QQ群 **1129395905** 或原工坊评论区。

[原 Steam 工坊页面](https://steamcommunity.com/sharedfiles/filedetails/?id=3840545624)

## English

Chain Stores adds directly operated branches to Probably Stolen. Version **0.1.5** supports game **1.0.0.15 and 1.0.0.16** with the official ModReflect and optional-mod service APIs.

Download `ChainStores-0.1.6.zip` from Releases. Back up your save, exit the game and copy the included `ChainStores` folder into the game's `Mods` directory. Enable it in the native Mod menu. Use one installation source at a time. Replace the installed files when updating and retain your game saves.

After buying the original shop, open Chain Management, inspect premises, rent or buy a branch, transfer at least 10000 credits and hire a trader. Visit branches to move stock, decorate and set trading policies. Complete management before advancing to the next day. Branches have independent cash, inventory, staff and faction reputations. Includes ordinary native customers, six original customers, upgrades and showcases. Supports all 11 game languages.

### Changes in 0.1.5

- Open Settings in Chain Management to drag and save the main-shop entry position, cancel a move or restore the default.
- The trade ledger now has aligned columns, date and direction filters, and pagination. Item, quantity, amount, quote and customer are shown together; detailed business events remain available.
- Container contents are discovered recursively across bags, storage devices, multiple tabs and nested containers. Contents can trade individually. Buying a filled container transfers ownership and allocates its cost across the contents.
- When the warehouse is full, intake can use free space in owned containers. Native capacity, type, lock and removal rules apply. Pin a container to retain its shell while trading the contents. Pinned cargo also prevents its enclosing container from being sold with it.
- Cancelled container intake restores ownership. Costs follow cargo through transfers and save reloads. Escape closes a container window before leaving a branch.

Four vanilla continuous arrangements are available. Optional sorting providers must supply a completion routine through the official service or registration API. Saved preferences are retained. Unadapted providers use vanilla intake; manual sorting in native container menus remains provided by each sorting mod.

This is a development preview. Brand franchises are planned for a later release. Report bugs in Workshop comments or QQ group **1129395905**.
