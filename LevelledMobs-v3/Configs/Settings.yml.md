```
本页信息最后更新为“生物等级”插件的3.13.3 b801版本。
```

---

# 如果实体已死亡，插件应该停止发送数据包吗？

```yaml
assert-entity-validity-with-nametag-packets: true
```

- `true` - 如果实体的生命值达到了 0，那么与该实体有关的数据包将不再会发送。

- `false` - 如果实体的生命值达到了 0，那么插件有可能会发送额外的数据包来尝试保持该实体的生命值铭牌等数据是准确的。

添加该设置是因为会尝试修复与 ViaBackwards 的兼容，默认情况下，ViaBackwards 会检测到“生物等级”插件实体死亡时的名称标签数据。

我不建议你更改此项设置，除非你知道你在做什么。

# 自动同步异步名称标签和等级

```yaml
async-task-update-period: 6
async-task-max-blocks-from-player: 100
```

该选项可以检查玩家附近 X 格以内的生物是否应该拥有等级、生物铭牌或者某个缺少的属性，其中 X 是`async-task-max-blocks-from-player:`。

其中，`async-task-update-period:`选项的单位是秒。

# 自定义`command`指令限制

```yaml
customize-summon-command-limit: 10
```

该选项的目的是限制使用`/lm summon`指令时的召唤实体的数量上限。

防止因为意外地让召唤数量过多而让服务器崩溃或者溢出。

# 头颅掉落倍率

```yaml
mobs-multiply-head-drops: false
```

- `true` - 生物头颅的掉落概率**不会**增加。
- `false` - 生物头颅的掉落概率**会**因为其他原因而增加，例如：抢夺附魔。

在有的服务器里，头颅会被视作为珍惜资源，不能与该实体的其他掉落物相提并论。这个设置是允许你决定这些头颅类的掉落物是否可以跟其他掉落物一样受到不同的可以增加掉落物数量的东西影响。

# 自定义掉落指令限制

```yaml
customcommand-amount-limit: 100
```

这有助于防止服务器的意外崩溃，因为有的实体在死亡时可能执行的指令数量可能会超过服务器的上限，从而造成服务器的崩溃。使用该选项可以通过本插件的自定义掉落系统来为掉落物设置一个强制的限制，防止指令的`数量`上限超过该数值。

# 生物处理延迟

```yaml
mob-process-delay: 0
```

设置“生物等级”插件在执行为生物给予等级或者其他操作时的处理延迟，单位是 tick。增加延迟只是为了给予其他插件更高的优先级，防止可能会造成的冲突。

我不建议你更改此项设置，除非你知道你在做什么。

# 召唤指令 - 与玩家的距离

```yaml
summon-command-spawn-max-distance-from-player: 5
```

在使用`/lm summon <数量> <实体> <登记>`指令时，生物生成与使用指令玩家之间的最大距离。

```yaml
summon-command-spawn-min-distance-from-player: 3
```

在使用`/lm summon <数量> <实体> <登记>`指令时，生物生成与使用指令玩家之间的最小距离。

# kill 指令忽略实体

```yaml
kill-skip-conditions:
  nametagged: true
  tamed: true
  leashed: true
  convertingZombieVillager: true
```

对于 kill 指令的实体忽略：

- `true` - 当实体受到来自“生物等级”插件里的 kill 指令时**会**被忽略。
- `false` - 当实体受到来自“生物等级”插件里的 kill 指令时**不会**被忽略。

设置当你使用`/lm kill`指令时可以忽略哪些实体。

防止对宠物或者其他类型的实体造成不必要的麻烦。

我不建议你更改此项设置，除非你知道你在做什么。

# 使用翻译组件

```yaml
use-translation-components: true
```

- `true` - 任何默认名称的实体都会根据玩家客户端上的语言来显示。
- `false` - 在一些旧版本和定制的客户端上不支持该功能，所以如果你的服务器的环境不需要让玩家使用客户端的语言切换实体名称，那么请禁用该功能。

在这个系统中提供了一种可以更改语言的机制，大多数情况下都应该将这个功能设置为启用。在一些旧版本和定制的客户端上可能会破坏名称的显示方式，如果你不需要这个功能，请禁用它。你可以参考应该英文名称列表，但是你也依旧可以通过`rules.yml`文件的`apply-setting: entity-name-override:`功能来修改实体的名称。

# 检测已加载区块的实体

```yaml
ensure-mobs-are-levelled-on-chunk-load: true
```

- `true` - 靠近玩家的那个区块会检测是否有实体拥有本不该属于该实体的等级。
- `false` - 任何实体都不会被重复检测。

