```
此页面最后更新于 3.13.0 b789
```

---

# PAPI 占位符

|           占位符           | 描述                                        |
| :------------------------: | :------------------------------------------ |
| %levelledmobs_mob-target%  | 准星上的等级生物名牌信息(3.3.0 或者 更新版) |
| %levelledmobs_displayname% | 展示玩家最后击杀的等级生物信息              |
|   %levelledmobs_mob-lvl%   | 展示玩家最后击杀的等级生物的等级            |
|  %levelledmobs_killed-by%  | 展示最后击杀等级生物的玩家                  |

# 内置占位符

|           占位符            | 描述                             |
| :-------------------------: | :------------------------------- |
|        %displayname%        | 实体自定义名                     |
|     %health-indicator%      | 血条指示器                       |
|                             |                                  |
|          %mob-lvl%          | 被击杀实体的等级                 |
|        %entity-name%        | 被击杀实体的种类                 |
|       %entity-health%       | 实际被击杀实体的血量             |
|   %entity-health-rounded%   | 被击杀实体的血量（整数）         |
|     %entity-max-health%     | 被击杀实体的最大血量             |
| %entity-max-health-rounded% | 被击杀实体的最大血量（整数）     |
|       %heart_symbol%        | 表示`♥`.                         |
|          %tiered%           | 分层着色器的颜色                 |
|         %wg_region%         | 实体死亡时所在的 WorldGuard 区域 |
|           %world%           | 实体死亡时所在的世界             |
|          %player%           | 杀死实体玩家的名字               |
|        %player-uuid%        | 杀死实体玩家的 UUID              |
|         %location%          | 实体死亡时所在的坐标（x y z）    |

# 内置玩家占位符

|          占位符          | 描述                                                                                    |
| :----------------------: | :-------------------------------------------------------------------------------------- |
|         %level%          | 玩家等级                                                                                |
|          %exp%           | 玩家距离下个等级还差多少百分比                                                          |
|      %exp-to-level%      | 玩家距离下个等级还差多少经验                                                            |
|       %total-exp%        | 玩家总经验                                                                              |
|    %world_time_tick%     | 游戏内时间 Game Tick (0 - 24000)                                                        |
|      %bed_distance%      | 玩家与其床的距离，若在某个玩家床不存在的世界则会定位到进入的传送门                      |
|     %home_distance%      | 玩家与主城或其家（essential）的距离，若玩家在某个其床不存在的世界则会定位到进入的传送门 |
| %home_distance_with_bed% | 次占位符是`%bed_distance%`和`%home_distance%`的结合（会优先使用`%bed_distance%`）       |
