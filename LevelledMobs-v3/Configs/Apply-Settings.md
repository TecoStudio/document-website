```
此页面最后更新于 3.9.0 b726
```

---

以下的示例展示了包含了多种不同条件的自定义等级获取的策略

```yml
apply-settings:
  baby-mobs-inherit-adult-setting: true
  creature-death-nametag: '%tiered%Lvl %mob-lvl%&8 | &f%entity-name%'
  death-messages:
    1: ['%player% was killed by %death_nametag%!']
  creeper-max-damage-radius: 3
  level-inheritance: true
  maxLevel: 25
  minLevel: 1
  nametag: '&8&l༺ %tiered%Lvl %mob-lvl%&8 | &f%displayname%&8 | &f%entity-health-rounded% %tiered%%heart_symbol% &r%health-indicator% &8&l༻'
  nametag-always-visible-time: 4000
  nametag-placeholder-unlevelled: ''
  nametag-placeholder-levelled: ''
  nametag-visibility-method: ['TARGETED', 'TRACKING', 'ATTACKED']
  nbt-data: ''
  sunlight-intensity: 5
  passenger-match-level: true
  use-custom-item-drops-for-mobs: false
  use-droptable-id: ''
  lock-entity: false

  entity-name-override:
    SKELETON: 'Jack Skellington'
    all_entities: 'Spawner %displayname%'

  entity-name-override:
    LVL-LVL:
      SKELETON: ['Verta Brae', 'Billy Bones']

  health-indicator:
    indicator: '█'
    indicator-half: '▌'
    scale: 4
    max: 5
    colored-tiers:
      tier-1: '&#22E76B' #绿色
      tier-2: '&#528CFF' #蓝色
      tier-3: '&#FFCD56' #黄色
      tier-4: '&#FE803C' #橙色
      tier-5: '&#F2003D' #红色
      tier-6: '&#B447FF' #紫色
      tier-#: 'color'
      default: '&#FFFFFF' #白色
    merge: true

    multipliers:
#     堆叠乘数
      use-stacked: true
      max-health: ['5.0', 'STACKED']
#     所有实体/默认属性
      max-health: 5.0
      movement-speed: 0.15
      attack-damage: 2.25
      ranged-attack-damage: 2.0
      creeper-blast-damage: 1.0
      follow-range: 0
      item-drop: 3
      xp-drop: 5
#     特殊增益（最小值 0.0 - 最大值 1.0 ）
      armor-bonus: 0.25
      armor-toughness: 0.15
      attack-knockback: 0.25
      knockback-resistance: 0.2
      zombie-spawn-reinforcements: 0.25

      vanilla-bonus: ['']

      custom-mob-level:
        EntityType:
          max-health: 5.0
          movement-speed: 0.15
          attack-damage: 2.25
          ranged-attack-damage: 2.0
          creeper-blast-damage: 1.0
          item-drop: 3
          xp-drop: 5
    tiered-coloring:
      1-5: '&#22E76B' #绿色
      6-10: '&#528CFF' #蓝色
      11-15: '&#FFCD56' #黄色
      16-20: '&#F2003D' #红色
      21-25: '&#B447FF' #紫色
      LVL-LVL: 'color'
      default: '&#FFFFFF' #白色

    maximum-death-in-chunk-threshold: 0
    max-adjacent-chunks: 3
    chunk-max-cooldown-seconds: 300
    disable-vanilla-drops-on-chunk-max: false

    spawner-particles: 'SOUL'
    spawner-particles-count: 10
```

> ### 这是计算默认增益时使用的公式。<br />
>
> newValue = defaultValue + (( defaultValue x configValue ) x ( entityLevel / maxLevel ))

> ### 这是计算特殊增益时使用的公式。<br />
>
> newValue = (entityLevel / maxLevel) x (attributeMax x configValue)
>
> 根据游戏中可能的最大值，对`attributeMax`进行硬编码以反映以下内容。
>
> `armor-bonus:` - 30.0 <br /> > `armor-toughness:` - 20.0 <br /> > `attack_knockback:` - 5.0 <br /> > `knockback_resistance:` - 1.0 <br /> > `zombie-spawn-reinforcements:` - 1.0

# 硬编码占位符

下面包含了一个预制的占位符列表，可以在构建`nametag:`的时候使用。

