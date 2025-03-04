---
description: All the information to configure the plugin
---

# ℹ️ Informations

### Links

Before you start configuring the plugin, please ensure that you are using the correct material names for your version.

👉 We invite you to check the material names using the following links:

* [1.8.8](https://helpch.at/docs/1.8.8/org/bukkit/Material.html)
* [1.12.2](https://helpch.at/docs/1.12.2/org/bukkit/Material.html)
* [1.13.2](https://helpch.at/docs/1.13.2/org/bukkit/Material.html)
* [1.14.4](https://helpch.at/docs/1.14.4/org/bukkit/Material.html)
* [Latest](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) (1.21)

\-> For the configuration of the sounds you must use the values of [XSound](https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java).

\-> [Enchanments](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)

\-> [Potions](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html)

\-> [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html)

\-> [Minecraft-heads](https://minecraft-heads.com/) (Minecraft head will allow you to get the base64 value to display a head)

\-> For colors, you can use Minecraft color codes with `&<code>`. For versions higher than 1.16, you can use hexadecimal colors, like this: `#<color>` (for example, `#ff55ff`).

{% hint style="info" %}
If your server has Kyori Adventure (with Paper or any Paper fork), you can use the [Mini message format](https://docs.adventure.kyori.net/minimessage/format.html).
{% endhint %}

### Informations

The plugin operates differently from other menu plugins. Here, we have a `Button` system that allows you to perform various actions. This system also enables other developers to easily add features to the plugin's configurations.

We will explore the different types of default buttons and their configuration elements. But first, let's take a look at the structure of an inventory file.
