---
description: How to create a button
---

# Create Button

The code for this example can be found here: [https://github.com/Maxlego08/zMenuExample/tree/master](https://github.com/Maxlego08/zMenuExample/tree/master)

If you need a more concrete example you can look at the zShop source: [https://github.com/Maxlego08/zShop/tree/master](https://github.com/Maxlego08/zShop/tree/master)

## Button

This documentation guides you through creating a `SpecialButton` for use in your plugin, utilizing the `SpecialButton.java` class to implement custom click actions. This example is the typical case of a very simple button.

### Overview

`SpecialButton` extends `ZButton` from the `fr.maxlego08.menu` API to customize the button's behavior on click events. It's designed to close the player's inventory interface, send a custom message, and apply a "jump" or "boost" effect to the player's velocity.

### Prerequisites

Ensure you have the `fr.maxlego08.menu` API included in your project to use `ZButton` and other required classes.

### Implementation Steps

#### Step 1: Define the SpecialButton Class

Create a class named `SpecialButton` that extends `ZButton`. This class will override the `onClick` method to define the button's behavior.

```java
public class SpecialButton extends ZButton {
    // Method implementation
}
```

#### Step 2: Override the onClick Method

In the `SpecialButton` class, override the `onClick` method to specify the actions that occur when the button is clicked. This includes closing the player's inventory, sending a custom message, and applying a velocity change to simulate a jump.

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot, Placeholders placeholders) {
    // Custom actions here
}
```

Step 3: Implement Custom Actions

Within the `onClick` method, add the logic for the custom actions:

1. **Close the Inventory Interface:** Use `player.closeInventory()` to close the inventory interface.
2. **Send a Custom Message to the Player:** Use `player.sendMessage("§fWhoosshh")` to send a custom message.
3. **Modify the Player's Velocity:**
   * Retrieve the current velocity: `Vector vector = player.getVelocity()`.
   * Modify the velocity to add an upward motion: `vector.add(new Vector(0, 2, 0))`.
   * Apply the new velocity: `player.setVelocity(vector)`.

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot, Placeholders placeholders) {
    player.closeInventory(); // Close the player's current inventory
    player.sendMessage("§fWhoosshh"); // Send a custom message to the player

    Vector vector = player.getVelocity(); // Get the current velocity of the player
    vector.add(new Vector(0, 2, 0)); // Modify the Y-axis to make the player "jump"
    player.setVelocity(vector); // Apply the new velocity to the player
}
```

#### Step 4: Regitser the SpecialButton

To register the `SpecialButton` in your plugin, instantiate it and add it to your inventory layout where needed. Ensure that the inventory system you're using supports custom button actions.

```java
public class MyPlugin extends JavaPlugin {
    @Override
    public void onEnable() {
        // Plugin startup logic
        // Assume buttonManager is your instance of a class managing buttons
        buttonManager.register(new NoneLoader(this, SpecialButton.class, "zmenuexample_special"));
    }
}

```

This method allows to save a button very quickly without having to create a new loader. You must specify the plugin from where the plugin comes from, the button class and the name. For the name of the button it is advisable to prefix the name of your plugin.

### Result

```java
package fr.maxlego08.example;

import fr.maxlego08.menu.api.utils.Placeholders;
import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;
import org.bukkit.entity.Player;
import org.bukkit.event.inventory.InventoryClickEvent;
import org.bukkit.util.Vector;

import org.bukkit.entity.Player;
import org.bukkit.event.inventory.InventoryClickEvent;
import org.bukkit.util.Vector;
import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;

/**
 * SpecialButton extends ZButton to implement a custom click action.
 */
public class SpecialButton extends ZButton {

    /**
     * Handles the click event on this special button.
     *
     * @param player The player who clicked the button.
     * @param event The inventory click event details.
     * @param inventory The inventory where the click occurred.
     * @param slot The slot number where the click happened.
     * @param placeholders Placeholders for dynamic text replacement, not used in this method.
     */
    @Override
    public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot, Placeholders placeholders) {
        // Close the inventory interface for the player.
        player.closeInventory();

        // Send a message to the player.
        player.sendMessage("§fWhoosshh");

        // Get the current velocity of the player.
        Vector vector = player.getVelocity();

        // Add to the player's current velocity to make them move upwards.
        // Here, 'new Vector(0, 2, 0)' adds no motion on the X and Z axes, but adds upward motion on the Y axis.
        vector.add(new Vector(0, 2, 0));

        // Apply the new velocity to the player, effectively causing a "jump" or "boost" effect.
        player.setVelocity(vector);

        // Call the superclass method if necessary. This call might be redundant if the superclass does not implement further action.
        super.onClick(player, event, inventory, slot, placeholders);
    }
}
```

## Paginate Button

This documentation outlines how to implement a `ExamplePaginateButton` for creating a paginated inventory interface in your plugin, using the provided `ExamplePaginateButton.java` class as a basis.

### Overview

`ExamplePaginateButton` leverages the `PaginateButton` interface from the `fr.maxlego08.menu.api` to offer pagination functionality, allowing items to be displayed across multiple inventory pages.

### Prerequisites

* Include the `fr.maxlego08.menu` API in your project.
* Understand basic concepts of inventory manipulation in Bukkit/Spigot plugins.

### Implementation Steps

#### Step 1: Extend ZButton and Implement PaginateButton

Your `ExamplePaginateButton` should extend `ZButton` and implement `PaginateButton`, enabling special render behavior and pagination:

```java
public class ExamplePaginateButton extends ZButton implements PaginateButton {
    private final ExamplePlugin plugin;
    
    public ExamplePaginateButton(Plugin plugin) {
        this.plugin = (ExamplePlugin) plugin;
    }
}
```

We use `Plugin` instead of `ExamplePlugin` because the `NoneLoader` class, which is responsible for button registration, requires a constructor parameter of the plugin. Since `NoneLoader` is designed to work with the general `Plugin` interface from Spigot, it ensures compatibility with any Spigot plugin. Casting to the specific `ExamplePlugin` class is then performed to access its unique functionalities. This approach maintains flexibility and adherence to Spigot's plugin architecture.

Step 2: Override `hasSpecialRender`

Indicate that your button uses custom rendering logic for pagination:

```java
@Override
public boolean hasSpecialRender() {
    return true;
}
```

#### Step 3: Implement Custom Rendering Logic

Override the `onRender` method to define how items are displayed based on the current page:

```java
@Override
public void onRender(Player player, InventoryDefault inventory) {
    Pagination<ItemStack> pagination = new Pagination<>();
    List<ItemStack> itemStacks = pagination.paginate(this.plugin.getItemStacks(), this.slots.size(), inventory.getPage());
    // Loop and add items to the inventory
}
```

#### Step 4: Define Pagination Size

Implement `getPaginationSize` to specify the total number of items for pagination. This directly influences the number of pages within the inventory, allowing for dynamic list management. Changes in the list size will automatically adjust the pagination, making this method a key component in handling variable amounts of data efficiently in the inventory UI.

```java
@Override
public int getPaginationSize(Player player) {
    return this.plugin.getItemStacks().size();
}
```

#### Step 5: Regitser the SpecialButton

To register the `ExamplePaginateButton` in your plugin, instantiate it and add it to your inventory layout where needed. Ensure that the inventory system you're using supports custom button actions.

```java
public class MyPlugin extends JavaPlugin {
    @Override
    public void onEnable() {
        // Plugin startup logic
        // Assume buttonManager is your instance of a class managing buttons
        buttonManager.register(new NoneLoader(plugin, ExamplePaginateButton.class, "zmenuexample_pagination"));
    }
}

```

This method allows to save a button very quickly without having to create a new loader. You must specify the plugin from where the plugin comes from, the button class and the name. For the name of the button it is advisable to prefix the name of your plugin.

### Result

```java
package fr.maxlego08.example;

import fr.maxlego08.menu.api.button.PaginateButton;
import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;
import fr.maxlego08.menu.zcore.utils.inventory.Pagination;
import org.bukkit.entity.Player;
import org.bukkit.inventory.ItemStack;
import org.bukkit.plugin.Plugin;

import java.util.List;

/**
 * ExamplePaginateButton extends ZButton and implements PaginateButton to provide
 * pagination functionality for a custom inventory within a zMenu.
 */
public class ExamplePaginateButton extends ZButton implements PaginateButton {

    // Reference to the main plugin instance for accessing its functionalities.
    private final ExamplePlugin plugin;

    /**
     * Constructor that casts the generic Plugin type to the specific ExamplePlugin type.
     * @param plugin The plugin instance, passed in as a generic Plugin type.
     */
    public ExamplePaginateButton(Plugin plugin) {
        this.plugin = (ExamplePlugin) plugin;
    }

    /**
     * Indicates that this button has a special render behavior, enabling pagination.
     * @return true to signify that custom rendering logic is used.
     */
    @Override
    public boolean hasSpecialRender() {
        return true;
    }

    /**
     * Custom rendering method for paginated items. It populates the inventory with items
     * based on the current page and available slots.
     * @param player The player viewing the inventory.
     * @param inventory The inventory being rendered.
     */
    @Override
    public void onRender(Player player, InventoryDefault inventory) {
        // Utilize Pagination utility to split itemStacks into pages.
        Pagination<ItemStack> pagination = new Pagination<>();

        // Get paginated list of ItemStacks for the current page.
        List<ItemStack> itemStacks = pagination.paginate(this.plugin.getItemStacks(), this.slots.size(), inventory.getPage());

        // Loop through the paginated items and add them to the inventory.
        for (int i = 0; i != Math.min(itemStacks.size(), this.slots.size()); i++) {
            int slot = slots.get(i); // Get the slot number.
            ItemStack itemStack = itemStacks.get(i); // Get the ItemStack.
            // Add the item to the inventory at the specified slot and set a click listener.
            inventory.addItem(slot, itemStack).setClick(event -> player.sendMessage("§fClick !"));
        }
    }

    /**
     * Determines the total size of pagination based on the total number of items.
     * @param player The player for whom the pagination size is calculated.
     * @return The total number of items to paginate.
     */
    @Override
    public int getPaginationSize(Player player) {
        // Return the total size of itemStacks to determine how many pages are needed.
        return this.plugin.getItemStacks().size();
    }
}

```

## Custom Button Loader

You can create your own button loader if your button needs more settings. Just create a class that will implement ButtonLoader. All you have to do is implement the methods, here is an example from zShop.

```java
package fr.maxlego08.zshop.loader;

import fr.maxlego08.menu.api.button.Button;
import fr.maxlego08.menu.api.button.DefaultButtonValue;
import fr.maxlego08.menu.api.loader.ButtonLoader;
import fr.maxlego08.zshop.ShopPlugin;
import fr.maxlego08.zshop.api.buttons.AddButton;
import fr.maxlego08.zshop.buttons.ZAddButton;
import org.bukkit.configuration.file.YamlConfiguration;
import org.bukkit.plugin.Plugin;

public class AddButtonLoader implements ButtonLoader {

    private final ShopPlugin plugin;

    public AddButtonLoader(ShopPlugin plugin) {
        this.plugin = plugin;
    }

    @Override
    public Class<? extends Button> getButton() {
        return AddButton.class;
    }

    @Override
    public String getName() {
        return "zshop_add";
    }

    @Override
    public Plugin getPlugin() {
        return this.plugin;
    }

    @Override
    public Button load(YamlConfiguration configuration, String path, DefaultButtonValue defaultButtonValue) {

        String amount = configuration.getString(path + "amount", "1");

        return new ZAddButton(this.plugin, amount);
    }
}

```