|            占位符             | 描述                                                   |
| :---------------------------: | :----------------------------------------------------- |
|        `%displayname%`        | 表示被击杀实体的 CustomName 字段。                     |
|     `%health-indicator%`      | 表示生命指示栏系统。                                   |
|          `%mob-lvl%`          | 表示被击杀实体的级别。                                 |
|        `%entity-name%`        | 表示被击杀实体的 EntityType（实体类型）。              |
|  `%levelledmobs_killed-by%`   | 表示最后一个杀死玩家的实体的 EntityType（实体类型）。  |
|       `%death_nametag%`       | 表示 `creature-death-nametag:` 的值。                  |
|       `%entity-health%`       | 表示被击杀实体的精确生命值。                           |
|   `%entity-health-rounded%`   | 表示被击杀实体的生命值，四舍五入到最接近的整数。       |
|     `%entity-max-health%`     | 表示被击杀实体的精确的最大生命值。                     |
| `%entity-max-health-rounded%` | 这表示被击杀实体的最大生命值，四舍五入到最接近的整数。 |
|       `%heart_symbol%`        | 这表示符号 `♥`。                                       |
|          `%tiered%`           | 这表示由 `tiered-coloring:` 选择的有效颜色。           |
|         `%wg_region%`         | 这表示实体死亡的 WorldGuard 区域。                     |
|           `%world%`           | 这表示实体死亡的世界名称。                             |
|         `%location%`          | 这表示实体死亡位置的三个坐标点。输出格式为 X Y Z。     |

---

