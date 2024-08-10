---
description: All information on inventories.
---

# 👨‍💻 Inventories

## Informations

The plugin has an `inventories` folder that will contain all your inventories. Each inventory will be represented by a file. You can create as many inventories as you want as well as subfolders to sort your inventories.

In the default configuration, you have this:

```
|- inventories
  |- test
    |- test3
      - example3.yml
    - example2.yml
  - example.yml
  - example_shop.yml
  - example_punish.yml
```

***

## Syntax

```yaml
name: "<inventory name>"
size: <inventory size>
fillItem: <itemstack>
updateInterval: <update interval>
clearInventory: <true/false>
items: <buttons>
open_requirement: <requirement>
```

***

### Name

```yaml
name: "<inventory name>"
```

The name of the inventory that will be displayed. Please note that depending on your version you have a character limit. You can use color and placeholders.

If your inventory has multiple pages, you can view the current page and the last page with the following placeholders: \
`%page%` - Current max \
`%maxPage%` - Last page

***

### Size

```yaml
size: <inventory size>
```

Sets the inventory size. By default the value will be `54`. The size of the inventory must be a multiple of `9` between **9** and **54**. So the following values:

* 9
* 18
* 27
* 36
* 45
* 54

***

### Fill Item

```yaml
fillItem: <itemstack>
```

Allows to fill all the slots of the same itemstack. See item information [here](https://zmenu.groupez.dev/configurations/items).

***

### Update Interval

```yaml
updateInterval: <update interval>
```

Allows you to define the time in milliseconds for the refresh of the buttons in the inventory. For the buttons to be updated you must have the update option enabled. More information [here](https://zmenu.groupez.dev/configurations/buttons).

***

### Clear Inventory

```yaml
clearInventory: <true/false>
```

Allows you to delete the player's inventory on opening and restore it on closing. Allows for example to use an image on your inventory without being hindered by the players' items.

***

### Matrix

The matrix configuration in a YAML file allows for intuitive organization of items within a Minecraft inventory by providing a visual representation of slot arrangements. In the given example, a 54-slot inventory named "&8Test" uses a matrix of characters, where 'A' represents slots filled with diamonds, to create a bordered layout. This method enhances clarity and design efficiency, as each character in the matrix corresponds to an item defined under the `items` section, allowing for easy customization of inventory layouts. The use of a matrix simplifies the creation of complex inventory designs by visually mapping out item placements.

```yaml
name: "&8Test"
size: 54
matrix:
  - "AAAAAAAAA"
  - "A       A"
  - "A       A"
  - "A       A"
  - "A       A"
  - "AAAAAAAAA"
items:
  A:
    item:
      material: DIAMOND
```

***

### Items

```yaml
items: <buttons>
```

List of buttons, all information [here](https://zmenu.groupez.dev/configurations/buttons).

***

### OpenWithItem

Opens the inventory with the interaction of an item. You must define the information of the item that will be used, the actions to be performed (full list [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html)) and the type of verification.

```yaml
# Open this menu by clicking a specific item
# You can use /zm giveopenitem <inventory> <player> to retrieve the item to use
#
openWithItem:
  # Define the item that will be clicked
  item:
    material: compass
    name: "&eOpen Basic Inventory"
    lore:
      - "&7Click on me !"
  # Look at https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html
  actions:
    - RIGHT_CLICK_BLOCK
    - RIGHT_CLICK_AIR
  # Define the type of verification.
  # Depending on your configuration and need you will define a certain type of verification. Here are all the types that exist:
  # - full -> Allows to check the itemStack in full, will use the ItemStack#isSimilar method.
  # - material -> Allows to check only the material
  # - name -> Allows to check only the display name
  # - lore -> Allows to check only the lore
  # - modelid -> Allows to check only the Custom Model Id
  type: full
```

***

### Open Requirement

More information [here](buttons/requirements.md#open-requirement).

## Translated Name

Allows you to translate the name of the player’s inventory

```yaml
# Inventory name (https://docs.zmenu.dev/configurations/inventories#name)
#
# This is the title of your inventory. You can put anything in it.
# Color code and placeholders are supported.
# If you are on Paper, Purpur or PufferFish you have access to the color code of MiniMessage (https://docs.advntr.dev/minimessage/format.html)
#
name: "&7Basics Inventory"

# Translate the inventory name into multiple languages
# You must define the language and the country used
# The vanilla Minecraft client will use lowercase language / country pairs separated by an underscore, but custom resource packs may use any format they wish.
translatedName:
  - locale: "fr_fr" # Allows to define the language in French
    name: "&aInventaire Basique"
  - locale: "es_es" # Allows to define the language in Spanish
    name: "&aInventario Básico"
```

## Patterns

After creating your [patterns](patterns.md), you can add them to your inventory this way:

```yaml
size: 54
name: "&4Advanced &cInventory &7%page%&8/&7%maxPage%"
patterns:
  - "pattern_example"
```

You must put the name of your file in the folder patterns. You can add as many patterns as you want.

Example from zAuctionHouseV3:

```yaml
name: '&8ᴀᴜᴄᴛɪᴏɴ &8(&f%page%&8/&f%maxPage%&8)'  # Title of the menu, supports color codes and placeholders

size: 54  # Size of the Minecraft inventory menu, must be a multiple of 9

patterns:  # List of pattern identifiers used in the menu
  - "zauctionhouse_decoration"  # Pattern for decorative elements
  - "zauctionhouse_pagination"  # Pattern for navigation between menu pages
  - "zauctionhouse_auction"  # Pattern related to auction items or functionalities

items:
  displayItems:
    type: ZAUCTIONHOUSE_AUCTION  # Type of items to display, specific to auction house items
    isPermanent: true  # Indicates these items will always be displayed and not dynamically updated
    slots:  # Specifies the slots in the menu for the items
      - 10-16  # Items occupy slots 10 through 16
      - 19-25  # Items occupy slots 19 through 25
      - 28-34  # Items occupy slots 28 through 34
      - 37-43  # Items occupy slots 37 through 43
    else:
      slots:
        - 22
      item:
        material: BARRIER
        name: '&c&nNo Items Found'
```

The auction inventory will use three patterns, one for decoration, one to manage pagination and one to display the main buttons (purchased items, expired items, categories, etc). There is only the button to define the list of items for sale in this inventory. The patterns will allow to reduce the size of the configuration and to be able to use it in several inventories.