这个功能就类似看门的一样，可以检测附近玩家已加载的区块中是否存在那些应该拥有更高等级的实体而现在却拥有更低等级。

如果你不了解这个功能，请不要修改它。

# 使用属性预设的基础值

```yaml
attributes-use-preset-base-values: false
```

- `true` - 使用预设的属性默认值。
- `false` - 使用被生成实体中生成的默认属性值。

在“生物等级”的 v2 版本中，我们会使用一个静态文件内的属性来生成实体，可以解决部分存在的兼容性问题。从此版本开始，我们已经修改了属性的生成和修改方式，因为考虑到种种情况，所以我们设置了一个存放属性的文件来备份这种情况，如果你不知道你在做什么，我们不建议你来更改此选项。

# 实体名称使用“CustomName”

```yaml
use-customname-for-mob-nametags: false
```

- `true` - 实体使用`CustomName`名称标签。
- `false` - 通过 ProtocolLib 插件使用数据包来修改“生物等级”插件的生物铭牌。

在“生物等级”插件的 v2 版本之前，我们在为实体生成铭牌时使用的是与**真实实体**相关的内容，这导致与其他插件冲突，并且当玩家在给生物使用命名牌的时候会被覆盖。

在“生物等级”插件的 v2 版本之后，我们通过 ProtocolLib 插件的数据包来为生物生成铭牌，因为该插件考虑到了玩家的不同名称标签等因素。

作为一个备用方案，我们添加了该设置，以便你随时将它们恢复成之前的那种形式，即使用“生物等级”插件的 v1 版本的格式，我们不建议更改此选项，因为。

**此选项一旦更改将不可逆！！！**

# 反馈生成（summon）指令至玩家/控制台（服务器端后台）

```yaml
print-lm-summon-results: true
```

- `true` - 输出反馈至控制台（服务器端后台)
- `false` - 不输出反馈

这个设置配置了，使用生成指令（summon）的时候是否输出到控制台（服务器端后台）。当你频繁使用生成指令（Summon）时，可以禁用`false`来减少控制台输出。

# 生成生物时获得等级

```yaml
level-mobs-upon-spawn: true
```

- `true` - 当生物在生成在世界中时，“生物等级”插件会立即给予该生物一个等级。
- `false` - 实体在受到玩家伤害和进攻玩家之前不会获得任何等级。

# 区块击杀统计

```yaml
exceed-kill-in-chunk-message: true
```

- `true` - 当目前的区块生物的死亡数量达到区块上限时，将会向击杀生物的玩家发送一条信息。
- `false` - 不会向任何玩家发送当前区块生物的死亡数量达到上限的任何信息。

# 检查实体哈希值

```yaml
check-mob-hash: true
```

这是`LM 3.12.0 b770`版本的一个新功能，由生物等级插件生成的实体会生成哈希值。哈希值会在服务器启动或者使用`/lm reload`刷新时生成哈希值，且哈希值在`rules.yml`文件中设置和`layout` 配置中是唯一的。此设置监听生物与目前配置文件的哈希值是否匹配。同时，会在区块加载和等级确认监听器使用时进行检查（ps. 默认是等待六秒后开始检查）。建议启用此设置，用于检查那些实体生成在那些非加载区块之中。

- `true` - 开启时，若实体判定为缺失或者拥有失效的哈希值，则根据现有配置文件重新更新实体和哈希值。
- `false` - 禁用时，则不会在区块加载时检查实体的哈希值，并更新实体。

# 玩家等级策略

```yaml
player-levelling-relevel-min-time: 5000
```

`player-levelling-relevel-min-time:`的意思是在实体被更新为距离其最近玩家的时间，单位是毫秒，将该值设置为`0`可阻止任何的等级分配。

该设置是围绕**玩家等级**策略系统而制作的。

# 名称标签占位符距离

```yaml
nametag-placeholder-maxblocks: 30
```

`nametag-placeholder-maxblocks:`的意思是设置实体在`%levelledmobs_mob-target%`下与玩家的渲染距离。

# 更新和调试模式

```yaml
use-update-checker: true
debug-entity-damage: false
debug-misc: [""]
file-version: 30
```

`use-update-checker:`如果设置为`true`，那么在服务器启动时会对拥有管理器权限的玩家通知“生物等级”插件是否有最新版本。

`debug-entity-damage:`如果设置为`true`，那么当你攻击实体时会在游戏中显示该实体的详细属性信息。

`debug-misc:`更多内容请在[settings.yml/Debug-Misc](https://github.com/lokka30/LevelledMobs/wiki/Documentation---Debug-Misc)中查看。

`file-version:`代表的是配置文件的版本，如果你不知道你在做什么请不要更改该数值，否则有可能会损坏你的插件和配置文件。
