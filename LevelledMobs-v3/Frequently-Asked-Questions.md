```
本页信息最后更新为“生物等级”插件的3.9.2 b734版本。

注意：随着我们对配置文件的更新，任何类似的问题都有可能会过时，请仔细分辨。
```

---

## 我应该如何开始？

<details>
<summary>点击查看解决方案</summary>

请不要担心！虽然我们知道新人会在看见“生物属性”插件时可能会感到害怕，但是也请相信对于这些问题，wiki 是会很详细的提出解决方案的。在许多文件里会出现预设和示例，这些内容可以帮助你更快的了解该插件，因为详细所以字数较多也请认真看完，从此处开始：

---

**你已经成功安装“生物等级”插件，没有报错但是插件没有生效？**

通常情况下，也是首先容易被忽略的步骤是：当你在启动服务器时，“生物等级”插件并没有报错。虽然这些插件可以同时和“生物等级”插件一起使用但实际上其他插件会导致“生物等级”插件无法使用，这种情况十分罕见，它们会在控制台中以大量文本的报错形式出现，这种报错只会出现在第一次启动服务器时出现。如果发生了这种情况，建议搭建一个测试环境然后一个一个插件进行测试来寻找那个会导致本插件失效的其他插件。

如果你已经开始编辑你的配置文件的话，你也许会在文件的格式上犯错，如果格式错误，那么本插件在启动服务器时会尝试在控制台中报告该情况。如果发生了格式错误的情况，那么本插件也无法正确的读取，从而导致插件的加载失败。YAML 是很多插件使用的通用语言，它对错误的检查能力较高，甚至是那些不小心打出来的多余空格。我们建议你去打开或者下载一个免费的在线 YAML 文件检查器来查看你的文件，来帮助你检查并发现你文件内的那些错误格式。

---

**没有遇到错误？那太好了，现在来了解文件里的规则吧。**

