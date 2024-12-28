```
此页面最后更新于3.10.0 b752版本
```

***

⚠

**在3.2.0b 511及以后版本的“生物等级”插件中，WorldGuard Flags被移除了!**

**因此我们在配置文件中添加了`allowed-worldguard-regions`配置选项**

**在未来的插件版本更新中，会删除这个选项**

***

以下所有你可以在你的WorldGuard区域中使用的WorldGuard Flags。以下功能需安装WorldGuard予以实现。注释：WorldGuard 并不是 “生物等级” 使用的必要插件或前置插件。

## `LM-AllowLevelledMobs`
允许在特定区域内生成的怪物拥有等级。

使用是`ALLOW`或者否`DENY`来确定是否开启此功能。

默认设置是开启`ALLOW`。

## `LM-UseCustomLevels`
是否开启在特定区域生成生物等级的限制。**(往下看)**

使用是`ALLOW`或者否`DENY`来确定是否开启此功能。

默认设置是关闭`DENY`。

## `LM-CustomMinLevel`
设置在特定区域生物生成的最低等级。

请使用正整数。

默认设置是`-1`，`-1`表示禁用此项功能。

## `LM-CustomMaxLevel`
设置在特定区域生物生成的最高等级。


请使用正整数。

默认设置是`-1`，`-1`表示禁用此项功能。