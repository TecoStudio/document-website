```
本页信息最后更新为“生物等级”插件的3.10.1版本。
```

---

在本界面中你可以找到本插件是否与你的服务器兼容的相关信息。

> **注意：**“支持”的意思是本插件的作者是否愿意去解决你遇到的问题。

> **注意：**“兼容性”的意思是与本插件同时加载时不会使其他插件缺少内容或者丢失内容。

# 我的世界版本

**在下列表格中未出现的版本说明与其是不支持或者不兼容的。**

> 注意：不想升级我的世界版本？那么你会流失大量的玩家，缺少漏洞补丁修复、新功能、性能优化、插件的兼容、社区的支持等内容。 ;)

> **警告：** 本插件的`v4.0.0`版本属于未来的版本，需要升到更高的我的世界版本才能运行。

<table width="100%">
    <tr>
        <th>MC版本</th>
        <th>兼容性</th>
        <th>支持</th>
        <th>最低Java版本</th>
        <th>备注</th>
    </tr>
    <tr>
        <td>1.18.x, 1.19.x, 1.20.x</td>
        <td>🟢</td>
        <td>🟢</td>
        <td>17</td>
        <td></td>
    </tr>
    <tr>
        <td>1.17.x</td>
        <td>🟢</td>
        <td>🟢</td>
        <td>17</td>
        <td>
            如果你为安装Paper端，或者其分支衍生等，那么你也需要安装<a href="https://www.spigotmc.org/resources/protocollib.1997/">ProtocolLib</a>插件。
        </td>
    </tr>
    <tr>
        <td>1.16.x</td>
        <td>🟢</td>
        <td>🟢</td>
        <td>17</td>
        <td>
            在此版本里，你也需要安装<a href="https://www.spigotmc.org/resources/protocollib.1997/">ProtocolLib</a>插件。
            <br/>
            如果你的Paper端由于Java版本问题而无法启动，请尝试添加<code>-DPaper.IgnoreJavaVersion=true</code>。
            <br />
            <i>我们的工作人员无法为你解决此类Java问题。</i>
        </td>
    </tr>
</table>

# 服务端类型

**在下方列表中未出现的服务端类型是不支持的，但也未必兼容。**

<table width="100%">
    <tr>
        <th>服务器类型</th>
        <th>兼容性</th>
        <th>支持</th>
        <th>备注</th>
    </tr>
    <tr>
        <td>Paper</td>
        <td>🟢</td>
        <td>🟢</td>
        <td>非常实用，强烈推荐。</td>
    </tr>
    <tr>
        <td>Purpur</td>
        <td>🟢</td>
        <td>🟢</td>
        <td></td>
    </tr>
    <tr>
        <td>Spigot</td>
        <td>🟡</td>
        <td>🟢</td>
        <td>
            有一定的兼容性限制，但是在本插件中的一些功能需要<a href="https://papermc.io/">Paper</a>端类型或者其分支衍生作品。
        </td>
    </tr>
</table>

### 不要使用混合类型的服务器类型！

> **注意：** 混合类型指的是服务器既可以运行 Bukkit 端的插件，也可以加载 Forge 和 Fabric 加载器的模组。

Mohist、Arclight、Cauldron、Magma 等等服务器类型<b>都没有</b>获得来自本插件的工作人员支持。

<details>
<summary>为什么？..</summary>

