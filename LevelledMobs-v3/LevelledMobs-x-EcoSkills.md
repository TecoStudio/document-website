生物等级允许通过玩家的等级或其他数据，来生成等级化生物
这些数据通过你选择的`PlaceHolder`占位符来获取

## 1. 寻找占位符

当你使用`ecoskills`时，你可以用其`PlaceHolder`的占位符

<https://plugins.auxilor.io/ecoskills/placeholderapi>

## 2. 编写文件

在预设部分之中，找到`player_Levelling`这个类

```yaml
  player_Levelling:
#   This Strategy Preset controls the player-stat based levelling system.
    name: 'LVLling Strategy - Player Based AVERAGE CHALLENGE'
    strategies:
      player-levelling:
        match-level: true
        use-player-max-level: false
        decrease-level: true
        player-level-scale: 1.0
        level-cap: 30
        tiers:
          1-15: 1-10
          16-30: 11-20
          31-45: 21-25
        variable: '%level%'
```

在`variable`部分修改至，你想用的占位符

> 提示：你可以使用`PlaceHolder`的`maths`模块来高效添加多个占位符

你可以按照你的需要，随意修改。 所有`player_levelling`的变量都可以在我们的wiki之中找到：

<https://github.com/lokka30/LevelledMobs/wiki/Documentation---Conditions,-Strategies,-and-Apply-Settings#player-levelling>

最后，我们需要在`default-rule`中启动`player_levelling`

你在`default-rule`中的`use-preset`应该长这样：

```yaml
default-rule:
  use-preset:
    - allowed_worlds
    - nametag_using_numbers
#    - nametag_using_indicator
#    - basic_challenge
    - average_challenge
#    - advanced_challenge
#    - extreme_challenge
#    - apply_LevellingVariance
#    - weighted_random_basic
    - weighted_random_average
#    - weighted_random_advanced
#    - weighted_random_extreme
#    - spawn_Levelling
#    - blended_Levelling
#    - ycoord_Levelling
#    - random_Levelling
#    - player_Levelling
```

需要修改成这样：

```yaml
default-rule:
  use-preset:
    - allowed_worlds
    - nametag_using_numbers
#    - nametag_using_indicator
#    - basic_challenge
    - average_challenge
#    - advanced_challenge
#    - extreme_challenge
#    - apply_LevellingVariance
#    - weighted_random_basic
    - weighted_random_average
#    - weighted_random_advanced
#    - weighted_random_extreme
#    - spawn_Levelling
#    - blended_Levelling
#    - ycoord_Levelling
#    - random_Levelling
    - player_Levelling
```

重点！记得保存你的文件（文件 -> 保存）！

## 3. 重启插件

现在你需要`reload`你的插件，告诉它你修改了文件，并启用`player_levelling`

下述指令，会使已经等级化生物按照`player_levelling`重新获取等级

运行： `/lm rules force_all`

## 完工！

现在所有的实体会按照，你所使用的EcoSkill的数据来获取等级了!
