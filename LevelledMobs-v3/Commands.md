```
本页信息最后更新为“生物等级”插件的3.2.0 b520版本。
```

***

# 👉 命令

以下指令适用于服务器管理员，可让管理员更轻松地管理插件和世界中现有的生物等级属性。

***

如果想要更加深入的了解权限的说明，请查看本 wiki 的权限页面。

* `/levelledmobs`
  * 本插件最基础的指令，在不选择任何参数时会在聊天栏显示一个当前可使用的权限列表。
  * 需要权限：`levelledmobs.command`

# /levelledmobs rules
  * `force_all`                - 强制让所有生物重新评级
  * `help_discord`             - 显示加入 Arcane 插件的 Discord 连接
  * `help_wiki`                - 显示 wiki 的链接
  * `reset <easy/normal/hard>` - 使用预设的难度重置 rules.yml 文件
  * `show_all`                 - 显示 rules.yml 文件中的所有规则
  * `show_effective`           - 显示适合最近生物的现有规则
  * `show_rule <name>`         - 显示指定规则

# /levelledmobs spawner
* `/levelledmobs spawner create`
  * 给予物品栏一个刷怪笼，只会在特定最小和最大区域内生成的生物。如果没有在以下参数中指定刷怪笼的刷怪生物类型，那么你需要对着刷怪笼使用刷怪蛋才能让刷怪笼正常运行。
  * 参数，使用下列列表中的组合，大多数参数都是可选的：
    * `/minlevel <数量>`           - 设置生物在刷怪笼中生成时的最低等级
    * `/maxlevel <数量>`           - 设置生物在刷怪笼中生成时的最高等级
    * `/name <名称>`                 - 设置刷怪笼的特定自定义名称
    * `/lore <描述>`                 - 设置描述，可以使用`\n`符号转行
    * `/nolore`                      - 删除默认的描述
    * `/customdropid <id>`           - 使用 customdrops.yml 文件内的 droptableid 参数修改该刷怪笼中生成生物的掉落物
    * `/spawntype <类型>`            - 设置刷怪笼生成的生物类型
    * `/delay <数量>`               - 设置刷怪笼生成生物的冷却时间
    * `/maxnearbyentities <数量>`   - 设置刷怪笼在生成该生物时的最大生物数量上限
    * `/minspawndelay <数量>`       - 设置下一次生成冷却时间的最小随机冷却时间值，单位：Tick
    * `/maxspawndelay <数量>`       - 设置下一次生成冷却时间的最大随机冷却时间值，单位：Tick
    * `/requiredplayerrange <数量>` - 设置刷怪笼在刷新生物时需要和玩家的距离
    * `/spawncount <数量>`          - 设置刷怪笼每次生成生物的数量
    * `/spawnrange <数量>`          - 设置刷怪笼的生成范围
    * `/giveplayer <玩家名称>`          - 给予刷怪笼到指定玩家的物品栏中

* `/levelledmobs spawner info` - 可对“生物等级”插件的刷怪笼右键获取更多信息
    * 使用时不添加参数可显示是否启用
    * `on`  - 启用刷怪笼的信息模式
    * `off` - 关闭刷怪笼的信息模式

* `/levelledmobs spawner copy` - 可对“生物等级”插件的刷怪笼右键获来复制该刷怪笼
    * 使用时不添加参数可显示是否启用
    * `on`  - 启用刷怪笼的复制模式
    * `off` - 关闭刷怪笼的复制模式

# /levelledmobs eggs
  * 参数，其中 minlevel、maxlevel 和 spawntype 是必填项，其他是可选的。
    * `/minlevel <数量>`           - 设置生物在刷怪蛋中生成时的最低等级
    
      `/maxlevel <数量>`           - 设置生物在刷怪蛋中生成时的最高等级
    
    * `/name <名称>`                 - 设置刷怪蛋的特定自定义名称
    
    * `/lore <描述>`                 - 设置描述，可以使用`\n`符号转行
    
    * `/nolore`                      - 删除默认的描述
    
    * `/customdropid <id>`           - 使用 customdrops.yml 文件内的 droptableid 参数修改该刷怪笼中生成生物的掉落物
    
    * `/spawntype <类型>`            - 设置刷怪蛋生成的生物类型
    
    * `/giveplayer <玩家名称>`          - 给予刷怪蛋到指定玩家的物品栏中

# /levelledmobs summon
  * 类似原版的`/summon`指令，使用该指令可以生成指定等级的生物，例如：你可以在玩家**Notch**的位置上生成一只**1级**的僵尸，或者在头顶5格的位置上生成生物。
  * 需要权限：`levelledmobs.command`和`levelledmobs.command.summon`
  * 用途：
    * `/levelledmobs summon <数量> <实体> <等级> here`
    * `/levelledmobs summon <数量> <实体> <等级> atPlayer <玩家名称>`
    * `/levelledmobs summon <数量> <实体> <等级> atLocation <x> <y> <z> [world]`

# /levelledmobs kill
  * 与Essentials插件的`/killall`指令类似，只不过该指令只是杀死附近或者指定维度中具有等级的生物。
  * 需要权限：`levelledmobs.command`和`levelledmobs.command.kill`，如果和以下子指令搭配可以实现额外的功能。
  * 使用：
    * `/levelledmobs kill all [world/*]`
      * 杀死发送指令时所处维度中具有等级的生物，如果参数修改成了`*`的话则会杀死服务器上所有维度里拥有等级的生物。
      * 需要额外权限：`levelledmobs.command.kill.all`
    * `/levelledmobs kill near <radius>`
      * 杀死发送指令时附近一定范围内具有等级的生物
      * 需要额外权限：`levelledmobs.command.kill.near`

# /levelledmobs reload
  * 和其他插件里的 `reload` 指令类似，只是从服务端重新读取和引用配置文件而不需要重启服务器。
  * 需要权限：`levelledmobs.command` 和 `levelledmobs.command.reload`

# /levelledmobs debug
  * 启用“生物等级”插件的调试模式，在以后你可以通过使用指令来开启或者关闭调试模式，而不仅仅通过修改 `settings.yml` 文件。
  * 请务必多查看“生物等级”插件的更新内容！

# /levelledmobs info
  * 打印目前所有已安装的插件版本信息，例如插件名称、插件版本、插件作者、插件描述、支持的原版版本以及对该插件具有非常大贡献的玩家的信息。

# /levelledmobs compatibility
  * 检查兼容性，检查服务器是否缺少重要功能或者运行了不支持的配置文件。
  * 需要权限：`levelledmobs.command`和`levelledmobs.command.compatibility`