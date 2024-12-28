```
本页最后更新于 LevelledMobs 3.13.0 b793
```

---

这些条件表示在应用任何**策略**或**应用设置**之前，针对实体可用的许多不同检查。
**注意**: 你的默认 `rules.yml` 文件可能不包含每个潜在的 `condition`、`strategy` 或 `apply-settings`，因此请定期查看 wiki 获取任何新的更新信息！

你可以参考上面的'最后更新'消息，了解本页的最后修改时间。

```yml
conditions:
  allowed-spawn-reasons:
  allowed-worldguard-regions:
  allowed-worldguard-region-owners:
  apply-above-y: 62
  apply-below-y: 62
  apply-plugins:
  biomes:
  custom-names:
  chance: 1.0
  entities:
  maxLevel: 50
  minLevel: 1
  max-distance-from-spawn: 100
  min-distance-from-spawn: 100
  mob-customname-status: EITHER
  mob-tamed-status: EITHER
  mythicmobs-internal-names:
  permission:
  spawner-names:
  scoreboard-tags:
  stop-processing: true
  within-coordinates:
    start-x:
    end-x:
    start-y:
    end-y:
    start-z:
    end-z:
  worlds:
  world-time-tick:
  cooldown-duration:
  cooldown-limit:

  level-plugins:
    DANGEROUS_CAVES: false
    ECO_BOSSES: false
    MYTHIC_MOBS: false
    ELITE_MOBS: false
    ELITE_MOBS_NPCS: false
    ELITE_MOBS_SUPER_MOBS: false
    INFERNAL_MOBS: false
    CITIZENS: false
    SHOPKEEPERS: false
    SIMPLE_PETS: false
```

