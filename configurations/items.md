# Items

Avant de commencer à configurer l'ItemStack du plugin, assurez-vous que vous utilisez le bon matériel pour votre version du jeu. Chaque bouton doit être accompagné d'un ItemStack (sauf dans certains cas spécifiques).

```yaml
item:
  material: <material>
  amount: <nombre>
  data: <données disponibles uniquement entre 1.8 et 1.12>
  durability: <la durabilité>
  url: <skin du joueur en base64>
  name: <nom de l'item>
  lore: <liste de textes>
  potion: <type d'effet de potion>
  level: <niveau de potion>
  sphash: <potion splash vrai ou faux>
  extended: <potion étendue vrai de flase>
  glow: <ajouter un effet de brillance>
  modelID: <identifiant du modèle personnalisé>
  enchants: <liste des enchantements>
  flags: <liste des itemsflag>
  firework: <feu d'artifice méta>
  banner: <couleur de la bannière>
  patterns: <modèle de bannière>
  color: <couleur de l'armure en cuir>
```

## Material

```yaml
material: <material>
```

Le matériau de l'article. Vous pouvez utiliser un placeholder pour afficher un matériau.

> **Valeurs matérielles prises en charge :**
>
> * [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) - Example: `material: STONE`
> * [Placeholder](https://www.spigotmc.org/resources/placeholderapi.6245/) value - Example: `material: %your_placeholder_material%`
> * [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) (hdb:\<ID>) Example: `material: hdb:<ID>`
> * [Oraxen](https://www.spigotmc.org/resources/%E2%98%84%EF%B8%8F-oraxen-add-items-blocks-armors-hats-food-furnitures-plants-and-gui-1-18-1-20-1.72448/) (oraxen:\<item name>) Example: `material: oraxen:<item name>`
> * [ItemAdder](https://www.spigotmc.org/resources/%E2%9C%A8itemsadder%E2%AD%90emotes-mobs-items-armors-hud-gui-emojis-blocks-wings-hats-liquids.73355/) (itemsadder:\<item name>) Example: `material:` itemsadder`:<item name>`
> * [SlimeFun](https://github.com/Slimefun/Slimefun4) (slimefun:\<item name>) Example: `material:` slimefun`:<item name>`
> * [Nova](https://github.com/xenondevs/Nova) (nova:\<item/block name>) Example: `material: nova:<item/block name>`
> * Base64 (base64:\<item in base64) Retrieve this value in base64 with the command `/zm save <item name> base64`

***

## Amount

```yaml
amount: <amount>
```

Le montant de la pile d'objets. Vous pouvez utiliser un espace réservé pour obtenir un montant dynamique.

## Data

```yaml
data: <données disponibles uniquement entre 1.8 et 1.12>
```

Les données matérielles, disponibles uniquement pour les versions entre 1.8 et 1.12. Par défaut, la valeur est de 0

## Durability

```yaml
durability: <durability>
```

La durabilité de l'objet, qui est de 0 par défaut.

## Url

```yaml
url: <skin du joueur en base64>
```

Permet d'afficher un head avec une url en base64. Vous pouvez trouver les valeurs des heads sur le site [minecraft-head.com](https://minecraft-heads.com/).

Vous devez prendre le contenu de la rubrique "Value" de la catégorie "Other" :

![minecraft-head.com example of value](../.gitbook/assets/base64.png)

Exemple

```yaml
url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNjM3YjhhMzk4MzdiYzNkNThmMDljOGM2ZTUzOTYyZDMzZjlmYTBiNjUzOThhNzc5MzUzYWRlMWUxNDcxM2VmZiJ9fX0="
```

## Name

```yaml
name: <nom de l'item>
```

Le nom qui sera affiché sur l'élément. Fonctionne avec PlaceholderAPI.

{% hint style="info" %}
Si votre serveur dispose de Kyori Adventure, vous pouvez utiliser l'option [mini message format](https://docs.adventure.kyori.net/minimessage/format.html).
{% endhint %}

## Lore

```yaml
lore:
  - <line1>
  - <line2>
  - <line3>
  - ...
```

Permet d'afficher l'histoire de l'objet. Fonctionne avec PlaceholderAPI.

## Potion

```yaml
  potion: <potion effect type>
  level: <potion level, 1 ou 2> # 1 par défaut
  splash: <potion splash vrai ou faux>
  extended: <potion étendue vrai de flase>
```

Permet de créer une potion. Vérifier le type d'effet de la potion [ici](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionType.html).

{% hint style="danger" %}
Attention, une potion ne peut pas être étendu et avec un niveau 2
{% endhint %}

{% hint style="info" %}
```yaml
# Pour les potions de 1.8 à 1.12, vous devez procéder comme ceci:
material: POTION
durability: 16454
```
{% endhint %}

## Glow

```yaml
glow: <true ou false>
```

Permet à l'objet de briller. Ajout d'un enchantement aléatoire et d'un indicateur d'objet HIDE\_ENCHANT.

## ModelID

```yaml
modelID: <custom model id>
```

Permet d'ajouter un identifiant de modèle personnalisé à l'article.

## Enchantments

```yaml
enchants:
  - <nom de l'enchantement>,<niveau d'enchantement>
```

Permet d'ajouter des enchantements, il faut mettre le nom de l'enchantement puis le niveau de l'enchantement, comme ceci : `ENCHANT,ENCHANT_LEVEL` Liste des enchantements disponibles : [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)

## Flags

```yaml
flags:
  - <flag 1>
  - <flag 2>
  - ...
```

Liste des ItemFlags : [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)

## Color

```yaml
type: LEATHER_CHESTPLATE
color: 40,150,40 # Couleur RVB

# Exemple avec ARGB
color: 1,40,150,40 # Couleur ARGB, Alpha, ROUGE, VERT, BLEU
```

Définir la couleur RVB (rouge, vert, bleu) pour les armuriers en cuir. Le format est le suivant :

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;rouge>,&#x3C;vert>,&#x3C;bleu>
</strong></code></pre>

Vous pouvez également ajouter un alpha à la couleur pour obtenir une couleur ARGB.

```yaml
couleur : <alpha>,<rouge>,<vert>,bleu>
```

{% hint style="info" %}
Le format des couleurs est le même pour les feux d'artifice, les bannières et les potions. Javadocs pour Couleur [ici](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Color.html#fromARGB\(int,int,int,int\)).
{% endhint %}

## Firework

```yaml
type: FIREWORK
firework:
  star: true
  flicker: true
  trail: true
  type: BALL_LARGE
  colors:
    - 250,10,10 # RGB and ARGB
  fadeColors:
    - 250,10,250 # RGB and ARGB
```

Firework type: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html)

## Banner

```yaml
type: BANNER
banner: PINK # Banner color
patterns: # Banner pattern: <color>:<pattern>
  - RED:SQUARE_BOTTOM_LEFT
  - GREEN:STRIPE_LEFT
```

Permet de créer une bannière. Liste des motifs : [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html)

