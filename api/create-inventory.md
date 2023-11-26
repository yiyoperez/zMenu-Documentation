# Create inventory

## Informations

With zMenu you will be able to use the inventory system for your plugins. So your users will have only one inventory system to know for many plugins. You can load an inventory simply or with a specific implementation.

## Inventory

### Load inventory

To load an inventory you must use the [InventoryManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html) provider. You must then use the [loadInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#loadInventory\(org.bukkit.plugin.Plugin,java.io.File\)) method. Before you start saving your inventories, it is recommended to delete all inventories from your plugin with the method [deleteInventories](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#deleteInventories\(org.bukkit.plugin.Plugin\)).

```java
@Override
public void onEnable() {
    ButtonManager buttonManager = this.getProvider(ButtonManager.class);
    
    // Allows to save the default configuration if it does not exist.
    File fileComplexe = new File(this.getDataFolder(), "complex_actions.yml");
    if (!fileComplexe.exists()) {
        this.saveResource("complex_actions.yml", false);
    }
    
    inventoryManager.deleteInventories(this);
    inventoryManager.loadInventory(this, fileComplexe);
}
```

### Load custom inventory&#x20;

Here is the next example for the button complex. You can create an inventory that will be extended from [ZInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/ZInventory.html).

```java
package fr.zmenu.example;

import java.util.List;
import java.util.Optional;
import org.bukkit.entity.Player;
import org.bukkit.inventory.ItemStack;
import org.bukkit.plugin.Plugin;
import fr.maxlego08.menu.ZInventory;
import fr.maxlego08.menu.api.button.Button;
import fr.zmenu.example.button.pagination.PaginationButton;

public class PaginationInventory extends ZInventory {

	private final ExamplePlugin plugin;

	public PaginationInventory(Plugin plugin, String name, String fileName, int size, List<Button> buttons) {
		super(plugin, name, fileName, size, buttons);
		this.plugin = (ExamplePlugin) plugin;
	}

	@Override
	public int getMaxPage(Player player, Object... objects) {

		int maxPage = super.getMaxPage(player, objects);
		int currentMaxPage = 1;

		Optional<PaginationButton> optional = this.getButtons(PaginationButton.class).stream().findFirst();
		if (optional.isPresent()) {
			PaginationButton button = optional.get();
			
			// List of elements that will be displayed
			List<ItemStack> elements = this.plugin.getItemstacks();
			
			int elementSize = elements.size();
			if (elementSize >= 1) {
				int size = button.getSlots().size();
				return ((elementSize / (size)) + (elementSize == (size) ? 0 : 1));
			}
		}

		return Math.max(maxPage, currentMaxPage);
	}

}
```

For an inventory with pagination you have to define the number of pages that your inventory will have. Here we will retrieve the button of type [PaginationButton](create-button.md#create-a-complexe-button), we will then retrieve the elements that will be displayed, you just have to apply the calculation as in the example.

All you have to do is register the button along with the inventory.

```java
@Override
public void onEnable() {
    ButtonManager buttonManager = this.getProvider(ButtonManager.class);
    
    // Allows to save the default configuration if it does not exist.
    File filePagination = new File(this.getDataFolder(), "examples/paginate_inventory.yml");
    if (!filePagination.exists()) {
	this.saveResource("examples/paginate_inventory.yml", false);
    }
    
    inventoryManager.deleteInventories(this);
    inventoryManager.loadInventory(this, filePagination, PaginationInventory.class);
}
```

### Open Inventory

Now that you have saved your inventory, you can open it. You have many methods [openInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#openInventory\(org.bukkit.entity.Player,fr.maxlego08.menu.api.Inventory\)) to open the inventory, so you have the choice to open an inventory. The simplest method is this one: [openInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#openInventory\(org.bukkit.entity.Player,org.bukkit.plugin.Plugin,java.lang.String\))(player, plugin, inventoryName)