|                            配置行选项                             | 描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| :---------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                      `minLevel:` `maxLevel:`                      | 这代表要应用于实体的 `minLevel` 和 `maxLevel`。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                            `nametag:`                             | 这代表 LM 的名牌，悬浮在实体上方。<br />你必须在任何支持 Minecraft 1.16 服务器上安装 [**ProtocolLib**](https://www.spigotmc.org/resources/protocollib.1997/) 以使此功能正常运行。<br />你可以通过将此值更改为 `disabled` 来禁用名牌。要使名牌栏完全消失，请确保将 `nametag-visibility-method:` 也更改为 `disabled`。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                     `creature-death-nametag:`                     | 这代表每当玩家被一个具有等级的实体杀死时使用的名称。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                         `death-messages:`                         | 这代表死亡消息树的开始，你可以在其中定义在玩家被实体杀死时发送给玩家的消息的设置。你可以通过更改左侧的数字来设置消息被使用的几率，同时在右侧包含你更改后的消息。这个系统与 `weighted-random:` 级别修改器类似：左侧的数字越高，使用该消息的几率就越高。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|       `nametag-visible-time:` `nametag-visibility-method:`        | 这些设置控制 LevelledMobs 何时以及多长时间显示实体的名牌。默认情况下，使用了三个选项 `TARGETED`、`TRACKING` 和 `ATTACKED`。<br />`TARGETED` - 用于当实体瞄准了一个有视线的玩家时。<br />`ATTACKED` - 用于当玩家攻击一个实体时。<br />`TRACKING` - 用于当实体正在主动追踪一个有目标的玩家（跟随范围）。<br />`ALWAYS_ON` - 名牌始终可见，即使穿过方块也是如此。<br />`MELEE` - 名牌仅在近战范围内可见。<br />`DISABLED` - 名牌被禁用。<br />名牌被禁用。<br />如果启用了实体的名牌，计时器（以毫秒为单位）将从下一个激活事件开始倒计时，否则将重置名牌至默认配置。<br />我们正在努力改进 Nametag 系统，同时不牺牲效率和资源管理。 这是最新的一步，但我们一直在寻找圣杯； 如果你有改进的方法，请告诉我们！                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `nametag-placeholder-unlevelled:` `nametag-placeholder-levelled:` | 这表示 `%levelledmobs_mob-target%` 占位符的不同潜在值。如果未填充，将使用默认的 `nametag:` 值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                        `health-indicator:`                        | 这代表生命指示栏系统树的开始，你可以在其中定义用于 `nametag:` 配置选项中使用的 `%health-indicator%` 标签所需的设置。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                  `indicator:` `indicator-half:`                   | 这两个配置选项代表健康指示器系统中用作指示器的字符。`indicator:` 用于大多数级别，而 `indicator-half:` 用于生物达到其生命的最终级别并开始减少到零时使用。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                          `scale:` `max:`                          | 这两个配置选项调整生命指示栏的外观。`max:` 代表在栏中有多少 `indicator:`，而 `scale:` 代表每个 `indicator:` 代表多少生命值。这也用于确定它所在的级别。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|        `colored-tiers:` `tier-#:` `default:` `merge: true`        | 这代表生命指示栏的不同颜色，用不同颜色的层次来表示更高级别的生命值，这些颜色会随着生命值的变化而改变。<br />每个层级代表一块通过 `1Tier = ( max: x scale: )` 计算的生命值，因此每个后续层级都代表额外的相同生命值块。<br />示例： 使用 `scale: 4` 和 `max: 5`，这意味着每个层级值为 `20hp`。如果我有一个实体，在最大级别时生命值为 `110hp`，那么这意味着我需要至少 6 个层次来着色可以显示的每个层次的生命值。超出层次内可用生命值的任何生命值都将使用 `default:` 颜色。最后，如果你像我们在默认配置文件中所做的那样分隔 `health-indicator:` 设置，你可以使用 `merge: true` 将两个值合并在一起。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                          `multipliers:`                           | 这代表增益系统树的开始，你可以根据它们的最高级别来调整实体属性的变化。这个值代表了实体属性在达到最高级别时的百分比增加。默认情况下，我们使用增益 `max-health`, `movement-speed`, `attack-damage`, `ranged-attack-damage`, `creeper-blast-damage`, `follow-range`, `item-drop`, 和 `xp-drop`. 由于大多数实体不会在此插槽中生成值，因此剩余的属性都是特殊的。由于我们在人为地添加它们，所以我们需要使用一个不同的公式来应用它们的属性，从 `0.0` 或 0% 的属性到 `1.0` 或 100% 的属性。 如果你不确定， [请参考此页面以查看你选择的属性是否有效！](https://minecraft.fandom.com/wiki/Attribute)!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                `multipliers:` `custom-mob-level:`                 | 这代表以一种方便的方式调整特定实体的增益。这是 `multipliers:` 的子部分，如上面的代码所示。选择特定的 EntityType 后，确保匹配必要的格式，然后使用上面列出的 `multipliers:` 来调整默认应用的值。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|         `multipliers:` `use-stacked:` `['X', 'STACKED']`          | 该系统允许你修改增益的处理方式。你可以在 multipliers: 下方添加 `use-stacked: true` 选项，该选项将从下面列出的增益中获取值，并将其添加到每个级别的实体中。你还可以选择修改特定增益的条目，将其默认值从 X 更改为 `['Y', 'STACKED']`，其中 Y 代表该增益的新堆叠值。<br />这在实际操作中的示例可能是 `max-health: ['5.0', 'STACKED']`，其中普通的未升级的僵尸将有 20hp；1 级将有 25hp；2 级将有 30hp；3 级将有 35hp，依此类推。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                   `creeper-max-damage-radius:`                    | 这代表爬行者爆炸的半径。<br />Minecraft 原版的默认值是`3` ，一个更强大的中位数是 `5`；大于 `10` 的任何值基本上都是核弹，不建议使用，除非你喜欢那个 :3。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|             `tiered-coloring:` `LVL-LVL:` `default:`              | 这代表分层着色系统树的开始，你可以在其中定义用于 `nametag:` 配置选项中使用的 `%tiered%` 标签所需的设置，以根据实体的当前级别应用颜色。<br />你将在 `LVL-LVL:` 处建立一个级别范围，然后在 `color` 位置使用十六进制或以 `&` 为前缀的 Minecraft 颜色代码。<br />你可以建立一个 `default:` 颜色，适用于在尚未指定的级别范围内生成或召唤的任何实体。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                       `sunlight-intensity:`                       | 这代表应用于在阳光中燃烧的实体的额外伤害。<br />这是一个有用的工具，用于杀死生命值可能超过太阳伤害的更高级别实体。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|                `baby-mobs-inherit-adult-setting:`                 | 当设置为 `true` 时，此设置将应用于 EntityType 的成年和幼年版本（如果可用）的任何条件。<br />当设置为 `false` 时，这将把 EntityType 分为成年（默认）和幼年形式，前缀为 `BABY_`。<br />**示例：** `ZOMBIE` 和 `BABY_ZOMBIE`。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                       `level-inheritance:`                        | 当设置为 `true` 时，任何经历转化事件的实体将保留其先前应用的设置。<br />当设置为 `false` 时，新转化的实体将尝试在其新状态下重新定级。<br />一个转化事件的示例是当较大的史莱姆分裂成较小的史莱姆，或当村民变成僵尸村民再变回来时。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|                     `passenger-match-level:`                      | 当设置为 `true` 时，任何以 `Passenger` 组合方式生成的实体将与堆栈中最低的实体（移动乘客的实体）生成的级别相匹配。无论最低的实体生成了什么级别，乘客都会匹配那个级别。当设置为 `false` 时，每个实体将根据自己的级别策略生成自己的级别！                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|                         `vanilla-bonus:`                          | 默认情况下，LevelledMobs 不会更改基础的属性奖励修饰符（在 LM3.7.4 之前，我们做到了！）。在 LevelledMobs 潜在地修改这些值之前，你可以排除或允许这些奖励。<br />详细信息来自：[minecraft.fandom.com/wiki/Attribute](https://minecraft.fandom.com/wiki/Attribute)<br />`ATTACKING_SPEED_BOOST` - 末影人为 6.2，僵尸猪人为 0.45 的固定值；仅在攻击时存在。<br />`BABY_SPEED_BOOST` - 固定值为 0.5；仅适用于幼年僵尸和幼年僵尸村民。<br />`COVERED_ARMOR_BONUS` - 当壳关闭时，固定值为 20.0；仅当完全关闭时存在。<br />`DRINKING_SPEED_PENALTY` - 当巫婆喝药水时，固定值为-0.25。<br />`FLEEING_SPEED_BOOST` - 所有被动生物逃跑时使用的固定值为 2。<br />`LEADER_ZOMBIE_BONUS` - 在生成僵尸时，有（很小的）随机机会生成。对于生成增援机会，随机数介于 0.5 和 0.75 之间。对于 generic.max_health，随机数介于 1.0 和 4.0 之间。<br />`RANDOM_SPAWN_BONUS` - 生成时生成；从 0.0 到 0.05 的高斯分布中的随机数。<br />`RANDOM_ZOMBIE_SPAWN_BONUS` - 生成时生成；随机数介于 0.0 和 1.5 之间。<br />`SPRINTING_SPEED_BONUS` - 所有生物（包括玩家）奔跑时使用的固定值为 0.3。<br />`ZOMBIE_REINFORCE_CALLEE` - 每次生成僵尸作为增援时创建的固定值为-0.05。<br />`ZOMBIE_REINFORCE_CALLER` - 每次僵尸生成其他僵尸作为增援时创建的固定值为-0.05。<br /> |
|                 `use-custom-item-drops-for-mobs:`                 | 当设置为 `true` 时，将启用 LM CustomDrops 系统。<br />当设置为 `false` 时，LM 将完全忽略 CustomDrops。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|                `entity-name-override:` `LVL-LVL:`                 | 此配置选项有多种实                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

施方法。你可以使用单行项目方法，例如 `SKELETON: 'Jack'`；多个随机选择的选项，例如 `SKELETON: ['Jack', 'Sally', 'Sandy Claws']`；或在应用之前检查实体的级别，如上面的代码所示（如果指定级别，则使用特定的自定义名称）。<br />你还可以使用标签 `%displayname%`，它将实体的名称插入到新应用的名称中。当应用一个规则到多个 EntityTypes 时，这将非常有用。
|`nbt-data:`|此配置选项需要软依赖 [**NBT-API**](https://www.spigotmc.org/resources/nbt-api.7939/) 以正常运行。这允许你将 NBT 标签应用于已生成的实体。这将 _添加_ NBT 标签到已有的 mob NBT 标签列表中（不会重置/覆盖任何内容）。<br />这是一个用于创建更多独特实体样式的有用工具集。
|`use-droptable-id:`|此配置选项要求启用 LM CustomDrops 系统。<br />它允许你从 CD 中选择一个单一的掉落表，以应用于通过 LM 的规则系统选择的实体，从而实现高度动态的掉落条件。可以引用多个掉落表 ID。
|`lock-entity:`|当设置为 `true` 时，名称标签和自定义掉落规则将锁定到实体，因此即使后来应用了不同的规则，它也不会更改。
|`maximum-death-in-chunk-threshold:`|这控制了区块杀死计数系统。当使用大于 0 的数字时，系统将启用，并且任何配置了 `use-chunk-kill-max` 的自定义掉落在达到此阈值后将不会掉落。
|`max-adjacent-chunks:`|将考虑在实体死亡的区块旁边的区块数量，以满足 `maximum-death-in-chunk-threshold` 的条件。
|`chunk-max-cooldown-seconds:`|当达到区块杀戮极限时，将基于此设置启动计时器，直到再次启用掉落。
|`disable-vanilla-drops-on-chunk-max:`|当达到区块杀戮阈值时，此设置将确定是否禁用基础的掉落。
|`spawner-particles`|这仅适用于 LM 生成器，它是在生成器生成生物体时使用的粒子效果。可以是来自此链接的任何值：https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html
|`spawner-particles-count`|当从 LM 生成器生成生物体时，将生成多少个粒子。

---
