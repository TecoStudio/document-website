```
本页信息最后更新为“生物等级”插件的3.8.2 b721版本。
```

---

在“生物等级”插件的`customdrops.yml`文件里，你可以自由地去设置许多与掉落物有关的选项来为不同生物制作它们专属的掉落物，可以是直接替换现有的掉落物列表，也是可以直接添加到现有的掉落物列表中。

[[点击此处查看最新的默认文件]](https://github.com/ArcanePlugins/LevelledMobs/blob/master/src/main/resources/customdrops.yml)

**需要配置文件的样板来帮助你制作示例吗？**
UltimaOath 目前正在开发一个`customdrops.yml`文件，该文件包含了成百上千行可用于自定义的掉落物列表，以便让你在服务器上使用它。该文件目前正在被维护中并且一直在持续更新。一旦制作完后，最后的作品也会留在下面的列表中，在制作期间，你可以[点击此处](https://github.com/UltimaOath/LevelledMobs/blob/master/src/main/resources/exampleconfigs/customdrops.yml)了解更多进度！

---

# 默认情况：

在这些配置选项中的选项都适用于自定义掉落物，除非你已经修改了其他掉落物选项的单个属性来覆盖掉默认设置。这些选项中的每个属性都必须要有一个值，否则“自定义掉落物”将有可能不会正常运行，但是一旦在此处就行了设置，那么如果不需要为其他掉落物进行单独命名的话那么可以不需要改。在此处修改的掉落物属于全局类型，一次修改始终生效，这同样适用于配置文件中的所有系统，包括**原版的掉落物列表**。

> ### 对于使用百分比数值的解释：`1.0` = 100% ； `0.0` = 0%

```yml
defaults:
  chance: 0.2
  use-chunk-kill-max: true
  amount: 1
  minLevel: -1
  maxLevel: -1
  damage: 0
  custommodeldata: -1
  min-player-level: -1
  max-player-level: -1
  nomultiplier: true
  nospawner: false
  equipped: 1.0
  equip-offhand: true
  override: false
  maxdropgroup: 1
  priority: 0
  player-caused: true
  item_flags: ''
  groupid: ''
  overall_chance: 0.0
  nbt-data: ''
  only-drop-if-equipped: false
  player-level-variable: ''
  name: ''
  lore:
    - ''
    - ''
  enchantments:
    ENCHANTMENT: X
  enchantments:
    ENCHANTMENT:
      shuffle: false
      default: 1
      X: 0.5
  overall_permission: ['']
  permission: ['']
  cause-of-death: ['']
  run-on-spawn: false
  run-on-death: true
  delay: 0
```

|                                          配置选项属性                                           | 描述                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| :---------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                            `chance:`                                            | 被选中作为掉落物的概率。                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                                      `use-chunk-kill-max:`                                      | 如果在`rules.yml`文件中开启了“区块击杀上限”功能，那么将此属性设置为`true`可以让自定义掉落物在达到上限后不会再掉落，直到冷却时间结束。                                                                                                                                                                                                                                                                                                     |
|                                            `amount:`                                            | 设置当被选中作为掉落物可以掉落的属性，这是一个范围，例如：`1-3`，将会在此范围内的最大值和最小值之间随机选择一个掉落物数量。                                                                                                                                                                                                                                                                                                               |
|                                     `minLevel:` `maxLevel:`                                     | 选择掉落物数量的最大值和最小值。<br />设置为`-1`可禁用特定的属性检查。                                                                                                                                                                                                                                                                                                                                                                    |
|                                            `damage:`                                            | 设置掉落物的物品耐久损耗情况，可以设置为单个数量或者设置为例如`50-99`的这种数字范围，数字越高损耗耐久越多。                                                                                                                                                                                                                                                                                                                               |
|                                       `custommodeldata:`                                        | 这是一个高级选项，设置的是该物品在作为掉落物时会选择的自定义 3D 模型。                                                                                                                                                                                                                                                                                                                                                                    |
|                                         `nomultiplier:`                                         | 检测生物在死亡时是否会根据该生物的`item-drop:`来增加或者降低掉落物种类。                                                                                                                                                                                                                                                                                                                                                                  |
|                                          `nospawner:`                                           | 检测通过刷怪笼生成的生物是否也可以拥有掉落物。                                                                                                                                                                                                                                                                                                                                                                                            |
|                                           `equipped:`                                           | 假如该生物可以手持或者装备某个掉落物的话，设置可以装备的概率。<br />装备的顺序会首先尝试手持，然后是头盔栏，假如生物无法穿戴装备的话，例如：蠹虫，那么会被忽略。                                                                                                                                                                                                                                                                          |
|                                        `equip-offhand:`                                         | 假如成功在`equipped:`选择了一个掉落物来装备并且本选项设置为了`true`，那么会将掉落物装备到副手栏而不是主手栏。                                                                                                                                                                                                                                                                                                                             |
|                                             `name:`                                             | 当被用于`MATERIAL`或者`PLAYER_HEAD`时，设置掉落物的名称。<br />当被用于`customCommand`时，那么这只是一个调试选项。<br />你可以使用原版的颜色代码来命名，如果你的服务器支持的话，也可以使用 HEX 颜色！                                                                                                                                                                                                                                     |
|                                             `lore:`                                             | 设置物品的描述，可以设置一行或者多行，设置完成后它们将会用于`MATERIAL`或者`PLAYER_HEAD`上。<br />你可以使用原版的颜色代码来命名，如果你的服务器支持的话，也可以使用 HEX 颜色！                                                                                                                                                                                                                                                            |
| `enchantments:`<br />`ENCHANTMENT:` `X`<br />`ENCHANTMENT:` `X: 0.5`<br />`shuffle:` `default:` | 设置物品拥有的附魔。<br />使用附魔名称来代替`ENCHANTMENT:`，使用附魔等级代替`X`。<br />例如：`UNBREAKING: 2`（附魔类型：耐久，附魔等级：2 级）<br />你也可以使用`ENCHANTMENT:`下面的`X: 0.5`来设置附物品拥有该附魔的概率，其中`X`代表的是附魔等级，而`0.5`代表的是附魔概率。<br />在此选项中你可以设置为`shuffle: false`来让物品根据顺序来获得附魔等级而不是随机等级，如果设置为`default: X`那么将会根据下方`X`设置的数值来指定附魔等级。 |
|                                           `override:`                                           | 决定生物是否可以同时掉落原版的掉落物，或者完全覆盖掉原版的掉落物。                                                                                                                                                                                                                                                                                                                                                                        |
|                                   `maxdropgroup:` `groupid:`                                    | 在同一个`EntityType`或者`drop-table:`下的多个材料物品中使用`groupid:`，将这些掉落物合并到同一个组中。当与`maxdropgroup:`一起使用时，将会限制在同一个组里可以掉落的数量和`chance:`设置的概率。                                                                                                                                                                                                                                             |
|                                           `priority:`                                           | 默认情况下，掉落物类似“生物等级”的树状方式来生成。<br />通过设置`priority:`优先级，你可以让单个掉落物比其他物品拥有更快的生成速度。                                                                                                                                                                                                                                                                                                       |
|                                        `player-caused:`                                         | 该选项是检测实体是否由玩家击杀和被其他类型的伤害击杀。<br />不建议将它从`true`更改为`false`，因为这有可能会导致刷怪塔失效，因为生物需要由玩家击杀才会掉落特殊的掉落物。                                                                                                                                                                                                                                                                   |
|                                        `overall_chance:`                                        | 设置该实体类型生成掉落物的概率，对于实体来说，只需要设置实体类型的通用概率，就可以让该类型的实体拥有一个统一的掉落概率而不需要为每个实体单独设置，如果首次未成功生成掉落物，那么该实体将不再会生成任何掉落物。                                                                                                                                                                                                                            |
|                                           `nbt-data:`                                           | 设置该掉落物的 nbt 标签。<br />**注意**：需要安装[NBT-API](https://www.spigotmc.org/resources/nbt-api.7939/)前置。                                                                                                                                                                                                                                                                                                                        |
|                                          `item_flags:`                                          | 允许你为掉落物设置`ITEM_FLAGS`来将隐藏属性应用到掉落物上。<br />`HIDE_ATTRIBUTES` - 隐藏属性，例如：已损耗的耐久。<br />`HIDE_DESTROYS` - 隐藏可破坏方块的属性。<br />`HIDE_DYES` - 隐藏物品的染色。<br />`HIDE_ENCHANTS` - 隐藏物品上的附魔。<br />`HIDE_PLACED_ON` - 隐藏可放置方块属性。<br />`HIDE_POTION_EFFECTS` - 隐藏药水效果。<br />`HIDE_UNBREAKABLE` - 隐藏无法破坏属性。                                                      |
|                                    `only-drop-if-equipped:`                                     | 当一个实体在`equipped:`穿戴了装备后并且在`chance:`被选择作为了掉落物。那么将此选项设置为`true`，那么装备将会掉落。如果设置为`false`，那么无论装备是否被选择为掉落物都会有概率尝试掉落。                                                                                                                                                                                                                                                   |
|                               `overall_permission:` `permission:`                               | 一个`MODALLIST`配置选项；检测距离实体最近的玩家，检测击杀生物的玩家，这取决于所选择的系统，所有的权限注册方式都是`levelledmobs.permission.<node>`，其中`<node>`代表的是权限配置的值。例如：你的权限是`levelledmobs.permission.vip`，那么你可以将权限名称设置为：`permission: ['vip']`。使用`overall_permission:`可将这些物品全部集中在一起，而`permission:`适用于每个单独的物品。                                                         |
|                                        `cause-of-death:`                                        | 一个`MODALLIST`配置选项；检测实体的死亡方式，只会检测对实体的致命一击，并且会忽略`player-caused: true`，因为死亡原因基本上不会涉及到玩家，例如：由火焰造成的伤害而不是玩家。                                                                                                                                                                                                                                                              |
|                             `min-player-level:` `max-player-level:`                             | 设置玩家最低和最高需要达到多少原版等级才能掉落某些掉落物。<br />设置为`-1`可禁用等级检查。                                                                                                                                                                                                                                                                                                                                                |
|                                     `player-level-variable`                                     | 如果更改了此选项，那么在上面的`min-player-level:`和`max-player-level:`将会使用目前的这个变量而不是玩家的原版等级。你可以在此处使用任何的`PAPI`占位符标签，类似`玩家等级`策略系统所使用的变量等级方式。                                                                                                                                                                                                                                    |
|                                        `external-amount`                                        | 当与`LM_Items`一起使用时，该选项会对指定的插件设置金额。                                                                                                                                                                                                                                                                                                                                                                                  |
|                                             `type`                                              | 当与`LM_Items`一起使用时，设置物品的类型，目前仅支持`MMOItems`。                                                                                                                                                                                                                                                                                                                                                                          |
|                                         `run-on-spawn`                                          | 仅适用于自定义指令，设置生物在生成时将会执行的指令。                                                                                                                                                                                                                                                                                                                                                                                      |
|                                         `run-on-death`                                          | 仅适用于自定义指令，设置生物在死亡时将会执行的指令。                                                                                                                                                                                                                                                                                                                                                                                      |
|                                             `delay`                                             | 仅适用于自定义指令，设置在执行指令前需要等待的时间，单位是 tick。                                                                                                                                                                                                                                                                                                                                                                         |

# 进阶掉落和指令属性

虽然材料和指令掉落都可以使用上述列出的任何配置选项，但是有两种特殊情况下可以使用特殊的配置选项。

目前有几个占位符可以使用，当与`customCommand:`一起使用时，可以使用指令来替换一些非必要的内容。

|         配置选项属性          | 描述                                             |
| :---------------------------: | :----------------------------------------------- |
|          `%mob-lvl%`          | 代表的是被击杀实体的等级。                       |
|          `%player%`           | 代表的是击杀该实体的玩家。                       |
|        `%displayname%`        | 代表的是被击杀实体的`自定义名称`词条。           |
|        `%entity-name%`        | 代表的是被击杀实体的`实体类型`。                 |
|     `%entity-max-health%`     | 代表的是被击杀实体的最大生命值，精准。           |
| `%entity-max-health-rounded%` | 代表的是被击杀实体的最大生命值，四舍五入到整数。 |
|         `%wg_region%`         | 代表的是实体死亡时的 WorldGuard 区域。           |
|           `%world%`           | 代表的是实体死亡时的维度名称。                   |
|       `%X%` `%Y%` `%Z%`       | 代表的是实体死亡时的坐标点。                     |

```yml
- PLAYER_HEAD:
    mobhead-id: ''
    mobhead-texture: ''
- MATERIAL:
- ENCHANTED_BOOK:
    enchantments:
      ENCHANTMENT: X
- customCommand:
    command: ''
    command: ['', '']
    ranged_A: ''
    ranged_B: ''
    name: ''
```

你可以在`mobhead-id`里填写玩家的`UUID`，在`mobhead-texture`里填写与头颅有关的`纹理`。你可以在网络上搜索“我的世界头颅库”或者[点击此处](https://minecraft-heads.com/)前往 Mojang 官方的头颅库中，你只需要使用这两个数值中的其中一个即可。

在材料掉落列出的`Defaults`部分是它们的默认配置信息。在此处列出的任何选项都可以在`MATERIAL`、`PLAYER_HEAD`和`customCommand`中使用。这将会告诉掉落物系统，你希望去设置一个指令来像实体类型的掉落一样。为了使该功能生效，至少需要`command:`选项配置和一个有效的控制台指令。你也可以跟上面展示的那样使用指令来一次执行多条指令。

一个有效的指令例子是：“`effect give %player% strength %ranged_a% %ranged_b%`”

附魔书（ENCHANTED_BOOK）是一种特殊的材料掉落，它可以根据`enchantments:`配置选项来开启功能。

以`ranged_`为前缀的标签是唯一的，该标签允许你制作一个随机刻发生器来作为占位符在指令中使用。在上面的例子中向你描述了如何使用 ranged 的配置选项，在`ranged_`的右边添加上 A/B/C/D 等等，最后即可形成标签。而值则是代表的是潜在类型的数值范围，可以在个别指令中以占位符的形式存在。同样使用前面的例子，`ranged_A: 1-2`和`ranged_B: 3-5`，那么第一个标签是 1-2 之间的任何数值，而第二个标签在激活的指令中使用的则是 3-5 之间的任何数值。

# 通用组：

“生物等级”插件包括了几个实体组，它们以一种更简便的形式集中在一起。在这些组中的每个组都有属于它们自己的 EntityType 在生效，一次制作后便可适用于多个实体，你可以在[通用实体类型](https://github.com/lokka30/LevelledMobs/wiki/Documentation---rules.yml#universal-mob-and-biome-groups)中查看！

# 实体类型：

在“生物等级”插件的`customdrops.yml`文件里列举出了截止于我的世界 1.17 版本中所有的原版实体。你可以找到你想要修改的实体而不是在配置文件的其他位置里添加额外实体，因为即使添加了它们也有可能不会正常加载。你也可以通过删除任何你不想要的实体列表，因为哪怕是删除了，你以后也是可以将它再次添加回来。

# 掉落物列表

在掉落物列表中有一个系统，它允许你添加材料和自定义指令，这些材料和指令可以作为一个单独的物品，使用`usedroptable: tableName`可以添加到额外实体，来帮助减少或者覆盖多个实体，也可以用来制作不同的等级掉落。

```yml
PUT_ENTITY_TYPE_HERE:
  - usedroptable: "putTableNameHere"
```

当使用掉落物列表制作掉落物时，你可以复制任何其他掉落物的格式，然后使用 tableName 替换 EntityType 即可。

> **记住**：任何未删除的掉落物配置选项都会从配置文件中读取对应内容。

# 第三方插件的支持

如果你想使用来自其他插件的自定义物品，请查看“`LM_Items`”。<br>
这个插件弥补了这个差距，因此你可以在本地读取来自第三方插件的物品。<br>
如果你需要下载，请[点击此处](https://www.spigotmc.org/resources/lm-items.102081/)前往。
