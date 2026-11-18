# 深空当铺：连锁店 / Chain Stores

《深空当铺：可能是偷的》的直营连锁经营 Mod，作者：是大帅鸟。

当前版本：**0.1.4 开发预览版**。需要游戏 **1.0.0.15** 及其官方 ModReflect、Mod 服务接口。

## 下载与安装

从 [Releases](https://github.com/shuainiaoda-bit/probably-stolen-chain-stores/releases) 下载 `ChainStores-0.1.4.zip`。先备份存档，退出游戏，再将压缩包内的 `ChainStores` 文件夹放入游戏目录的 `Mods` 文件夹。在游戏原生 Mod 菜单启用。同一 Mod 只启用一个来源；从工坊版切换时先停用工坊版。

买下原店后，点击主界面上方“连锁经营”，考察并租赁或买下店面。每家新店首次转入至少 10000 信用点，招聘一名交易员后开业。进入门店搬货、装修和设置买卖类别，睡前管理后点击“下一天”结算。

每家分店分别保存资金、库存、员工和势力声望。支持原版普通顾客、6 种原创买卖顾客、装修升级及独立展览柜。界面和经营说明支持游戏全部 11 种语言。

## 0.1.4 更新

- 动态游戏成员访问改用官方 ModReflect，正式包声明和扫描得到的额外能力均为空。
- 原版四种持续排列保留；第三方排列通过官方可选服务或原有协程接口提供完成通知。
- 旧存档的排列选择保留。未接入完成接口的排序 Mod 暂时使用原版入库；它们在原版容器菜单中的手动功能仍由对应 Mod 提供。更好的库存排序旧版需要作者接入完成接口后才能自动持续排列。
- 物品副本完成校验后只应用位置，保留数量、状态、内容物、固定物品和购入成本。

校验文件 `SHA256SUMS.txt` 与安装包一同发布。问题反馈：QQ群 **1129395905**，或在原 Steam 工坊评论区留言。

[原 Steam 工坊页面](https://steamcommunity.com/sharedfiles/filedetails/?id=3840545624)

## English

Chain Stores adds directly operated branches to Probably Stolen. Version **0.1.4** requires game **1.0.0.15** with the official ModReflect and optional-mod service APIs.

Download `ChainStores-0.1.4.zip` from Releases. Back up your save, exit the game, and copy the included `ChainStores` folder into the game's `Mods` directory. Enable it in the native Mod menu. Enable only one source of the mod at a time.

After buying your original shop, open Chain Management, inspect premises, rent or buy a branch, transfer at least 10000 credits and hire a trader. Visit branches to move stock, decorate and set trading policies. Complete management before advancing to the next day.

Branches have independent cash, stock, staff and faction reputations. Includes ordinary native customers, six original customers, upgrades and showcases. Supports all 11 game languages.

This release replaces dynamic reflection with the official API; the production manifest and native scanner report no extra capabilities. Four vanilla arrangements remain available. Optional sorting providers must supply a completion routine through the official service or the existing registration API. Unadapted sorting mods, including older Better Inventory Sorting versions, use vanilla intake until their authors add the adapter. Saved preferences are retained. Manual sorting in the native container menu remains provided by each sorting mod.

This is a development preview. Brand franchises are planned for a later release. Report bugs in the Workshop comments or QQ group **1129395905**.
