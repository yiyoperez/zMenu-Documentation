---
description: How to create a button
---

# Create button

## Informations

One of the great features of zMenu is its button customization. You will be able to create buttons for your plugins, which will allow users to have only one inventory plugin for the whole server. The goal of zMenu is to make as many plugins as possible use its API, so that users have only one type of inventory configuration for their entire server.

To create a button you will need at least two classes. A first one for the button and a second one to change the button. You can also create an interface to implement your button, but this is not mandatory.

The final code is available here: [https://github.com/Maxlego08/zMenuExample](https://github.com/Maxlego08/zMenuExample)

## Button&#x20;

The mandatory implementation for a button will be [ZPlaceholderButton](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/button/ZPlaceholderButton.html). You then have the choice to implement your buttons with one of the types available [here](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/button/buttons/package-summary.html). If your plugin has an API you can create an interface and implement it as a [PlaceholderButton](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/PlaceholderButton.html), but it is not mandatory.



Here is the heirarchy of buttons: [PlaceholderButton](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/PlaceholderButton.html) extend [PermissibleButton](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/PermissibleButton.html) who extend [Button](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html).

If you have a question don't hesitate to ask on [discord](https://discord.groupez.dev/).

### Creating a classic button

We will create a simple button with an action that will be performed when clicked.

#### 1. Create button class

First you need to create a class that will be extended from `ZButton`:

```java
public class SpecialButton extends ZButton{
}
```

You have just created a button, you just have to implement the methods and register it.

#### 2. Implementation

For the example we will make sure that when the player clicks, the inventory will be closed, a message will be sent to him and he will be sent into the sky.

To detect the click of a player you have to implement the [onClick](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html#onClick\(org.bukkit.entity.Player,org.bukkit.event.inventory.InventoryClickEvent,fr.maxlego08.menu.inventory.inventories.InventoryDefault,int\)) method.

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot) {
}
```

In this method we have the player, the click event and the InventoryDefault object. This object allows to manage all the actions of the inventory. It will allow you to retrieve information about the page, about the Inventory object of spigot and many other things.

We can now implement this method:

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot) {

	player.closeInventory();
	player.sendMessage("§fWhoosshh §5" + this.plugin.getItemstacks().size());
	
	Vector vector = player.getVelocity();
	vector.add(new Vector(0, 2, 0));
	player.setVelocity(vector);

}
```

You can see that in this example we refer to this.plugin. It is important to know that the constructor of your Button can have an empty constructor or a constructor with the [Plugin](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/plugin/Plugin.html) interface. You can then cast the plugin interface into your plugin. (Cf #3 Register button)

Here is the class with all the implementations:

```java
package fr.zmenu.example.button.special;

import org.bukkit.entity.Player;
import org.bukkit.event.inventory.InventoryClickEvent;
import org.bukkit.plugin.Plugin;
import org.bukkit.util.Vector;

import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;
import fr.zmenu.example.ExamplePlugin;

public class SpecialButton extends ZButton {

	private final ExamplePlugin plugin;

	public SpecialButton(Plugin plugin) {
		super();
		this.plugin = (ExamplePlugin) plugin;
	}

	@Override
	public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot) {

		player.closeInventory();
		player.sendMessage("§fWhoosshh §5" + this.plugin.getItemstacks().size());
		
		Vector vector = player.getVelocity();
		vector.add(new Vector(0, 2, 0));
		player.setVelocity(vector);

	}

}
```

#### 3. Register button

Now you have to register the button. To register a button you need a [ButtonLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html). In this example we don't need a complex loader. So we can use the [NoneLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/button/loader/NoneLoader.html). This loader will allow you to load a button very simply. As said in the second part, the [NoneLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/button/loader/NoneLoader.html) will allow you to load your class with or without the [Plugin](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/plugin/Plugin.html).

Go to your main class. You will need to get the [ButtonManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html) provider and use the register method to [register](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html#register\(fr.maxlego08.menu.api.loader.ButtonLoader\)) a button.

To recover the provider here is a very useful method:

```java
private <T> T getProvider(Class<T> classz) {
    RegisteredServiceProvider<T> provider = getServer().getServicesManager().getRegistration(classz);
    return provider == null ? null : provider.getProvider() != null ? (T) provider.getProvider() : null;
}
```

You just have to use the methods to register a button. It is advised before registering your buttons to remove all buttons from your plugin with the [unregisters](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html#unregister\(fr.maxlego08.menu.api.loader.ButtonLoader\)) method.

```java
@Override
public void onEnable() {
    ButtonManager buttonManager = this.getProvider(ButtonManager.class);
    buttonManager.unregisters(this);
    buttonManager.register(new NoneLoader(this, SpecialButton.class, "ZMENUEXAMPLE_SPECIAL"));
}
```

With the NoneLoader you have to specify the name of your button. We advise you to put the `<name of your plugin>_<the name of the button>`

### Create a complexe button

#### 1. Create button class

We are going to create a button to do pagination. The button will display items on several slots depending on the page. So we have to create a button that will be extended from `ZButton`. We will also create a PaginationButton interface which will be extended from [SlotButton](file:///D:/Users/Maxence/Desktop/docs/fr/maxlego08/menu/api/button/buttons/SlotButton.html).

```java
public interface PaginationButton extends ZButton {
}
```

```java
public class ZPaginationButton extends ZButton implements PaginationButton {
}
```

#### 2. Implementation

zMenu uses the TemplatePlugin. So the plugin has many utility classes. Here we will use the [Pagination](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/zcore/utils/inventory/Pagination.html) class. This class will allow to sort a list according to a number of elements and a page.

Here is the complete class:

```java
package fr.zmenu.example.button.pagination;

import java.util.ArrayList;
import java.util.List;

import org.bukkit.entity.Player;
import org.bukkit.inventory.ItemStack;

import fr.maxlego08.menu.button.ZButton;
import fr.maxlego08.menu.inventory.inventories.InventoryDefault;
import fr.maxlego08.menu.zcore.utils.inventory.Pagination;
import fr.zmenu.example.ExamplePlugin;

public class ZPaginationButton extends ZButton implements PaginationButton {

	private final ExamplePlugin plugin;

	/**
	 * @param slots
	 * @param plugin
	 */
	public ZPaginationButton(List<Integer> slots, ExamplePlugin plugin) {
		super.slots = slots
		this.plugin = plugin;
	}

	@Override
	public void onRender(Player player, InventoryDefault inventory) {

		Pagination<ItemStack> pagination = new Pagination<>();
		List<Integer> slots = new ArrayList<Integer>(this.getSlots());
		List<ItemStack> itemStacks = pagination.paginate(this.plugin.getItemstacks(), slots.size(),
				inventory.getPage());

		for (int i = 0; i != Math.min(itemStacks.size(), slots.size()); i++) {

			int slot = slots.get(i);
			ItemStack itemStack = itemStacks.get(i);
			inventory.addItem(slot, itemStack).setClick(event -> {
				player.sendMessage("§fClick !");
			});
		}
	}
}
```

An inventory that will be extended from slotButton will have a special render with the [onRender](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html#onRender\(org.bukkit.entity.Player,fr.maxlego08.menu.inventory.inventories.InventoryDefault\)) method. You can activate the special rendering with the method [hasSpecialRender](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html#hasSpecialRender\(\)).

#### 3. Register button

To register this button we will have to create a [ButtonLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html).

```java
public class PaginationLoader implements ButtonLoader {
}
```

You must then implement the 4 methods. The method [getButton](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html#getButton\(\)) you have to return the button, here you have to return the PaginationButton.class

```java
package fr.zmenu.example.button.pagination;

import java.util.List;
import org.bukkit.configuration.file.YamlConfiguration;
import org.bukkit.plugin.Plugin;
import fr.maxlego08.menu.api.button.Button;
import fr.maxlego08.menu.api.loader.ButtonLoader;
import fr.zmenu.example.ExamplePlugin;

public class PaginationLoader implements ButtonLoader {

	private final ExamplePlugin plugin;

	/**
	 * @param plugin
	 */
	public PaginationLoader(ExamplePlugin plugin) {
		super();
		this.plugin = plugin;
	}

	@Override
	public Class<? extends Button> getButton() {
		return PaginationButton.class;
	}

	@Override
	public String getName() {
		return "ZMENUEXAMPLE_PAGINATION";
	}

	@Override
	public Plugin getPlugin() {
		return this.plugin;
	}

	@Override
	public Button load(YamlConfiguration configuration, String path, DefaultButtonValue defaultButtonValue) {
		List<Integer> slots = ButtonLoader.loadSlot(configuration.getStringList(path + "slots"));
		return new ZPaginationButton(slots, this.plugin);
	}
}
```

We advise you to put the `<name of your plugin>_<the name of the button>`

For the [load](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html#load\(org.bukkit.configuration.file.YamlConfiguration,java.lang.String\)) method the plugin will provide you with a YamlConfiguration and the path into the configuration. Then you have to return the implementation of your button. To be able to load a list of slot you have the method [loadeSlot](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html#loadSlot\(java.util.List\)) which from a list of string will return a list of interger.

Then, as in the first example, you must save the button.

```java
buttonManager.register(new PaginationLoader(this));
```

4\. Inventory

Now you have to create an inventory to be able to manage the pagination.
