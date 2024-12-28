```
此页面最终更新于 LevelledMobs 3.1.1 b481
```

---

## 关于

LevelledMobs 的 `messages.yml` 文件允许你自定义从插件发送的所有聊天消息。

## 占位符

LevelledMobs 允许你在你的消息中包含各种不同的占位符。占位符看起来像 `%this%`，并会在消息发送给玩家时被替换。

### 警告

> **大多数占位符仅在某些消息中起作用。**

> 通常，如果消息中默认不包含占位符，则不会在消息中对它进行处理。

> 因此，如果你不确定文件中的一条或多条消息支持哪些占位符，你可能会发现引用默认 messages.yml 文件很有用。

> 例如，你将无法在'无权限'消息中使用占位符 `%supportedVersions%` 。

### 列表:

|         配置行选项          | 描述                                                                                             |
| :-------------------------: | :----------------------------------------------------------------------------------------------- |
|         `%prefix%`          | LevelledMobs 在插件通过发送的任何消息之前使用的前缀。                                            |
|         `%player%`          | 事件指向的玩家的名称。                                                                           |
|          `%label%`          | 运行 LM 命令时使用的主要命令别名。<br />**示例：** `/lm` 或 `/levelledmobs`                      |
|         `%amount%`          | 事件的输入值。                                                                                   |
|       `%entityType%`        | 事件的 `EntityType` 值。                                                                         |
|          `%level%`          | 正在处理的事件中实体的等级。                                                                     |
|       `%summonType%`        | 召唤 `EntityType` 的输入值。                                                                     |
|         `%entity%`          | 正在处理的实体的名牌、`自定义名称` 或默认名称值。                                                |
|      `%x%` `%y%` `%z%`      | 这三个标签报告事件的 **X**、**Y** 和 **Z** 坐标。                                                |
|          `%world%`          | 事件发生的世界名称的值。                                                                         |
|     `%targetUsername%`      | 事件目标的用户名。                                                                               |
|    `%targetDisplayname%`    | 事件目标的显示名称。                                                                             |
|        `%maxAmount%`        | 返回来自 `settings.yml` 的 **_召唤命令限制器_** 的值。                                           |
|  `%minLevel%` `%maxLevel%`  | 返回正在处理的事件中的 `minLevel` 和 `maxLevel` 值。                                             |
|         `%killed%`          | 返回在正在处理的事件中被杀死的实体数量。                                                         |
|         `%skipped%`         | 返回在 LM 杀死事件期间被跳过的实体数量。                                                         |
|         `%radius%`          | 在 LM 的召唤命令中使用的半径的输入值。                                                           |
| `%minRadius%` `%maxRadius%` | 返回最小和最大半径值。                                                                           |
|         `%version%`         | 返回 LM 的当前版本，格式为 `LM X.Y.Z b000`，其中 `X.Y.Z` 代表发布版本，`b000` 代表实际的构建号。 |
|       `%description%`       | 返回内部 LM 描述文本。                                                                           |
|    `%supportedVersions%`    | 返回内部 LM 支持的版本文本。                                                                     |
|      `%contributors%`       | 返回内部 LM 贡献者列表文本。                                                                     |
|    `%incompatibilities%`    | 返回内部 LM 不兼容性文本。                                                                       |