|                         配置行选项                         |                                                                                                                                                                        描述                                                                                                                                                                        |
| :--------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                `minLevel:`<br />`maxLevel:`                |                                                                          这些特定的配置选项是在 LM 计算实体等级后检查等级的。<br />**示例:** 一个转化实体，比如从僵尸村民变成普通僵尸；或者根据规则系统内的条件，为实体应用 `use-droptable-id:` 而不是 CustomDrops 系统。                                                                          |
|                         `chance:`                          |                                                                                                                       这代表一个自定义规则发生的几率。否则将被跳过。<br />**示例:** 设置 `chance: 0.5` 将会得到 50% 的几率。                                                                                                                       |
|                     `stop-processing:`                     |                                                                                                               这代表一个强制性的停止对排队的自定义规则堆栈进行处理。一旦触发了包含此配置选项的规则，将阻止未来任何自定义规则的处理。                                                                                                               |
|     `mob-customname-status:`<br />`mob-tamed-status:`      |                     这些配置选项表示实体是否设置了 CustomName 或已被驯服：<br />`NOT_SPECIFIED` - 默认状态，基本上没有被检查或使用<br />`EITHER` - 实体的 CustomName 或驯服状态不重要<br />`NAMETAGGED` / `TAMED` - 实体需要有 CustomName 或已被驯服<br />`NOT_NAMETAGGED` / `NOT_TAMED` - 实体不应该有 CustomName 或未被驯服                      |
|                         `worlds:`                          |                                                                                                                                            一个 `MODALLIST` 配置选项；这代表对实体生成的世界进行检查。                                                                                                                                             |
|           `apply-above-y:`<br />`apply-below-y:`           |                                                                                                                                                    这检查实体是否位于特定的 Y 坐标之上或之下。                                                                                                                                                     |
|                     `world-time-tick:`                     |                                                  一个 `MODALLIST` 配置选项；这代表世界中当前的时间，以刻度表示。Minecraft 中的 24 小时为 `0-24000` 的世界刻度值。你可以通过引用 [此链接](https://minecraft.fandom.com/wiki/Daylight_cycle#24-hour_Minecraft_day) 来更好地了解 Minecraft 的时间。                                                   |
| `min-distance-from-spawn:`<br />`max-distance-from-spawn:` |                                                                                                                                                  这检查实体是否距离生成坐标的最小或最大距离之内。                                                                                                                                                  |
|               `allowed-worldguard-regions:`                |                                                                                                                                      一个 `MODALLIST` 配置选项；这代表对实体生成的 WorldGuard 区域进行检查。                                                                                                                                       |
|            `allowed-worldguard-region-owners:`             |                                                                                                                                一个 `MODALLIST` 配置选项；这代表对实体生成的 WorldGuard 区域的所有者列表进行检查。                                                                                                                                 |
|                  `allowed-spawn-reasons:`                  | 一个 `MODALLIST` 配置选项；这代表对可能的生成原因标志进行检查。<br />你可以参考 [SpigotMC javadocs](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html) 中关于 `CreatureSpawnEvent.SpawnReason` 的不同选项。你也可以使用 `LM_SUMMON` 或`LM_SPAWNER`，即通过 `/lm summon` 或`/lm 命令创建的实体。 |
|                      `custom-names:`                       |                                                                                                                                一个 `MODALLIST` 配置选项；这代表当应用等级时，检查实体的 CustomName，假设它有一个。                                                                                                                                |
|                        `entities:`                         |                                                                                                                                              一个 `MODALLIST` 配置选项；这代表应用自定义规则的实体。                                                                                                                                               |
|                         `biomes:`                          |                                                                                                                                          一个 `MODALLIST` 配置选项；这代表对实体生成的生物群系进行检查。                                                                                                                                           |
|                `mythicmobs-internal-names:`                |                                                 一个 `MODALLIST` 配置选项；这代表对 MythicMob 自定义怪物的内部名称进行检查。<br />**注意:** 我们在特别与 **MM5** 的兼容性方面遇到了几个问题。我们正在等待 **MM** 团队的解决方案。在解决此问题之前，我们建议继续使用 **5.0.0** 之前的 **MM** 版本。                                                 |
|                      `apply-plugins:`                      |                                                                                                                                   一个 `MODALLIST` 配置选项；这代表检查生成的实体是否来自于一个内部支持的插件。                                                                                                                                    |
|                      `level-plugins:`                      |                                                                                                                   与上面的 `apply-plugins:` 以类似的方式工作，使用了规则系统中的不同格式，以便于方便使用（尽管它们是可互换的）。                                                                                                                   |
|                     `scoreboard-tags:`                     |                                                                                                                                                一个 `MODALLIST` 配置选项；如果一个实体包含计分板标                                                                                                                                                 |

签，你可以使用它来包含或排除它们。
|`spawner-names:`| 一个 `MODALLIST` 配置选项；这代表对创建实体的 `LM Spawner` 的名称进行检查。
|`permission:`| 一个 `MODALLIST` 配置选项；这代表对实体最近的玩家，或者杀死实体的玩家的检查，具体取决于它的实现。所有权限都被注册为 `levelledmobs.permission.<node>`，其中 `<node>` 表示此配置的值。例如，如果你的权限是 `levelledmobs.permission.vip`，你将配置为 `permission: ['vip']`。
|`cooldown-duration:`| 当配置了规则并使用它时，它将在冷却时间过期之前有效地禁用规则。
|`cooldown-limit:`| 当配置了 `cooldown-duration:` 时，规则必须执行的次数，然后规则在一段时间内被禁用。
|`within-coordinates:`<br />`start-` `end-`|这个系统允许你设置 `start-` 和 `end-` 坐标，以定义一个要应用规则的世界内区域。你可以只指定一个轴来标记一个点或线；指定两个轴来制作一个沿着这两个轴的正方形；或指定三个轴来制作一个长方体区域。你还可以将 `'-'` 或 `'+'` 作为任何坐标的 `end-`，并且它将从 `start-` 值开始到指定的方向的无限大。最后，如果指定了 `start-` 但未指定 `end-`，则 `end-` 将与 `start-` 值相同；反之亦然。

---
