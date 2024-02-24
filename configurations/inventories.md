---
description: All information on inventories.
---

# Inventories

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
