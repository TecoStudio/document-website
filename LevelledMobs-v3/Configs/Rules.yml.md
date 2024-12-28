```
本页最后更新于 LevelledMobs 3.10.3 b763
```

---

LevelledMob 的 `rules.yml` 文件允许你制作真正模块化的 **自定义规则**，它可以修改或扩展应用于任何和所有 EntityType 的 **默认规则**。
规则文件分为三个主要部分：**预设**、**默认规则**和**自定义规则**。
本文档提供了对规则文件如何工作的一般理解。

有关更多详细信息，请了解如何使用不同的[条件](https://github.com/lokka30/LevelledMobs/wiki/Documentation---Conditions)、[策略](https://github.com/lokka30/LevelledMobs/wiki/Documentation---Strategies)和[应用设置](https://github.com/lokka30/LevelledMobs/wiki/Documentation---Apply-Settings)。

---

# 通用生物群组:

LevelledMobs 包含多组实体，这些实体以易于识别的格式捆绑在一起。当使用`allowed-groups:`或`excluded-groups:`时，每个组都充当自己的 EntityType，这允许你一次选择多个实体。 你可以合并`included-list:` 或 `excluded-list:`来对组内的特定实体进行例外处理。

你还可以在规则文件中创建自己的实体或生物群系自定义分组。这些组目前无法在自定义掉落中使用，但将来可以访问；请稍后再回来查看！

|   实体类型通用群组    | 描述                                       |
| :-------------------: | :----------------------------------------- |
|      `all_mobs`       | 所有实体，无论它们是否被等级化。           |
| `all_levellable_mobs` | 所有已经被等级化的实体。                   |
|  `all_hostile_mobs`   | 所有敌对实体，无论它们是否被等级化。       |
|  `all_passive_mobs`   | 所有被动实体，无论它们是否被等级化。       |
| `all_overworld_mobs`  | 所有主世界中的实体，无论它们是否被等级化。 |
|   `all_nether_mobs`   | 所有地狱中的实体，无论它们是否被等级化。   |
|   `all_flying_mobs`   | 所有飞行实体，无论它们是否被等级化。       |
|   `all_ground_mobs`   | 所有陆上的实体，无论它们是否被等级化。     |
|  `all_aquatic_mobs`   | 所有水生的实体，无论它们是否被等级化。     |

---

# 预设:

LM 允许你将某些配置选项集成到称为**预设**的集合中，这些预设可以在**默认规则**或使用 `use-preset:` 配置行的任何**自定义规则**中应用。例如：

```yml
custom-rules:
  - enabled: true
    name: '自定义规则'
    use-preset: presetName, otherPresetName
    use-preset:
      - presetName
      - otherPresetName
```

```yml
presets:
  presetName:
    name: "预设名称"
    system:
```

**预设**部分覆盖文件的前三分之一，默认情况下，它主要用于填充**默认规则**，并为常见问题提供多种不同的开箱即用的解决方案！ 你可以编辑自己的预设或将其添加到列表中，也可以压根不使用预设系统。 这有助于防止规则文件中出现重复文本。

制作预设时，应遵循上述结构。 从`presets:`标签开始，缩进两个空格，然后为预设指定一个名称以供稍后引用，并将`presetName:`替换为该值。 确保该值仅使用字母数字值，不包含空格。
紧接着，再缩进两个空格，你应该为你的预设指定一个易于阅读的`name:`。 尽管这不是必需的，但你稍后会感谢自己！
最后，`system:`代表`conditions:`、`strategies:`和`apply-settings:`，具体取决于你想要构建的预设类型！

# 默认规则：

LM 要求此部分填充以下最少的信息，以便使用最少的功能。 默认情况下，LM 使用上面解释的 **预设** 系统来使用必要的值以及其他几个值填充默认规则，以便快速轻松地在预配置设置之间切换。

```yml
default-rule:
  conditions:
    worlds:
      allowed-list: ["*"]
    strategy:
      random: true
    apply-settings:
      minLevel: 1
      maxLevel: 25
      multipliers:
        max-health: 5.0
        movement-speed: 0.15
        attack-damage: 2.25
        ranged-attack-damage: 2.0
        creeper-blast-damage: 1.0
        item-drop: 3
        xp-drop: 5
      nametag: "&8&l༺ %tiered%Lvl %mob-lvl%&8 | &f%displayname%&8 | &f%entity-health-rounded% %tiered%%heart_symbol% &r%health-indicator% &8&l༻"
      creature-death-nametag: "%tiered%Lvl %mob-lvl%&8 | &f%entity-name%"
```

# 自定义规则：

LM 开箱即用，具有多种不同的**自定义规则**，这些规则均可以被启用和禁用。
这些用于实现特定结果，例如使用第一个自定义规则禁用被动实体的等级化，并提供如何以独特方式使用自定义规则的多个示例。

## 优先级：

默认情况下，LM 按线性顺序处理规则：从上到下； 从默认规则到第一条至最后一条自定义规则。 你可以在自定义规则中建立优先级配置行，该规则将覆盖其在队列中的位置，从而允许其比堆栈的其余部分更早或更晚处理。 请记住，默认规则将**始终**在任何自定义规则之前被首先处理，以填充任何必要的默认值。
下面展示了优先级如何改变自定义规则的“堆栈队列”的示例：

```yml
custom-rules:
  - enabled: true
    name: "在堆栈之前运行，作为最高优先级，作为默认规则之后处理的第一条规则"
    priority: 2

  - enabled: true
    name: "在堆栈之前运行，在任何更高优先级之后运行"
    priority: 1

  - enabled: true
    name: "运行排队堆栈（与不列出优先级相同）"
    priority: 0

  - enabled: true
    name: "运行排队堆栈（与优先级相同：0）"

  - enabled: true
    name: "在堆栈之后、任何较低优先级之前运行"
    priority: -1

  - enabled: true
    name: "在堆栈后面运行，优先级最低，在最后运行"
    priority: -2
```

以下表示自定义规则的基本框架:

```yml
custom-rules:
  - enabled: true
    priority: 1
    name: ""
    use-preset:
    conditions:
    strategies:
    apply-settings:
```

- `- enabled:` - 这表示自定义规则会被启用还是禁用.
- `priority:` - 该值会覆盖自定义规则的处理顺序.
- `name:` - 这代表了用于调试目的的自定义规则的易于阅读的表示.
- `use-preset:` - 这允许你在自定义规则中使用预设.
- `conditions:`, `strategies:`, 及 `apply-settings:` - [这里有更为详细的说明](#).

在构建应用于实体的最终自定义规则时，自定义规则中未明确列出的任何详细信息都将从默认规则中收集该信息。 例如：

```yml
default-rule:
  conditions:
    worlds:
      allowed-list: ["*"]
    entities:
      allowed-list: ["all_mobs"]

custom-rules:
  - enabled: true
    name: "禁用被动实体"
    conditions:
      entities:
        allowed-list: ["all_passive_mobs"]
    apply-settings:
      maxLevel: 0
```

上面结构的解读方式，从默认规则开始：所有世界都是等级化的，所有实体都是基于默认规则的等级化的。 制定自定义规则时，我不需要指定规则将应用于哪个世界，因为它从默认规则中获取值“所有世界”。 但是，我必须指定实体，因为如果我不指定，自定义规则将适用于默认规则中所述的“所有实体”。 最后，我应用了级别`0`，它禁用了所有世界中被动实体的等级化。

---

> 注意：某些配置选项使用自定义`MODALLIST`来配置。  
> 下面演示如何使用 MODALLIST 功能:

```yml
allowed-list: [""]
allowed-groups: [""]
excluded-list: [""]
excluded-groups: [""]
merge: true
```

`MODALLIST` 配置选项的阅读相当简单，因为它们仅在条件部分中使用。
如果配置选项需要使用 `MODALLIST` , 例如 `entities:` 和 `worlds:`, 那么你使用哪个配置选项取决于你的需求。

**示例:** 如果要检查条件是否满足一个实体是僵尸，你将使用 allowed-list:，意味着列表只允许你批准的满足条件的实体。

**示例:** 如果你希望条件适用于除僵尸之外的所有实体，那么你可以使用`excluded-list:`, 这意味着该列表将使用除你排除满足条件的实体之外的所有实体。

**示例:** 如果要应用于 all_passive_mobs 组，但要跳过鸡，则可以使用 `allowed-groups:` 和 `excluded-list:`,你将允许组中的所有被动实体满足条件，而你的`excluded-list:`将在最终处理之前被删除。

某些`MODALLIST`配置选项无法使用'-groups'行，因为这些选项仅限于实体和生物群系自定义或通用组。 如果你希望组合默认规则和自定义规则中两个不同`MODALLIST`的列表，则只需在配置列表的末尾添加`merge: true`行即可将两者组合在一起。
