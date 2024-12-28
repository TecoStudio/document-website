```
此页面最后更新为 LevelledMobs 3.9.3 b735
```

---

LevelledMobs 的 `rules.yml` 文件允许你创建真正模块化的 **自定义规则**，这些规则可以修改或扩展应用于任何和所有 EntityTypes 的 **默认规则**。
该规则文件分为三个主要部分：**预设规则**、**默认规则** 和 **自定义规则**；尽管主要功能是通过 _建立默认规则_ 来对所有在已建立的默认条件下的实体进行级别设置，然后通过 _添加自定义规则的形式对默认规则进行异常规则_，在这些条件下可以建立一组条件，这些条件将在默认规则下应用更改。我们创建了预设规则部分，以便可以快速添加到默认规则或自定义规则中的任何经常引用的条件或设置，以帮助减小文件的大小，尽管你不必引用或包含预设规则部分，只要你已手动编写了条件和设置。

# 默认规则

`rules.yml` 文件中的 `default-rule:` 部分建立了大多数实体级别设置的规则。这为 LevelledMobs 提供了一个基线，用于在设置实体属性和级别时进行工作。在默认配置下，我们充分利用 `presets:` 部分来建立大多数的默认 `conditions:`。这些预设包括 `allowed_worlds`、`weighted_random_Levelling`、`average_challenge` 和 `nametag_using_numbers`。如果你引用相同名称的 `presets:`，你将看到包括各种 `conditions:`、`strategies:` 和 `apply-settings:`的这些预设。由于它们在 `default-rule:` 中引用，因此每个这样的 `presets:` 本质上都会被复制到 `default-rule:` 中。如果在同一个默认规则下设置了相同的配置选项，则只会监听最后一个。

对于 `default-rule:`，你需要告诉 LevelledMobs 的最低要求是：你希望在哪些世界中应用 LevelledMobs，你希望使用哪种策略来设置实体的级别，以及你希望这些实体有多强大。次要设置包括诸如将名牌应用于实体以显示其更改后的属性和数值，或者设置限制从生成方块中获得级别的实体的条件。

一般来说，你希望你的 `default-rule:` 尽可能地开放，以符合你对服务器的开放性。这一部分旨在从一开始限制 LevelledMobs 所做的更改，从特定世界中将其完全删除到建立总体使用的核心策略。不要担心，你可以通过自定义规则进行任何需要的更改。

# 自定义规则

`rules.yml` 文件中的 `custom-rules:` 部分建立了对默认规则的任何例外的规则。在默认配置下，我们使用了四个不同的自定义规则，这些规则提供了经过玩家测试的例外规则，我们认为这些规则有助于提高整体体验。每个规则都可以根据服务器的需要进行更改或删除。

> CR - NoLevel 所有被动 + 实体类型

```yaml
- enabled: true
  name: "CR - NoLevel 所有被动 + 实体类型"
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

默认情况下，选定的 `default-rule:` 世界中的所有实体都会接收一个级别。
第一个自定义规则设置了一个条件检查：所有属于“被动”组的实体，Minecraft 将这些实体视为鸡、猪、绵羊等实体，一些特定的实体（`'ENDER_DRAGON', 'WITHER', 'VILLAGER', 'ZOMBIE_VILLAGER', 'WANDERING_TRADER', 'PHANTOM', 'BAT', 'RAVAGER', 'WARDEN'`），以及所有 `BABY_` 实体（代表所有幼年实体）。
然后，我们告诉 LevelledMobs，如果出现这些实体中的任何一个，我们将设置 `maxLevel: 0`。当实体级别为 0 时，LevelledMobs 将不会受到任何更改的影响，被视为未受 LevelledMobs 影响的实体。
之所以选择这些实体，原因各不相同，有些明显，有些不太明显。对我们来说，只有敌对实体受到级别设置是有意义的，我们取消了对像村民、僵尸村民、流浪商人等实体的级别设置，以保护它们的特性。然后还有像蝙蝠这样被视为“中立”生物的生物的生物，以及迷你 Boss 、凋零使者和末影龙这样的“最终 Boss”，让用户决定如何释放这些实体。

> CR - 自定义下界级别设置

```yaml
- enabled: true
  name: "CR - 自定义下界级别设置"
  conditions:
    worlds: "world_nether"
  strategies:
    y-coordinate:
      start: 100
      end: 40
      period: 0
