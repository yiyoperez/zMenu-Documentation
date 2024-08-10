---
description: All the information to configure the plugin
---

# ℹ️ Informations

### Links

Before you start configuring the plugin, please check that you are using the material name for your version.&#x20;

\-> We invite you to check the names of the materials with the following links:

* [1.8.8](https://helpch.at/docs/1.8.8/org/bukkit/Material.html)
* [1.12.2](https://helpch.at/docs/1.12.2/org/bukkit/Material.html)
* [1.13.2](https://helpch.at/docs/1.13.2/org/bukkit/Material.html)
* [1.14.4](https://helpch.at/docs/1.14.4/org/bukkit/Material.html)
* [Latest](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) (1.20)

\-> For the configuration of the sounds you must use the values of [XSound](https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java).

\-> [Enchanments](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)

\-> [Potions](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html)

\-> [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html)

\-> [Minecraft-heads](https://minecraft-heads.com/) (Minecraft head will allow you to get the base64 value to display a head)

\-> For the colors you can use the code of minecraft with a `&<code>`. For versions higher than 1.16 you can use [hexadecimal colors](https://www.google.com/search?q=hex+color) like this `#<color>` (`#ff55ff` for example).

{% hint style="info" %}
If your server has Kyori Adventure, you can use the [mini message format](https://docs.adventure.kyori.net/minimessage/format.html).
{% endhint %}

### Informations

The plugin will work differently from other menu plugins. Here we have a "Button" system that will allow to perform some action. This system allows other developers to easily add features to the plugin configurations. We will see together what are the different types of default buttons and their configuration elements.

But first let's see the structure of an inventory file.
