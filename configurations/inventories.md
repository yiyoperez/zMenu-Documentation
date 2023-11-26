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

Allows you to define the time in seconds for the refresh of the buttons in the inventory. For the buttons to be updated you must have the update option enabled. More information [here](https://zmenu.groupez.dev/configurations/buttons).

***

### Clear Inventory

```yaml
clearInventory: <true/false>
```

Allows you to delete the player's inventory on opening and restore it on closing. Allows for example to use an image on your inventory without being hindered by the players' items.

***

### Items

```yaml
items: <buttons>
```

List of buttons, all information [here](https://zmenu.groupez.dev/configurations/buttons).

***

### Open Requirement

More information [here](buttons/requirements.md#open-requirement).