如果你刚刚安装了该插件并且没有在启动时控制台没有报错，那么本插件应该可以正常运行。在此提供了一个简易描述，更详细的讲解在[此处](https://github.com/ArcanePlugins/LevelledMobs/wiki/Understanding-the-Default-Config)找到。为了了解到规则是如何运行的，我将描述分成设置和选项两个项目。首先，规则分为：`预设（presets）`、`默认规则（default-rule）`、`自定义规则（custom-rules）`三种。预设：包括部分不同的系统，这些系统被分隔且拥有独立的名称，例如：在默认配置文件中使用的预设的名称是`allowed_worlds`、`weighted_random_Levelling`、`average_challenge`。你会注意到很多其他类型的预设，如果你想切换预设，只需要将名字更改即可，且可以随时使用预设。

在预设的下面是`默认规则`。`默认规则是`“生物等级”插件的核心，跟我们刚刚说的一样，我们使用的预设名称是`allowed_worlds`、`weighted_random_Levelling`、`average_challenge`。你可以看见这些预设都是默认开启的，同时也有一些预设是默认关闭的，如下：

```yaml
default-rule:
  use-preset:
    - allowed_worlds
    - nametag_using_numbers
    #- nametag_using_indicator
    #- basic_challenge
    - average_challenge
    #- advanced_challenge
    #- extreme_challenge
    - weighted_random_Levelling
    #- spawn_Levelling
    #- lvl-mod_spawn-blended
    #- ycoord_Levelling
    #- random_Levelling
    #- lvl-mod_player-variable
    #- lvl-mod_apply-variance
```

首个预设，`allowed_worlds`，设置插件生效的维度黑名单，只有在该黑名单以外的维度的生物才能拥有生物等级。在该预设下，除了末地（`world_the_end`）以外的维度的生物都拥有对应的生物等级，可以理解为黑名单。

```yaml
allowed_worlds:
  # 设置插件的生效维度。
  name: "维度黑名单"
  conditions:
    worlds:
      # 生效维度列表：['*']
      excluded-list: ["world_the_end"]
```

第二个预设，`nametag_using_numbers`，是与生物铭牌有关的预设设置。在目前是所有预设中有一个类似的预设叫`nametag_using_indicators`，功能基本一样但只是辅助系统来做出区分的能力。不管是什么预设，你都可以根据自己的爱好来选择和编辑它们。

```yaml
nametag_using_numbers:
  #   设置生物铭牌，其中与生命值有关的是使用%entity-health-rounded%显示。
  name: "名称标签"
  apply-settings:
    nametag: "&8&l༺ %tiered%Lvl %mob-lvl%&8 | &f%displayname%&8 | &f%entity-health-rounded%&8/&f%entity-max-health-rounded% %tiered%%heart_symbol% &8&l༻"
```

第三个预设，`average_challenge`，是其他四个经过测试的`_challenge`选项之一，你可以自由地在它们之间切换或者编辑它们，也可以添加属于你自己的预设（推荐复制或者粘贴其他的`_challenge`预设然后将名称更改为自己的即可，例如：`epic_challenge`）。其中`average_challenge`是在原版服务器的普通难度里测试的，但是在感觉上像困难模式；`basic_challenge`是难度更简单；而`advanced_challenge`和`extreme_challenge`是为了测试即使拥有了全套附魔的顶级玩家而准备的。

因为预设没有考虑到每个服务器的不同玩家的自定义能力，例如：mcMMO、AureliumSkills 等可以增加玩家攻击力的插件，或者提供非原版的附魔等等，所以当你在修改难度时请务必考虑这些情况。

每个不同的`_challenge`难度预设总体都是差不多的：设置`最高等级`(`maxLevel:`)、设置`倍率`(`multipliers:`)，然后设置其他细节，例如：不同`等级`（`%tiered%`）的生物拥有`不同颜色`(`tiered-coloring:`)。最后是修改生物铭牌的显示方式，修改不同的占位符位置（`名称数值铭牌：nametag_using_numbers`、`名称铭牌：nametag_using_indicators`、`生命值铭牌：health-indicator:`）等等。目前拥有两种修改难度的办法：如果你想让实际难度不变但是只是想更改等级之间的差距来让该生物更容易打或者更难打，你只需要修改该预设的`最高等级`（`maxLevel:`）而不是修改`倍率`（`multipliers:`），这将允许在不同的等级之内降低等级上限，默认是从 1 到`最高等级`（`maxLevel:`）。如果你想直接修改生物的实际难度，你只需要修改`倍率`（`multipliers:`），一旦你觉得生物的难度合适，你可以慢慢的调整`最高等级`（`maxLevel:`）来分散或者缩小差异。

从“生物等级”插件的`3.9版本`开始，你可以使用乘法来设置最高等级提升难度百分比等相关参数。例如：如果设置为“`max-health: 5.0`”，那么该生物每升一级都会增加 500%的生命值；或者你也可以选择使用堆叠（`STACKED`）选项来设置每升一级时会增加指定的值，例如：如果设置为“`max-health: ['5.0', 'STACKED']`”，那么每当生物从 1 级升到最高等级时，每升一级都会直接增加 5 点生命值而不是使用乘法来增加生命值。

也可以设置不同等级的`生物铭牌颜色`（`tiered-coloring:`），例如：1-5 级的生物铭牌是绿色，而 6-10 级的生物铭牌为蓝色等等，关于如何使用，请查看[Wiki](https://github.com/ArcanePlugins/LevelledMobs/wiki/Documentation---Apply-Settings)。

```yaml
average_challenge:
  name: "平均值 - 难度倍率"
  apply-settings:
    minLevel: 1
    maxLevel: 25
    multipliers:
      max-health: 5.0
      movement-speed: 0.15
      attack-damage: 2.25
      ranged-attack-damage: 2.25
      creeper-blast-damage: 0.75
      item-drop: 3.0
      xp-drop: 5.0
      #       特殊倍率（最低0.0 - 最高1.0）
      armor-bonus: 0.2
      armor-toughness: 0.15
      ##   可选的值，可以使用堆叠也就是加法来代替，如下：
      # max-health: [ '4.25', 'STACKED' ]

    tiered-coloring:
      1-5: "&#22E76B" #绿色
      6-10: "&#528CFF" #蓝色
      11-15: "&#FFCD56" #黄色
      16-20: "&#F2003D" #红色
      21-25: "&#B447FF" #紫色
      default: "&#FFFFFF" #白色
    health-indicator:
      scale: 4
      max: 5
      merge: true
```

在此基础上，我已经告诉了你如何为“生物等级”插件设置生物的等级和难度等等，接下来我会告诉你如何将等级给予实体。通过第四个选项`weighted_random_Levelling`来告诉插件应该给予更高概率给最低等级，给予更高概率给最高等级而不是生物在生成时就拥有最高等级，有关其他的选项和说明请在[Wiki](https://github.com/ArcanePlugins/LevelledMobs/wiki/Documentation---Strategies)中查看。

```yaml
weighted_random_Levelling:
  # 设置预设的随机偏置。
  name: "等级权重 - 随机"
  strategies:
    weighted-random: true
```

你可以自由地编辑上述文件中的预设值来符合你想要的规则，例如：你可以将`advanced_challenge`预设下的`maxLevel:`值从默认的 25 更改为 50 而不是更改`advanced_challenge`文件来让当前维度获得一个 1-50 级的随机值。

你也可以将预设的名称更改成你自己想要的那个名称来在其他的地方使用该预设，例如：你可以将`average_challenge`更改为`epic_challenge`，然后修改`epic_challenge`预设其他数值。

你也可以禁用预设，使用其他相同类型的预设来覆盖掉，例如：如果你想禁用`weighted_random_Levelling`，那么你可以使用`spawn_Levelling`来覆盖掉它，同时是以生物在生成时的生成距离来决定该生物的等级。

还有一个是以`lvl-mod_`为开头的特殊预设，该预设代表的是各种额外系统，可以在实体被`Levelling`分配后再次修改其属性。例如：`lvl-mod_player-variable`是一个可以根据附近玩家的数量来调整实体等级的系统，`lvl-mod_apply-variance`可以为等级添加一个随机的正负值，`lvl-mod_spawn-blended`可以为`spawn_Levelling`预设添加一个生成高度的参数，但前提是需要开启该参数。

---

**哇！这些字好多哇！**

别担心，这些只是`预设`的大部分`描述`！请不要担心，你既然走到了这里，那么接下来只需要走一小部分了，除此之外剩余的这些也就是`默认规则`和各种设置！如果你担心不会使用，也可以不使用预设，因为预设只是为了方便自定义，你可以简单的修改生物铭牌的排列方式、等级颜色等内容，这样就可以避免去编辑这些很长但是没什么用的预设，如果你不打算自定义插件的话也可以不去编辑这些预设来避免麻烦。

---

**自定义规则 - 这有个规则！**

规则部分包括了对`默认规则`的额外修改或者增加。如果你使用的是我们最初设置的默认标准并且删除了所有的自定义规则，该插件依旧可以正常运行，但是对于被动生物（例如：少数特殊实体、村民、流浪商人和其他幼体实体）的等级没有特殊加成，同时不会为下界维度设置自定义等级策略，该策略使用的是世界高度而不是默认规则，也不会为实体作出修改，例如：取消末影人的`移动速度`、`最大生命值`、`倍率`等等加成，以便保护玩家不会在与末影人战斗时因为移动速度而难以攻击的情况发生，最后僵尸主人也不会被削弱，以便让玩家在战斗时可以更好的聚集生物，这些自定义规则都在制作时进行了测试，你可以自由地选择这些规则，最终的选择权在你的手上！

从这里开始你可以继续去添加自定义规则来达到符合你自己的目的，建立一套属于自己的检查规则，然后在该规则上设置或者更改策略，在 Wiki 上有许多[条件](https://github.com/ArcanePlugins/LevelledMobs/wiki/Documentation---Conditions)可供你自由选择。

---

**末日尽头：自定义掉落**

恭喜你走到了这里，在我们这个插件的自定义掉落的系统中允许你在设置原版物品的同时，还可以设置许多来自第三方插件里的物品，这些来自其他插件里的物品也可以同步到游戏中，你可以选择[LM_ITEMS](https://www.spigotmc.org/resources/lm-items.102081/)插件或者[NBT-API](https://www.spigotmc.org/resources/nbt-api.7939/)插件来制作这些内容，通过设置物品上的 NBT 数据来制作属于你自己的物品。

关于掉落有许多东西需要更详细的解释，特别是对于 Wiki 里的一些内容，但是对于那些想自定义物品的人来说，可以不需要查看示例库，因为在许多其他地方都拥有一个十分庞大的信息库，例如：[自定义掉落示例库](https://github.com/ArcanePlugins/LevelledMobs/wiki/Sample-CustomDrops)，[可以通过以下方法](https://github.com/ArcanePlugins/LevelledMobs/wiki/Sample-Custom-Rules#using-drop-tables-with-custom-rules)来实现表格的制作，因为它们为你提供了自定义掉落的各种修改和条件。

---

**你说的这些是人话吗？**

在做完这些内容后，你是不是还在感觉到疑惑或者有其他的疑问？不要由于，请加入 Arcane 的[Discord](https://www.discord.io/arcaneplugins)频道来提出你的问题，哦对了，记得在发言之眼仔细查看频道的规则来避免发生一些不愉快的事。当我们有空的时候，我们很乐意去为你进行解答！

---

</details>

## 我应该如何让本插件在指定维度生效或者禁用？

<details>
<summary>点击查看解决方案</summary>

在`rules.yml`文件的第 180 行只有，你应该可以看到一个与`allowed_worlds`有关的内容，如下：

```yaml
allowed_worlds:
  # 设置插件的生效维度。
  name: "维度黑名单"
  conditions:
    worlds:
      # 生效维度列表：['*']
      excluded-list: ["world_the_end"]
```

### 白名单

如果你想设置生效维度的白名单，例如：只允许“A”、“B”、“C”三个维度的生物拥有等级，那么可以使用以下方法：

```yaml
allowed-list: ["A", "B", "C"]
# excluded-list: [ 'world_the_end' ]
```

当`excluded-list`前面有注释符号`#`时，说明该选项目前是禁用的。

### 黑名单

如果你想让指定维度以外的所有维度的生物都可以获得等级，例如：除了“A”、“B”、“C”三个维度之外的其他维度，那么可以使用以下方法：

```yaml
# allowed-list: ['my_world']
excluded-list: ["A", "B", "C"]
```

当`allowed-list`前面有注释符号`#`时，说明该选项目前是禁用的。

</details>

## 为什么本插件的自定义生物名称标签不会显示？

<details>
<summary>点击查看解决方案</summary>

> **注意**：本条信息不包含“生物等级”插件的 3.5 版本和更低版本，因为插件的更低版本需要安装 ProtocolLib 前置，所以不可能可以在 1.19 版本上运行。请确保你的插件和服务器类型始终都是最新版！

- 你是不是运行 1.16、1.17 或者除了 Paper 端的 1.18 服务器？如果是的话那么请确保你在除了安装“生物等级”插件之外是否还安装了前置插件[ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/)。

- 请检查你服务器的控制台内是否有报错，也检查一下`rules.yml`文件内的格式是否正确。

- 如果上述都没问题，那么理论来讲都应该会显示生物名称的对应标签，如果还是没有的话，请务必及时联系作者寻求帮助。

</details>

## 如何给予名为 X 的生物获得等级？

### 以及：为什么小僵尸、监守者等生物没有等级？

<details>
<summary>点击查看解决方案</summary>

默认情况下，以下生物没有等级：

- 被动生物，例如：牛、猪；
- 幼体生物，例如：小僵尸、小村民等；
- 劫掠兽、末影龙、凋灵、监守者；
- 村民、僵尸村民、流浪商人；
- 幻翼、蝙蝠。

> **注意**：默认情况下通过刷怪笼生成的生物也是不会拥有等级的，我们已经在疑难解答 Wiki 中的另外一个问题的答案里说了如何让刷怪笼生成的生物也拥有等级。

在`rules.yml`文件的第`399`行你可以看见以下类似的代码：

```yaml
custom-rules:
  - enabled: true
    name: "CR - 被动生物无等级 + 实体类型"
    use-preset: allowed_worlds
    conditions:
      entities:
        allowed-groups: ["all_passive_mobs"]
        allowed-list:
          [
            "BABY_",
            "ENDER_DRAGON",
            "WITHER",
            "VILLAGER",
            "ZOMBIE_VILLAGER",
            "WANDERING_TRADER",
            "PHANTOM",
            "BAT",
            "RAVAGER",
            "WARDEN",
          ]
    apply-settings:
      maxLevel: 0
```

如果要给予被动生物等级，那么只需要将：

```yaml
allowed-groups: ["all_passive_mobs"]
```

更改为：

```yaml
allowed-groups: []
```

如果想让在`allowed-list`列表中的生物获得等级，那么只需要在列表中删除该生物即可。例如：如果想让小僵尸这种幼体生物获得等级，那么只需要将：

```yaml
allowed-list:
  [
    "BABY_",
    "ENDER_DRAGON",
    "WITHER",
    "VILLAGER",
    "ZOMBIE_VILLAGER",
    "WANDERING_TRADER",
    "PHANTOM",
    "BAT",
    "RAVAGER",
    "WARDEN",
  ]
```

更改为：

```yaml
allowed-list:
  [
    "ENDER_DRAGON",
    "WITHER",
    "VILLAGER",
    "ZOMBIE_VILLAGER",
    "WANDERING_TRADER",
    "PHANTOM",
    "BAT",
    "RAVAGER",
    "WARDEN",
  ]
```

在`rules.yml`文件里的工作方式是：任何通过实体的检查条件的生物（例如：凋灵骷髅‘`WITHER_SKELETON`’）都不会拥有等级，它们的生物等级都是 0 级也就是无等级。

</details>

## 目前可以选择哪些系统？

<details>
<summary>点击查看解决方案</summary>

- **随机等级权重** (**默认**)
  - 等级属于随机值，但是你可以设置让某些等级的出现概率更高。
  - 默认情况下，较低等级的值出现的概率会比高等级的概率更多。
  - 目前有简单（easy）/普通（normal）/困难（hard）三种模式的预设可供选择。
- **随机等级**
  - 随机选择等级，每个等级的随机概率都是一样的。
- **生成距离**
  - 根据生物距离出生点时的距离增加，距离出生点越远等级越高。
- **Y 轴高度**
  - 根据生物在生成时的 Y 轴高度而修改，生物的等级等于目前所在高度，Y 轴高度越高生物的等级越高。
- **混合类型**
  - 将“生成距离”和“Y 轴高度”这两个预设结合起来。
- **玩家等级**
  - 一个特殊的等级系统，允许你使用来自其他插件中的玩家数据来修改生物的等级（任何与 PlaceholderAPI 有关的占位符），生物的等级会基于该数值而增加。
  - 例如：你可以设置让拥有更高等级或者金钱的玩家附近可以生成更高等级的生物，这一切都可以根据你的需要而设置！
  - 我们在下面的这个问题里有一个答案，我们详细地解答了如何在你的服务器上使用“玩家等级”预设。
- ... 以及更多内容！

</details>

## 我应该如何切换到其他的等级系统？

<details>
<summary>点击查看解决方案</summary>

> **注意**：如果你想单独启用“玩家等级”系统的话，在本章的下面有一个解决办法可以帮助到你。

在 default-rules 的开头区域找到下面文件的这种内容，你的文件内容可能会略有不同：

```yaml
default-rule:
  use-preset:
    - allowed_worlds
    - nametag_using_numbers
    #- nametag_using_indicator
    #- basic_challenge
    - average_challenge
    #- advanced_challenge
    #- extreme_challenge
    - weighted_random_Levelling
    #- spawn_Levelling
    #- lvl-mod_spawn-blended
    #- ycoord_Levelling
    #- random_Levelling
    #- lvl-mod_player-variable
    #- lvl-mod_apply-variance
```

*注释*是为了*关闭*那些你不想用的系统，如果你你想开启这些系统的话请*取消*该系统前面的注释符号即可。

> YAML 是几乎每个“`.yml`”文件的通用编辑语言，可以在此类文件中使用注释`#`来让游戏在启动时忽略该一行的内容。
>
> “为什么要忽略这一行？”，使用注释符号`#`可以让游戏在启动时忽略，让你更方便地更换本插件选择的对应系统。

使用前请确保你为目前的默认规则里启用了至少 1 个生物铭牌、挑战预设、等级策略。

> **注意**：已存在的生物不会被赋予等级，如果你想强制对所有维度的生物赋予等级，请使用`/lm rules force_all`指令，如果你担心可能会对实体造成影响，那么也可以使用`/lm kill all * /nodrops`来强制杀死所有维度中已存在等级的实体，同时通过该指令杀死的生物不会有任何的掉落物。

> **注意**：如果使用的是混合类型系统，那么也需要将“生成距离”系统开启。

</details>

## “生物等级”插件是否会更改生物的生成机制和生成概率？

<details>
<summary>点击查看解决方案</summary>

**不，“生物等级”插件不会更改任何的生成机制。**“生物等级”插件插件只是赋予了生物在生成时的等级，同时也不会增加生物的生成概率，也不会禁止生物的生成，因此，不会对任何的生物生成机制作出更改。我们非常不喜欢在插件内添加这种模糊的操作来暗中修改游戏内容。:)

如果你服务器的生物生成出现了问题，请检查你的服务器已安装的插件和那种防止延迟的插件是否对服务器做出了更改。

</details>

## 如何为其他插件的生物增加等级或者删除等级？

### 除此之外：`level-plugins`是什么？

<details>
<summary>点击查看解决方案</summary>

在`rules.yml`文件的大概[327 到 399](https://github.com/ArcanePlugins/LevelledMobs/blob/master/src/main/resources/rules.yml#L327-L339)行，你应该可以看见一个叫`level-plugins`的文件内容。在该内容里有一个支持插件的列表，默认是关闭（`false`）状态，当你把对应插件的“`false`”更改为“`true`”时，对应插件内的生物都会被“生物等级”插件赋予等级属性。

但是对于兼容性的考虑，我们建议你将这些插件全部禁用。

</details>

## 支持哪些服务端类型？

<details>
<summary>点击查看解决方案</summary>

请查看[兼容 Wiki](https://github.com/lokka30/LevelledMobs/wiki/Compatibilities)页面。

</details>

## “生物等级”插件和其他哪些插件是兼容或者不兼容？

<details>
<summary>点击查看解决方案</summary>

请查看[兼容 Wiki](https://github.com/lokka30/LevelledMobs/wiki/Compatibilities)页面。

</details>

## 属性公式是如何计算的？

<details>
<summary>点击查看解决方案</summary>

每个属性的公式如下：

```
默认值 + ((默认值 x 配置值) x ((实体等级 - 1) / (最高等级 - 1))) = 新的数值
```

这些公式会在将来的本插件的 4 版本中进行简化。

</details>

## 这个插件会增加我的服务器延迟吗？

<details>
<summary>点击查看解决方案</summary>

不会！请放心，我们对性能进行了优化，在曾经的一些出现过延迟的服务器我们对他们进行了优化，后续已经解决了性能问题。同时我们也和其他贡献者进行了合作，更改了内存的消耗，并且以最大的努力删除不必要的代码。

</details>

## 如何使用“玩家等级”系统？

<details>
<summary>点击查看解决方案</summary>

> 在“生物等级”插件的 v3.8 版本开始，将“玩家等级”更改为“玩家等级修改器”。

### [如果你想查看本章节的视频，请点击此处！](https://www.youtube.com/watch?v=qTZ_GlQjGD8)

玩家等级系统属于额外的一种系统，它可以根据最近玩家的一些变量来修改玩家附近的生物等级。它需要等级策划和其他的策略一起运行，例如：**随机等级权重**和**生成距离**系统。这样生物就有一个基础的等级，直到拥有对用变量的玩家在其附近出现，那么就会根据变量来修改该生物的实际等级，可以使用任何 PlaceholderAPI 的占位符，例如：AureliumSkills、mcMMO、EcoSkills 等等...

以下是用于玩家等级的默认预设，在`rules.yml`文件中：

```yaml
lvl-mod_player-variable:
# 该策略会根据玩家的等级变量来修改附近的生物等级。
name: "LVLling Modifier - Player Variable AVERAGE CHALLENGE"
strategies:
  player-levelling:
  match-level: true
  use-player-max-level: false
  decrease-level: true
  recheck-players: false
  preserve-entity: 10s
  player-level-scale: 1.0
  level-cap: 30
  tiers:
    1-15: 1-10
    16-30: 11-20
    31-45: 21-25
  variable: "%level%"
```

如果你要使用其他的`变量`，你需要将`match-level`和`use-player-max-level`设置为`false`，因为它们会覆盖掉变量的值，关于它们的描述和设置，请在[Wiki](https://github.com/lokka30/LevelledMobs/wiki/Documentation---Strategies#player-variable-modifier)中查看。

当你需要更改变量时，你需要了解变量的数值范围，正常情况只能设置 50-100 的数字，或者 100000 等等更多的数字。如果你不确定范围，你可以输入`/papi parse me <placeholder>`指令查询，使用你的变量将`<placeholder>`替换为指定变量即可。当你了解到范围之后，那么你就可以根据变量的数值来设置生物的`等级`，决定了当该生物靠近玩家时将会设置的生物等级。等级左侧的数值代表的是`变量`，而右侧的值代表的是生物会被修改为的`最终等级`。

默认情况下，生物等级都可以在`rules.yml`中找到预设，但是默认是关闭状态，如果你需要开启该预设，只需要将该预设前面的注释符号`#`删除即可，例如：如果想开启`- lvl-mod_player-variable`预设，只需要将-左边的注释符号`#`删除即可开启。。

```yaml
default-rule:
  use-preset:
    - allowed_worlds
    - nametag_using_numbers
    #- nametag_using_indicator
    #- basic_challenge
    - average_challenge
    #- advanced_challenge
    #- extreme_challenge
    - weighted_random_Levelling
    #- spawn_Levelling
    #- lvl-mod_spawn-blended
    #- ycoord_Levelling
    #- random_Levelling
    - lvl-mod_player-variable
    #- lvl-mod_apply-variance
```

</details>

## 如何翻译实体或生物的名称？

<details>
<summary>点击查看解决方案</summary>

> **注意**：在[官方](https://github.com/lokka30/LevelledMobs/wiki/Official-Translations)和[非官方](https://github.com/lokka30/LevelledMobs/wiki/Unofficial-Translations)的翻译 Wiki 中有一些预设的翻译，这些翻译都是制作好的成品！如果你想将生物的名称翻译成其他的语言，你可以自由地为它们制作对应的文件，如果你的语言包含实体名称（`entity-name-override`），那么也需要将该实体的语言文本复制到对应的文件中来覆盖，详细内容请查看下方的信息页面。

请在`rules.yml`文件中查看与实体名称（`entity-name-override`）有关的那一部分，在制作本教程时有关实体名称的那一部分在`rules.yml`的第`396`行。

> **注意**：在即将制作完成的“生物等级”插件的 4 版本中，翻译的过程会被简化。:)

</details>

## “生物等级”插件是否可以让更高等级的生物掉落更多的经验或者更好的物品？

<details>
<summary>点击查看解决方案</summary>

默认情况下，当玩家击杀本插件高等级的生物都可以获得更多的战利品和经验值，等级越高经验值越多，你可以使用我们的自定义系统来自定义战利品的掉落。

</details>

## “生物等级”插件是如何运行的？

<details>
<summary>点击查看解决方案</summary>

此处有一个简单的解释，但是仅供参考：

当生物在你的服务器上生成时，本插件会检测该生物是否可以拥有等级属性，如果可以拥有，那么本插件会根据预设的系统来为该生物添加生物等级，该等级会决定了生物的经验值和战利品数量，等级越高战利品和经验值越多。同时你也可以为本插件进行自定义设置，可以为更高等级的生物设置独特的战利品，或者其他的奖励！

</details>

## 如何更改标签或生物铭牌？

<details>
<summary>点击查看解决方案</summary>

首先需要检查一下铭牌使用的是什么类型的预设。

打开`rules.yml`文件，然后找到`use-presets`部分，截止于目前制作时，`default-rule`在`rules.yml`文件的第`348`行。

在下方可以找到一个类似的预设列表：

```yaml
default-rule:
  use-preset:
    - allowed_worlds
    - nametag_using_numbers
    #- nametag_using_indicator
    ...
    ...
    ...
```

现在你使用的预设名称是`nametag_using_numbers`或者`nametag_using_indicator`，想开启或者关闭只需要在前面添加或者删除注释符号`#`即可，现在使用的预设名称是`nametag_using_numbers`。

现在你知道了你的预设的名称，现在只需要向上滚动找到该预设的那一部分，如果是`nametag_using_numbers`预设，那么在第 328 行；如果是`nametag_using_indicator`预设，那么在第 310 行，不同插件版本的行数可能会略有不同。

找到对应预设的那一部分后，可以找到以下内容：

```yaml
nametag_using_indicator:
    name: '名称标签 - 生命值铭牌'
    apply-settings:
        nametag: '&8&l༺ %tiered%Lvl %mob-lvl%&8 | &f%displayname%&8 | &f%entity-health-rounded% %tiered%%heart_symbol% &r%health-indicator% &8&l༻'
        health-indicator:
            ...
            ...
            ...
            merge: true

nametag_using_numbers:
    name: '名称标签 - 生命值数字'
    apply-settings:
        nametag: '&8&l༺ %tiered%Lvl %mob-lvl%&8 | &f%displayname%&8 | &f%entity-health-rounded%&8/&f%entity-max-health-rounded% %tiered%%heart_symbol% &8&l༻'
```

只需要在`nametag`选项中编辑对应数值的位置即可自定义格式，设置格式后需要在游戏里输入`/lm reload`指令或者重启服务器来应用更改的格式变化。

</details>

## 如何编辑生物的战利品？

<details>
<summary>点击查看解决方案</summary>

需要打开`customdrops.yml`文件，点击[此处](https://github.com/lokka30/LevelledMobs/wiki/Documentation---customdrops.yml)可前往寻找教程。

</details>

## 如何二次更改已有等级的生物难度？

#### 还有：什么是挑战？如何更改？

<details>
<summary>点击查看解决方案</summary>

我们默认为游戏添加了四种可供选择的挑战，挑战的本质也是属于难度的一种，只会对等级较高的生物影响，这取决于你服务器上设置的难度，例如：困难模式。

默认情况下，使用的难度是平均难度，功能是会生成一个具有等级的生物，和原版的难度模式类似，可以选择更低的难度来让生物更容易打，也可以使用更高的难度让生物更难打，你也可以不使用自带的预设难度去自己制作难度，这些都是完全可以自定义的。

在`rules.yml`文件的第 350 行，你可以自由选择你想要的难度，默认情况下看起来的文件格式如下：

```yaml
#- basic_challenge
- average_challenge
#- advanced_challenge
#- extreme_challenge
```

如果你想更改你服务器上的难度，请确保服务器上至少开启了一种难度，如果需要开启预设列表中的某个挑战，只需要将该挑战前面的注释符号`#`删除即可，如果想禁用的话，那就也是一样在指定的挑战前面添加注释符号`#`，例如：如果想禁用平均难度并且开启最低难度的挑战，就可以设置成如下：

```yaml
- basic_challenge
#- average_challenge
#- advanced_challenge
#- extreme_challenge
```

如果你觉得对我们设置的默认挑战不太满意的话，你可以自己去自定义一个挑战预设，建议复制一个现有的预设然后自己去修改。例如：可以自己去设置一个比困难模式还更难的挑战预设：

1. 在大约`236`行到`267`行，属于`extreme_challenge`挑战的预设，可以复制整个预设，然后修改后将其重命名为`insane_challenge`。

2. 根据你的喜好去编辑这些预设里的数值，乘法需要遵循一个公式，我们已经在疑难解答的 Wiki 中添加了该公式的描述。在我们的 Discord 频道上也有可能会有修改这些数值的支持，我们建议你去使用测试的服务器来不断地测试，直到对结果完全满意。

3. 在大约`311`行到`314`行，你可以将你制作的挑战预设添加到该列表中，然后需要确保将其他挑战的预设前面都禁用，也就是在其他挑战预设的前面添加注释符号`#`，最后在下面添加上`insane_challenge`即可。

```yaml
#- basic_challenge
#- average_challenge
#- advanced_challenge
#- extreme_challenge
- insane_challenge
```

4. 保存文件。

5. 可选：使用`/lm rules force_all`指令来将新添加的这个挑战预设应用到服务器上现有的生物上，也会让之后生成的生物都会受到本次添加的挑战预设的影响。

</details>

## 如何让刷怪笼生成的生物增加等级？

<details>
<summary>点击查看解决方案</summary>

> **注意**：为了保持游戏的平衡，我们不建议使用刷怪笼来让生物获得等级，因为有可能会造成游戏的货币通胀，如果你不想让那些基于摔落伤害的刷怪塔失效，那么请不要更改刷怪笼在生成生物时的生命值。

在`rules.yml`文件的第`325`行，找到`allowed-spawn-reasons`，然后将

```yaml
conditions:
  allowed-spawn-reasons:
    excluded-list: ["SPAWNER"]
```

更改为

```yaml
conditions:
  allowed-spawn-reasons:
    excluded-list: []
```

最后如果一切设置完毕，那么刷怪笼在生成生物时将会自动获得等级属性。

</details>

## 如何将拥有名称的生物排除在等级之外？

<details>

<summary>点击查看解决方案</summary>

在`rules.yml`文件中搜索以下内容：

```yaml
mob-customname-status: EITHER
```

插件的不同版本可能会更改行数，但是默认是 347 行，并且将上述的内容更改为以下内容：

```yaml
mob-customname-status: NOT_NAMETAGGED
```

保存文件后输入`/lm rules force_all`指令来应用本次更改。

</details>

## 我应该如何更改生物的最高等级？

<details>
<summary>点击查看解决方案</summary>

首先，请确保你使用的挑战预设。

在`rules.yml`文件的第`311`行到`314`行，如果你看到了下面这种情况，那么说明你有可能在之前就已经修改好了：

```yaml
#- basic_challenge
- average_challenge
#- advanced_challenge
#- extreme_challenge
```

我们注意到在这个例子中开启了`average_challenge`挑战预设，这个预设在`rules.yml`文件的`212`行左右设置的。如果你不使用该挑战预设，那么你需要修改为其他挑战的预设，例如：基础挑战，也就是`basic_challenge`预设。

如果你的是`average_challenge`预设，那么你可以在第`175`行看见以下内容：

```yaml
average_challenge:
  name: "Average-Challenge Multipliers"
  apply-settings:
    minLevel: 1
    maxLevel: 25
    multipliers:
      max-health: 5.0
      movement-speed: 0.15
      attack-damage: 2.25
      ranged-attack-damage: 2.25
      creeper-blast-damage: 0.7
      #... continues ...
```

要目前挑战预设里的生物最高等级，只需要将`maxLevel`数值从`25`更改为`50`或者`其他更高的数字`，你拥有完全的自定义权限，尽情的随心所欲吧！

一旦你将编辑操作完成后请保存文件，然后我们建议你使用`/lm rules force_all`指令来将更改内容重新应用到你的服务器上，来让这些现有等级的生物的最高等级从`25`更改为`50`或者更高。:)

</details>

## 如何从其他插件（例如：ExecutableItems、ItemsAdder 和 EcoItems）中制作自定义掉落物？

<details>
<summary>点击查看解决方案</summary>

使用的 PenalBuffalo 插件的[等级物品](https://www.spigotmc.org/resources/lm-items.102081/)拓展插件。

</details>

## 如何增加生物的属性（例如：生命值）设置超过 2048？

<details>
<summary>点击查看解决方案</summary>

“生物等级”插件并没有限制该数值，这是因为你的服务器类型问题。

在`spigot.yml`文件中，可以增加对应属性的最大值：

```yaml
attribute:
  maxHealth:
    max: 2048.0
  movementSpeed:
    max: 2048.0
  attackDamage:
    max: 2048.0
```

请注意：我的世界原版并不是为了更多数值而设置的，如果你将属性的数值突破限制设置成更高的话，请务必注意游戏平衡。

</details>

## 生物等级是否也适合用于玩家等级？

<details>
<summary>点击查看解决方案</summary>

不，没有。我们制作这个插件并不是为了增加玩家的等级，只是为了增加生物的等级而已，如果你想增加玩家的其他等级，推荐使用 [AureliumSkills（免费）](https://www.spigotmc.org/resources/aurelium-skills-advanced-skills-stats-abilities-and-more.81069/)或者[McMMO（付费）](https://www.spigotmc.org/resources/official-mcmmo-original-author-returns.64348/)插件。

</details>

## MythicMob 插件的实体不能正常升级或者缩放？

<details>
<summary>点击查看解决方案</summary>

在 MythicMobs 插件的 2.5.6 版本中，对于 MythicMobs 插件的安装配置方式做出了部分的修改。默认情况下，可以通过 MythicMobs 自带的机制来实现生物等级的升级和缩放，这和“生物等级”插件是完全分离的。“生物等级”插件会检测一个完整的实体，然后再将等级给予该实体，如果 MythicMobs 插件依旧完全激活了系统，那么在“生物等级”插件给予等级之前它们完全可以随机获得不断增加的属性。

为了将实体重置为普通数值，你可以在 MythicMobs 中完全禁用缩放系统而只是用“生物等级”插件里的属性，或者返左来操作，虽然我们推荐你使用我们的这个系统而不是使用他们的，但是这最后的选择权在你的手上！如果要禁用缩放的话，请在 MythicMob 插件的`config.yml`文件中将每个维度的`Enabled`设置为`false`，你也可以使用修改器来针对这些内容做出调整。

![MM Config.YML](https://i.ibb.co/KV2jsP9/image.png)

</details>

## 没找到你的问题？

请假如 ArcanePlugins 的[Discord](https://www.discord.io/arcaneplugins)频道然后反馈你的问题。
