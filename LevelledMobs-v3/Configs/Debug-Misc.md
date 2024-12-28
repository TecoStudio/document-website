```
本页信息最后更新为“生物等级”插件的3.13.0 b793版本。
```

---

```yml
debug-misc: [""]
```

以下列表中的名称都是可以添加到`settings.yml`文件中的`debug-misc:`选项中来作为调试模式的选择对象。

你可以同时添加多个调试对象，只需要使用英文的逗号“`,`”隔开即可。

> ### 禁止等级<br />
>
> 与实体等级铭牌的有关选项。

- `APPLY_LEVEL_FAIL` - 当“生物等级”插件未给予实体等级时的报告。
- `ENTITY_TRANSFORM_FAIL` - 实体已经转化了但是未满足某个等级要求的报告。
- `SCOREBOARD_TAGS` - 因计分板规则不符合标准而被拒绝的报告。
- `SKYLIGHT_LEVEL` - 报告由于光照登记不符合标准而被拒绝的登记。
- `DENIED_FORCE_BLOCKED_ENTITY_TYPE` - 当“生物等级”因生物的硬编码问题而无法给予等级时。
- `DENIED_RULE_ENTITIES_LIST` - 当实体列表被拒绝给予等级时。
- `DENIED_RULE_MINLEVEL` - 当实体未达到给予等级的要求被拒绝时。
- `DENIED_RULE_MAXLEVEL` - 当等级数值超过最大值而被拒绝时。
- `DENIED_RULE_WORLD_LIST` - 当实体在被禁止生成时维度列表中而被拒绝时。
- `DENIED_RULE_BIOME_LIST` - 当实体在被禁止生成时生物群系列表中而被拒绝时。
- `DENIED_RULE_PLUGIN_COMPAT` - 当实体因为被指定插件拒绝给予等级时。
- `DENIED_RULE_SPAWN_REASON` - 当`allowed-spawn-reason:`被特定因素而被拒绝给予等级时。
- `DENIED_RULE_CUSTOM_NAME` - 当由于`自定义名称`与配置等级数值不一致而被拒绝时。
- `DENIED_RULE_CHANCE` - 当随机概率配置被等级拒绝时。
- `DENIED_RULE_WG_REGION` - 当由于`WorldGuard`插件的区域规则被拒绝生成时。
- `DENIED_RULE_WG_REGION_OWNER` - 当由于`WorldGuard`插件的区域所有者规则被拒绝生成。
- `DENIED_RULE_MYTHIC_MOBS_INTERNAL_NAME` - 当因 MM 插件实体名称被拒绝生成等级时。
- `DENIED_RULE_RULE_Y_LEVEL` - 当由于实体坐标高或于配置的指定 Y 轴坐标而被拒绝生成等级时。
- `DENIED_LEVEL_0` - 当实体的`maxLevel: 0`设置为 0 而被拒绝时。
- `DENIED_RULE_MIN_SPAWN_DISTANCE` - 当实体因太靠近出生点而被拒绝生成等级时。
- `DENIED_RULE_MAX_SPAWN_DISTANCE` - 当实体因距离出生点太远而被拒绝生成等级时。
- `DENIED_RULE_RULE_STOP_PROCESSING` - 当实体因`stop-processing:`配置选项而被拒绝生成等级时。
- `DENIED_RULE_SPAWNER_NAME` - 当实体因刷怪笼名称不符合标准而被拒绝生成时。
- `DENIED_RULE_WORLD_TIME_TICK` - 当实体因时间 tick 不符合标准而被拒绝生成时。
- `DENIED_RULE_PERMISSION` - 当实体因玩家权限等级不符合标准而被拒绝生成时。
- `DENIED_RULE_WITH_COORDINATES` - 当实体因`within-coordinates:`被拒绝在特定位置上生成等级时。

> ### 预处理<br />
>
> 当等级给予生物之前的流程事项。

- `ENTITY_SPAWN` - 报告生物在生成后被给予等级的时间。

> ### 规则流程<br />
>
> 连接到规则系统中的监听器有关的流程配置选项。

- `APPLY_LEVEL_SUCCESS` - 报告生物等级成功给予生物时的时间。
- `MOB_SPAWNER` - 报告从刷怪笼方块中升级的实体。
- `ENTITY_MISC` - 报告幼体完全长成并允许升级时间。
- `PLAYER_LEVELLING` - 显示与`玩家等级`（如果启用）策略有关的调试信息。
- `ATTRIBUTE_MULTIPLIERS` - 显示与属性乘法倍率有关的调试信息。
- `NBT_APPLY_SUCCESS` - 在 NBT 数据成功应用到已分级实体时报告。
- `RULE_COOLDOWN` - 报告规则由于满足冷却所需条件而被禁用。
- `MULTIPLIER_REMOVED` - 显示在多久之后从实体身上移除`vanilla-bonus:`。

> ### 后处理<br />
>
> 当实体被设置等级时进程相关的选项。

- `ENTITY_TAME` - 显示已驯服实体的等级。
- `RANGED_DAMAGE_MODIFICATION` - 报告已产生伤害的炮弹调整之后的远程伤害输出。
- `MOB_HASH` - 当实体具有无效的或者已丢失的 hash key 并重新评估后报告。

> ### 关于死亡流程<br />
>
> 当设置等级的生物实体死亡时进程相关的选项。

- `CUSTOM_DROPS` - 当生物等级`自定义掉落`被处理的时间。
- `CUSTOM_EQUIPS` - 当一个 `CustomDrop` 可以在生成时完成装备的时候报告。
- `MOB_GROUPS` - 报告死亡实体所述的怪物团体。
- `GROUP_LIMITS` - 报告与 `CustomDrops` `group-limits:` 设置相关的变量。
- `CUSTOM_COMMANDS` - 当来自 `CustomDrop` 系统的 `CustomCommand`被处理时候的报告。
- `SET_LEVELLED_ITEM_DROPS` - 显示生物等级调整实体物品掉落的信息。
- `SET_LEVELLED_XP_DROPS` - 显示生物等级调整实体经验值掉落的信息。
- `CHUNK_KILL_COUNT` - 当一个区块满足禁用掉落物的最大条件时报告。

> ### 开发者选项<br />
>
> 仅限开发者使用。

- `THREAD_LOCKS` - 显示与内部线程锁有关的调试信息。
