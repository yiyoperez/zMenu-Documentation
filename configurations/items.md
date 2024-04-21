# Items

Prima che cominci a configurare l'itemstack del plugin assicurati di utilizzare il materiale corretto per la tua versione del gioco.

Ogni pulsante deve essere accompagnato da un itemstack (tranne in alcuni casi specifici).
```yaml
item:
  material: <material>
  amount: <amount>
  data: <data, only avaible between 1.8 and 1.12>
  durability: <durability>
  url: <player skin in base64>
  name: <display name>
  lore: <list of text>
  potion: <potion effect type>
  level: <potion level>
  sphash: <potion splash true or false>
  extended: <potion extended true of flase>
  glow: <add glow effect>
  modelID: <custom model id>
  enchants: <list of enchantments>
  flags: <list of itemflag>
  firework: <firework meta>
  banner: <banner color>
  patterns: <banner pattern>
  color: <leather armor color>
```

## Materiale

```yaml
material: <material>
```

Il materiale dell'item. È possibile utilizzare un placeholder per visualizzare un materiale.
> **Supported material values:**
>
> * [Materiali](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) - Esempio: `material: STONE`
> * [Placeholder](https://www.spigotmc.org/resources/placeholderapi.6245/) valore - Esempio: `material: %your_placeholder_material%`
> * GRATUITO - [zHead](https://www.spigotmc.org/resources/zhead-database.115717/) **RACCOMANDATO** (zhd:\<id>) Esempio: `material: zhd:<id>`
> * A PAGAMENTO - [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) (hdb:\<id>) Esempio: `material: hdb:<id>`
> * A PAGAMENTO - [Oraxen](https://www.spigotmc.org/resources/%E2%98%84%EF%B8%8F-oraxen-add-items-blocks-armors-hats-food-furnitures-plants-and-gui-1-18-1-20-1.72448/) (oraxen:\<item name>) Esempio: `material: oraxen:<item name>`
> * A PAGAMENTO - [ItemAdder](https://www.spigotmc.org/resources/%E2%9C%A8itemsadder%E2%AD%90emotes-mobs-items-armors-hud-gui-emojis-blocks-wings-hats-liquids.73355/) (itemsadder:\<item name>) Esempio: `material:` itemsadder`:<item name>`
> * GRATUITO - [SlimeFun](https://github.com/Slimefun/Slimefun4) (slimefun:\<item name>) Esempio: `material:` slimefun`:<item name>`
> * GRATUITO - [Nova](https://github.com/xenondevs/Nova) (nova:\<item/block name>) Esempio: `material: nova:<item/block name>`
> * Base64 (base64:\<item in base64) Ritrova questo valore in base64 con il comando `/zm save <item name> base64`

***

## Amount

```yaml
amount: <amount>
```

La quantità dell'item. Puoi usare un placeholder per un valore dinamico.

***

## Data

```yaml
data: <data, only avaible between 1.8 and 1.12>
```

Il material data, disponibile solo per versioni tra la **1.8** e la **1.12**. Il valore predefinito è 0

***

## Durabilità

```yaml
durability: <durability>
```

La durabilità dell'item, il valore predefinito è 0.

***

## Url

```yaml
url: <player skin in base64>
```

Permette di visualizzare una testa con un URL in base64. Puoi trovare i valori delle teste sul sito [minecraft-head.com](https://minecraft-heads.com/).
Devi prendere il valore in "Value" nella categoria "For Developers":

![minecraft-head.com example of value](../.gitbook/assets/base64.png)

Esempio

```yaml
url: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNjM3YjhhMzk4MzdiYzNkNThmMDljOGM2ZTUzOTYyZDMzZjlmYTBiNjUzOThhNzc5MzUzYWRlMWUxNDcxM2VmZiJ9fX0="
```

***

## Nome

```yaml
name: <display name>
```

Il nome dell'item. Funziona con PlaceholderAPI.

{% hint style="info" %}
Se il tuo server ha Kyori Adventure, puoi usare [MiniMessage](https://docs.adventure.kyori.net/minimessage/format.html).
{% endhint %}

***

## Lore (descrizione)

```yaml
lore:
  - <line1>
  - <line2>
  - <line3>
  - ...
```

La descrizione dell'item. Funziona PlaceholderAPI.

***

## Pozione

```yaml
  potion: <potion effect type>
  level: <potion level, 1 or 2> # 1 by default
  splash: <potion splash true or false>
  extended: <potion extended true of flase>
```

Ti permette di creare una pozione. Controlla l'effetto della pozione [qui](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionType.html).

{% hint style="danger" %}
Attenzione, la durate della pozione non può essere allungata e il livello massimo è 2
{% endhint %}

{% hint style="info" %}
```yml
# For potions in 1.8 up to 1.12 you have to do like this:
material: POTION
durability: 16454
```
{% endhint %}

***

## Luminosità

```yaml
glow: <true of false>
```

Permette all'item di brillare. Aggiunge un incantesimo casuale e il flag HIDE\_ENCHANT.

***

## ModelID

```yaml
modelID: <custom model id>
```

Ti permette di aggiungere la Custom Model Data all'item

***

## Incantesimi

```yaml
enchants:
  - <enchantment name>,<enchantment level>
```

Ti permette di aggiungere incantesimi, devi inserire il nome dell'incantesimo quindi il livello dell'incantesimo, in questo modo: `ENCHANT,ENCHANT_LEVEL` Elenco degli incantesimi disponibili: [https://hub.spigotmc.org/javadocs/spigot/ org/bukkit/enchantments/Enchantment.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html)
***

## Flags

```yaml
flags:
  - <flag 1>
  - <flag 2>
  - ...
```

Lista delle flags: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)

***

## Colore

```yaml
type: LEATHER_CHESTPLATE
color: 40,150,40 # RGB color

# Example with ARGB
color: 1,40,150,40 # ARGB color, Alpha, RED, GREEN, BLUE
```

Seleziona il colore RGB (Red, Green, Blue) per le armature in pelle. Formato:

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;red>,&#x3C;green>,&#x3C;blue>
</strong></code></pre>

Puoi anche aggiungere un colore alpha per avere il formato ARGB

<pre class="language-yaml"><code class="lang-yaml"><strong>color: &#x3C;alpha>,&#x3C;red>,&#x3C;green>,blue>
</strong></code></pre>

{% hint style="info" %}
The color format is the same for fireworks, banner and potion. \
Javadocs for Color [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Color.html#fromARGB\(int,int,int,int\)).
{% endhint %}

***

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

Tipi di Firework: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html)

***

## Banner

```yaml
type: BANNER
banner: PINK # Banner color
patterns: # Banner pattern: <color>:<pattern>
  - RED:SQUARE_BOTTOM_LEFT
  - GREEN:STRIPE_LEFT
```

Ti permette di creare un banner. Lista degli schemi: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/banner/PatternType.html)