**因为 Bukkit 的 API 都不是为了适配模组而诞生的**，[所有黑客使用的方法](https://essentialsx.net/do-not-use-mohist.html)都是为了绕过该问题，很多内容已经遭到了破坏，这对于插件的开发者来说都是很难追查的。在我们遇到的一些服务器的错误里，大多数的错误都是来自此类混合服务器中。

本插件不是唯一拒绝为混合类服务器提供插件的人，甚至连[EssentialsX](https://essentialsx.net/do-not-use-mohist.html)也谴责过...

</details>

# Java 版本

如果你使用的是`1.16`或者`1.17`版本，那么你需要安装`Java 17`来运行本插件。

> **注意：** 本插件无法帮助你解决与 Java 有关的安装问题，因为在互联网上拥有大量且免费的此类教程。

# 插件版本

我们只为使用本插件`最新版本`或者`开发版本`的玩家提供帮助。

如果你使用的是旧版本，那么你不仅会错过许多功能或者增加游戏体验的内容，例如：漏洞补丁修复、性能升级等，同时也不会获得本插件的开发人员支持。

<details>
<summary>但是我不想更新插件！</summary>

如果有什么问题阻碍了你更新到最新版本，请务必告诉我们开发人员，我们可以为你解决。如果你的问题是无效的或者自己很容易解决的，请别联系我们开发人员。 :)

</details>

# <u>不兼容</u>的插件

<b><u>这并不意味着所有的插件都是<i>完全</i>不兼容的，请务必仔细阅读它们的描述。</u></b>

<table>
    <tr>
        <th width="15%">插件</th>
        <th width="15%">严重程度</th>
        <th>描述</th>
    </tr>
    <tr>
        <td>mcMMO</td>
        <td>🟢 轻微</td>
        <td>
            mcMMO有一个生命值系统，你需要禁用它，因为该系统会导致本插件的视觉错误。
        </td>
    </tr>
    <tr>
        <td>模型引擎</td>
        <td>🟡 中等</td>
        <td>
            模型引擎插件会覆盖掉本插件的生物铭牌，所以当生物升级时本插件将无法在生物的顶部渲染等级铭牌，我们无法在本插件中解决该问题。
            </br>
            只不过在我们的社区里设立了一个此类问题的<a href="https://github.com/ArcanePlugins/LevelledMobs/wiki/Compatibility-%7C-LevelledMobs,-ModelEngine,-and-MythicMobs">解决方案</a>。
        </td>
    </tr>
    <tr>
        <td>全息生物生命值插件 <i>（和其他拥有生命值铭牌的插件）</i></td>
        <td>🟡 中等</td>
        <td>
            与mcMMO类似，全息生命值插件会导致本插件的铭牌出现视觉渲染错误，需要在全息生命值插件中禁用该功能或者删除全息生命值插件。
            <br />
            你也许可以使用BOSS的状态栏或者其他类型的生命值栏来代替。
        </td>
    </tr>
    <tr>
        <td>堆叠插件</td>
        <td>🔴 严重</td>
        <td>
            堆叠插件会导致本插件的渲染出现严重错误，除非禁用<b>生物堆叠</b>，否则此类堆叠插件会破坏本插件的名称标签和自定义的掉落系统。
        </td>
    </tr>
    <tr>
        <td>每个世界插件</td>
        <td>🔴 严重</td>
        <td>
            世界类插件破坏了大量的插件，包括本插件。
            <br />
            本插件通过规则获得了与世界插件一样的功能，因此为了本插件而去使用世界插件是没有意义的。
            <br />
            你可以自己在服务器上运行世界插件和本插件，但请不要使用世界插件来管理本插件。
        </td>
    </tr>
</table>

---

# <u>兼容</u>（和集成）插件

### 我们为以下插件提供了一个集成：

- `MythicMobs`
- `InfernalMobs`
- `EliteMobs`
- `Shopkeepers`
- `Citizens`
- `DangerousCaves 2`
- `EcoBosses`
- `SimplePets`

有了这些集成插件的存在，可以在默认情况下使本插件不会让这些集成插件里的生物获得等级属性。

### 为本插件提供集成的插件：

- [`MobHunting`](http://www.spigotmc.org/resources/mobhunting.3582/)：通过击杀更高等级的生物可获得更多的钱。
- [`Money From Mobs`](https://www.spigotmc.org/resources/money-from-mobs-1-12-1-17.79137/)：通过击杀更高等级的生物可获得更多的钱。
