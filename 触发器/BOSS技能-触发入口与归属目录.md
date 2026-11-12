# BOSS 技能：触发入口与归属定位

用途：后续查找 BOSS 技能时，先区分是谁造成伤害、谁受到伤害以及技能标识存放在谁身上。2026-11-12 对当前源码备份的 `BOSS技能`、`存档BOSS` 两个分类逐项通过 MCP 只读核对入口；不含其他类别中的怪物技能、Debuff 和 BOSS 挑战逻辑。

共检查到 43 个启用触发：两个是技能数组初始化，其余 41 个列于下表。伤害事件使用 `JYDamageEvent` 时，“伤害来源”表示入口检查 `GetEventDamageSource()` 身上的技能；“受伤单位”表示入口检查 `GetTriggerUnit()` 身上的技能；攻击事件检查 `GetAttacker()`。这只描述入口过滤，冷却、目标、最终伤害和内部动作需要另行追踪；`入口清点` 不表示该技能已学会。表格标识仅适用于本源码，目标图须重新核对。

| 分类 | 触发器 | 入口事件 | 检查技能的单位 | 源码技能数组 | 学习状态 |
| --- | --- | --- | --- | --- | --- |
| BOSS技能 | BOSSC0（招老弟） | 伤害事件 | 伤害来源 | BOSS_JN3[0] | 入口清点 |
| BOSS技能 | BOSSA1（冲击波） | 伤害事件 | 伤害来源 | BOSS_JN1[1] | 部分链路 |
| BOSS技能 | BOSSA2（丢个炸弹晕） | 伤害事件 | 伤害来源 | BOSS_JN1[2] | 入口清点 |
| BOSS技能 | BOSSA3（直线眩晕） | 伤害事件 | 伤害来源 | BOSS_JN1[3] | 入口清点 |
| BOSS技能 | BOSSA4（圆圈炸晕） | 伤害事件 | 伤害来源 | BOSS_JN1[4] | 部分链路 |
| BOSS技能 | BOSSA5（圆圈炸晕2次） | 伤害事件 | 伤害来源 | BOSS_JN1[5] | 入口清点 |
| BOSS技能 | BOSSA6（直线眩晕3条） | 伤害事件 | 伤害来源 | BOSS_JN1[6] | 入口清点 |
| BOSS技能 | BOSSA7（本多无敌） | 伤害事件 | 受伤单位 | BOSS_JN1[7] | 部分链路 |
| BOSS技能 | BOSSA8（三道魔气） | 伤害事件 | 伤害来源 | BOSS_JN1[8] | 入口清点 |
| BOSS技能 | BOSSA9（捶地三次） | 伤害事件 | 伤害来源 | BOSS_JN1[9] | 入口清点 |
| BOSS技能 | BOSSA10（回旋镖发出去停顿几秒） | 伤害事件 | 伤害来源 | BOSS_JN1[10] | 部分链路 |
| BOSS技能 | BOSSA11（直线3次依次出现） | 伤害事件 | 伤害来源 | BOSS_JN1[11] | 入口清点 |
| BOSS技能 | BOSSA12（喷火） | 伤害事件 | 伤害来源 | BOSS_JN1[12] | 入口清点 |
| BOSS技能 | BOSSA13（猿王撼地） | 伤害事件 | 受伤单位 | BOSS_JN1[13] | 入口清点 |
| BOSS技能 | BOSSA14（牛牛弹射） | 伤害事件 | 伤害来源 | BOSS_JN1[14] | 部分链路 |
| BOSS技能 | BOSSA15（黑刹玄阵） | 伤害事件 | 受伤单位 | BOSS_JN1[15] | 部分链路 |
| BOSS技能 | BOSSA16（发动攻击停止） | 被攻击事件 | 攻击者 | BOSS_JN1[16] | 入口清点 |
| BOSS技能 | BOSSA16（整合技） | 伤害事件 | 伤害来源 | BOSS_JN1[16] | 入口清点 |
| BOSS技能 | BOSSA17（时光之门） | 伤害事件 | 受伤单位 | BOSS_JN1[17] | 部分链路 |
| BOSS技能 | BOSSA18（剑影留痕） | 伤害事件 | 伤害来源 | BOSS_JN1[18] | 入口清点 |
| BOSS技能 | BOSSA19（树界） | 伤害事件 | 伤害来源 | BOSS_JN1[19] | 入口清点 |
| BOSS技能 | BOSSA20（无天） | 伤害事件 | 伤害来源 | BOSS_JN1[20] | 入口清点 |
| BOSS技能 | BOSSA101（天门落剑） | 伤害事件 | 伤害来源 | BOSS_JN1[101] | 部分链路 |
| BOSS技能 | BOSSA102（天门直线） | 伤害事件 | 伤害来源 | BOSS_JN1[102] | 入口清点 |
| BOSS技能 | BOSSA103（自身大范围） | 伤害事件 | 伤害来源 | BOSS_JN1[103] | 入口清点 |
| 存档BOSS | CundangBOSSA1（冲击波） | 伤害事件 | 伤害来源 | BOSSCD_JN1[1] | 入口清点 |
| 存档BOSS | CundangBOSSA2（圆圈爆炸） | 伤害事件 | 伤害来源 | BOSSCD_JN1[2] | 入口清点 |
| 存档BOSS | CundangBOSSA3（捶地2次） | 伤害事件 | 伤害来源 | BOSSCD_JN1[3] | 入口清点 |
| 存档BOSS | CundangBOSSA4（圈和直线依次出现） | 伤害事件 | 伤害来源 | BOSSCD_JN1[4] | 入口清点 |
| 存档BOSS | CundangBOSSA5（受伤每秒回血） | 伤害事件 | 受伤单位 | BOSSCD_JN1[5] | 部分链路 |
| 存档BOSS | CundangBOSSA6（捶地3次） | 伤害事件 | 伤害来源 | BOSSCD_JN1[6] | 入口清点 |
| 存档BOSS | CundangBOSSA7（冲击波） | 伤害事件 | 伤害来源 | BOSSCD_JN1[7] | 入口清点 |
| 存档BOSS | CundangBOSSA8（冲击波） | 伤害事件 | 伤害来源 | BOSSCD_JN1[8] | 入口清点 |
| 存档BOSS | CundangBOSSA9（前方多方向圈炸） | 伤害事件 | 伤害来源 | BOSSCD_JN1[9] | 入口清点 |
| 存档BOSS | N5Debuff14（剑客剑气） | 伤害事件 | 伤害来源 | JN_Debuff[14] | 入口清点 |
| 存档BOSS | zzzz1（灾厄之眼） | 伤害事件 | 伤害来源 | BOSSCD_JN2[1] | 部分链路 |
| 存档BOSS | zzzz2（灾厄魔爪） | 伤害事件 | 伤害来源 | BOSSCD_JN2[2] | 部分链路 |
| 存档BOSS | zzzz3（圆圈爆炸） | 伤害事件 | 伤害来源 | BOSSCD_JN3[1] | 入口清点 |
| 存档BOSS | zzzz4（受伤圆圈爆炸） | 伤害事件 | 受伤单位 | BOSSCD_JN3[1] | 部分链路 |
| 存档BOSS | CundangBOSSD2（冲击波） | 伤害事件 | 伤害来源 | BOSSCD_JN4[2] | 入口清点 |
| 存档BOSS | CundangBOSSD3（圆圈爆炸） | 伤害事件 | 伤害来源 | BOSSCD_JN4[3] | 部分链路 |

初始化分别由 `BossJN_Set` 和 `BossCundangJN_Set` 建立技能数组。特别注意：普通 BOSS 的 `BOSSA16` 有被攻击事件和伤害事件两个不同触发器；仙界秘宝 `zzzz3` 与 `zzzz4` 使用相同数组项，但前者检查伤害来源，后者检查受伤单位。`CundangBOSSD3` 检查伤害来源，不能只凭“圆圈爆炸”判断是受伤触发。

有关冷却、伤害、命中组、怪物死亡后的法阵、玩家归属和计时器，参见[技能机制规范](技能机制-叠层状态召唤与BOSS.md)及[多目标与法阵规范](技能制作-多目标选取与冰冻法阵.md)。此清点不等于 GUI 逻辑、伤害先后、保存重开或多人游戏验证。