```

默认情况下，选择的 `default-rule:` 中的任何世界都将使用在其中建立的策略

来应用级别。虽然这是可以接受的，但考虑到下界世界更像是一个垂直地图，更改策略从 `weighted-random` 更改为 `y-coordinate` 会更有意义。通过此更改，下界中的所有实体都将遵循 `default-rule:`，但有一个例外，即更改要应用的策略。

> CR - 自定义实体属性

```yaml
- enabled: true
  name: "CR - 自定义实体属性"
  use-preset: allowed_worlds
  apply-settings:
    multipliers:
      custom-mob-level:
        ENDERMAN:
          max-health: 0.0
          movement-speed: 0.0
        SILVERFISH:
          max-health: 0.0
          movement-speed: 0.0
        CREEPER:
          movement-speed: 0.025
        WITHER_SKELETON:
          max-health: 1.0
```

默认情况下，根据 `default-rule:` 下的级别设置，对任何实体进行级别设置将使用在那里建立的增益来确定属性更改的程度。一直以来，我们已经了解到某些对于普通服务器的异常情况应该进行设置。每个这些设置都可以根据你的需要进行更改或删除。
此自定义规则使用了 `multipliers:` `apply-settings:` 的子部分，称为 `custom-mob-level:`，它允许你为特定实体建立默认增益（在默认的 `average_challenge` 中建立）进行更改。

我们首先修改的实体是末影人，我们建立了这样的设置：当末影人受到级别设置时，不会更改其 `max-health:` 和 `movement-speed:`。这样做的目的是，在标准环境中，当你攻击末影人时，它们通常会获得大量的移动速度和传送能力。如果将末影人完全设置为级别，生命值和移动速度的增加将使它们几乎不可能被杀死。这也有助于防止玩家建造的末影人农场被破坏的情况。
第二个实体是蠹虫，出于类似的原因，取消了 `max-health:` 和 `movement-speed:` 的更改。
第三个实体是爬行者，它的 `movement-speed:` 设置了一个较低的上限。尤其是在级别设置时，爬行者可能具有挑战性。降低移动速度可以防止爬行者向玩家冲过来，从而使玩家在爆炸前有机会逃脱。
第四个实体是凋零骷髅，其凋零能力使得即使在标准规则下也具有挑战性。这个调整的 `max-health:` 有助于减轻这些实体的挑战难度，同时保持它们的增加的攻击伤害和移动速度等其他 `multipliers:`。

> CR - 自定义僵尸猪灵级别设置

```yaml
- enabled: true
  name: "CR - 自定义僵尸猪灵级别设置"
  conditions:
    worlds: "world_nether"
    entities: "ZOMBIFIED_PIGLIN"
  strategies:
    random: true
  apply-settings:
    minLevel: 1
    maxLevel: 5
    multipliers:
      max-health: 1.0
      movement-speed: 0.25
      attack-damage: 0.5
      ranged-attack-damage: 0.0
      item-drop: 0.5
      xp-drop: 1.0
    tiered-coloring:
      1-5: "&#22E76B" #绿色
```

默认情况下，如果不设置此规则，僵尸猪灵将像在此之前的下界中的任何其他敌对实体一样进行级别设置。僵尸猪灵是少数在受到攻击时会组成队伍反击的实体之一，特别是这类实体会形成一支小队，长时间追赶玩家。我们发现如果让僵尸猪灵根据 `default-rule:` 的规则设置级别，它们将变得难以挑战，会使下界通常难以探索。
在此自定义规则下，我们已经设置了在下界中的任何 `ZOMBIFIED_PIGLIN` 进行条件检查。这些实体将采用其 `default-rule:` 的增益，并将这些值替换为此自定义规则中建立的值；所有这些值都低于默认的调整。我们还提供了一个独特的 `tiered-coloring:`，它调整了名牌中的 `%tiered%` 输出；这只是一种纯粹的外观变化。

这些自定义规则提供了对实体级别设置的精细控制，允许服务器管理员根据其所需的游戏体验进行级别设置。

如果你有任何具体问题或需要进一步澄清有关 LevelledMobs 配置的任何方面，请告诉我。
