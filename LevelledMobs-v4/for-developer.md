# ⚙️ For Developers

For assistance, please [visit the support discord](https://discord.gg/arcaneplugins-752310043214479462).

---

Direct Links to Sonatype and the Maven Repositories.

https://central.sonatype.com/artifact/io.github.arcaneplugins/levelledmobs-plugin <br/>
https://mvnrepository.com/artifact/io.github.arcaneplugins/levelledmobs-plugin

:::tabs
==Maven
### Maven
1. Add to the Repository:

```
<repository>
    <id>Central Sonatype</id>
    <url>https://central.sonatype.com/</url>
</repository>
```

2. Add the LevelledMobs dependency:

```
<dependency>
    <groupId>io.github.arcaneplugins</groupId>
    <artifactId>LevelledMobs-plugin</artifactId>
    <version>X.X.X</version>
</dependency>
```

** Make sure to replace `X.X.X` with the lastest version of LevelledMobs, [as referenced here](https://mvnrepository.com/artifact/io.github.arcaneplugins/levelledmobs-plugin).

==Gradle
### Gradle
1. Add the Repository:
```
repositories {
    maven("https://central.sonatype.com/")
}
```
2. Add the LevelledMobs dependency:
```
implementation("io.github.arcaneplugins:levelledmobs-plugin:X.X.X")
```
** Make sure to replace `X.X.X` with the latest version of LevelledMobs, [as referenced here](https://mvnrepository.com/artifact/io.github.arcaneplugins/levelledmobs-plugin)
:::

## Access the LevelledMobs processing
- The [LevelInterface class](https://github.com/ArcanePlugins/LevelledMobs/blob/master/levelledmobs-plugin/src/main/kotlin/io/github/arcaneplugins/levelledmobs/LevelInterface.kt) provides core information;
- [Multiple events](https://github.com/ArcanePlugins/LevelledMobs/tree/master/levelledmobs-plugin/src/main/kotlin/io/github/arcaneplugins/levelledmobs/events) which can be listened to and modified with ease;
- A populated [Javadocs](https://arcaneplugins.github.io/LevelledMobs/) with basic documentation;

## Obtaining the Level of a Mob without using the API

:::tabs
==Java
**Simple solution**
```java
    public int getMobLevel(LivingEntity livingEntity){
        Plugin levelledMobsPlugin = Bukkit.getPluginManager().getPlugin("LevelledMobs");
        if (levelledMobsPlugin == null) return 0;
        NamespacedKey levelKey = new NamespacedKey(levelledMobsPlugin, "level");
        return Objects.requireNonNullElse(
                livingEntity.getPersistentDataContainer().get(levelKey, PersistentDataType.INTEGER),
                0
        );
    }    
```
**Elegant Solution**
```java
public class LevelledMobsManager {
    private final Boolean levelledMobsIsInstalled;
    private NamespacedKey key;

    public LevelledMobsManager(){
        Plugin levelledMobsPlugin = Bukkit.getPluginManager().getPlugin("LevelledMobs");
        levelledMobsIsInstalled = levelledMobsPlugin != null && levelledMobsPlugin.isEnabled();

        if (levelledMobsIsInstalled){
            key = new NamespacedKey(levelledMobsPlugin, "level");
        }
    }

    public boolean hasLevelledMobsInstalled(){
        return levelledMobsIsInstalled != null && levelledMobsIsInstalled;
    }

    public int getLevelledMobsMobLevel(Entity entity){
        if (!hasLevelledMobsInstalled()) return 0;

        Integer mobLevel = entity.getPersistentDataContainer().get(key, PersistentDataType.INTEGER);
        return Objects.requireNonNullElse(mobLevel, 0);
    }
}
```
==Kotlin
**Simplified Solution**
```Kotlin
    fun getMobLevel(livingEntity: LivingEntity) : Int{
        val levelledMobs = Bukkit.getPluginManager().getPlugin("LevelledMobs") ?: return 0
        val levelKey = NamespacedKey(levelledMobs, "level")
        return livingEntity.persistentDataContainer.get(levelKey, PersistentDataType.INTEGER) ?: 0
    }
```
**Elegant Solution**
```Kotlin
class LevelledMobsManager {
    private val levelledMobsIsInstalled: Boolean?
    private var key: NamespacedKey? = null

    init {
        val levelledMobsPlugin = Bukkit.getPluginManager().getPlugin("LevelledMobs")
        levelledMobsIsInstalled = levelledMobsPlugin != null && levelledMobsPlugin.isEnabled

        if (levelledMobsIsInstalled) {
            key = NamespacedKey(levelledMobsPlugin!!, "level")
        }
    }

    fun hasLevelledMobsInstalled(): Boolean {
        return levelledMobsIsInstalled != null && levelledMobsIsInstalled
    }

    fun getLevelledMobsMobLevel(entity: Entity): Int {
        if (!hasLevelledMobsInstalled()) return 0

        return entity.persistentDataContainer.get(key!!, PersistentDataType.INTEGER) ?: 0
    }
}
```
:::

## Integrating into CustomDrops Sample
Below is a sample bit opf coe which uses the CustomDrops system of LevelledMobs via the API
```java
    private void testCustomDrops(){
        ItemStack itemStack = new ItemStack(Material.NETHERITE_SWORD);
        ItemMeta meta = itemStack.getItemMeta();
        assert meta != null;
        meta.setDisplayName("Cool Netherite Sword");
        meta.setLore(List.of("Created via API"));
        itemStack.setItemMeta(meta);

        // https://arcaneplugins.github.io/LevelledMobs/3.9.3/me/lokka30/levelledmobs/LevelledMobs.html
        LevelledMobs lm = LevelledMobs.getInstance();

        // https://arcaneplugins.github.io/LevelledMobs/3.9.3/me/lokka30/levelledmobs/customdrops/CustomDropItem.html
        CustomDropItem customDropItem = new CustomDropItem(lm); // must pass instance to LevelledMobs main class
        customDropItem.setItemStack(itemStack);

        // these options correspond to many of the item specific options shown here:
        // https://github.com/ArcanePlugins/LevelledMobs/wiki/Documentation---customdrops.yml
        customDropItem.chance = 1.0F;
        customDropItem.equippedSpawnChance = 1.0F;

        // https://arcaneplugins.github.io/LevelledMobs/3.9.3/me/lokka30/levelledmobs/customdrops/CustomDropInstance.html
        final CustomDropInstance customDropInstance = new CustomDropInstance(EntityType.ZOMBIE);
        customDropInstance.customItems.add(customDropItem);
        // mob specific options can be set on customDropInstance

        lm.customDropsHandler.externalCustomDrops.addCustomDrop(customDropInstance);
        // the drop is now registered just as if it were in customdrops.yml

        main.getLogger().info("Added a new drop for zombie");
    }
```
