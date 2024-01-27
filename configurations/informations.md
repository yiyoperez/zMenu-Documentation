---
description: Toutes les informations pour configurer le plugin
---

# Informations

### Liens

Avant de commencer à configurer le plugin, veuillez vérifier que vous utilisez le nom du matériau pour votre version.

\-> Nous vous invitons à vérifier les noms des documents à l’aide des liens suivants :

* [1.8.8](https://helpch.at/docs/1.8.8/org/bukkit/Material.html)
* [1.12.2](https://helpch.at/docs/1.12.2/org/bukkit/Material.html)
* [1.13.2](https://helpch.at/docs/1.13.2/org/bukkit/Material.html)
* [1.14.4](https://helpch.at/docs/1.14.4/org/bukkit/Material.html)
* [Dernière](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) (1.20)

\-> Pour la configuration des sons, vous devez utiliser les valeurs de [XSound](https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java).

\-> [Enchanments](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)

\-> [Potions](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html)

\-> [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html)

\-> [Minecraft-heads](https://minecraft-heads.com/) (Minecraft head vous permettra d’obtenir la valeur base64 pour afficher une tête)

\-> Pour les couleurs, vous pouvez utiliser le code de minecraft avec un `&<code>`. Pour les versions supérieures à 1.16, vous pouvez utiliser les [couleurs hexadécimal](https://www.google.com/search?q=hex+color) comme ceci`#<color>` (`#ff55ff` par exemple).

{% hint style="info" %}
Si votre serveur dispose de Kyori Adventure (Paper, Purpur, PurfferFish, etc), vous pouvez utiliser le [mini message format](https://docs.adventure.kyori.net/minimessage/format.html).
{% endhint %}

### Informations

Le plugin fonctionnera différemment des autres plugins de menu. Ici, nous avons un système "Button" qui permettra d’effectuer certaines actions. Ce système permet aux autres développeurs d’ajouter facilement des fonctionnalités aux configurations du plugin. Nous verrons ensemble quels sont les différents types de boutons par défaut et leurs éléments de configuration.&#x20;

Mais voyons d’abord la structure d’un fichier d’inventaire.
