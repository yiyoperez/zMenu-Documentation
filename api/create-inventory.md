# Create inventory

## Informations

Avec zMenu vous pourrez utiliser le système d'inventaire pour vos plugins. Ainsi vos utilisateurs n'auront qu'un seul système d'inventaire à connaître pour plusieurs plugins. Vous pouvez charger un inventaire simplement ou avec une implémentation spécifique.

## Inventory

### Chargement de l'inventaire

Pour charger un inventaire, vous devez utiliser la fonction [InventoryManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html). Vous devez ensuite utiliser la méthode loadInventory. Avant de commencer à enregistrer vos inventaires, il est recommandé de supprimer tous les inventaires de votre plugin avec la méthode [deleteInventories](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#deleteInventories\(org.bukkit.plugin.Plugin\)).

```java
@Override
public void onEnable() {
    ButtonManager buttonManager = this.getProvider(ButtonManager.class);
    
    // Permet d'enregistrer la configuration par défaut si elle n'existe pas.
    File fileComplexe = new File(this.getDataFolder(), "complex_actions.yml");
    if (!fileComplexe.exists()) {
        this.saveResource("complex_actions.yml", false);
    }
    
    inventoryManager.deleteInventories(this);
    inventoryManager.loadInventory(this, fileComplexe);
}
```

### Chargement de l'inventaire personnalisé&#x20;

Voici l'exemple suivant pour le bouton complexe. Vous pouvez créer un inventaire qui sera étendu à partir de [ZInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/ZInventory.html).

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

Pour un inventaire avec pagination, vous devez définir le nombre de pages que votre inventaire aura. Ici, nous allons récupérer le bouton de type [PaginationButton](create-button.md#create-a-complexe-button), nous récupérons alors les éléments qui seront affichés, il vous suffit d'appliquer le calcul comme dans l'exemple.&#x20;

Il ne vous reste plus qu'à enregistrer le bouton ainsi que l'inventaire.

```java
@Override
public void onEnable() {
    ButtonManager buttonManager = this.getProvider(ButtonManager.class);
    
    // Permet d'enregistrer la configuration par défaut si elle n'existe pas.
    File filePagination = new File(this.getDataFolder(), "examples/paginate_inventory.yml");
    if (!filePagination.exists()) {
	this.saveResource("examples/paginate_inventory.yml", false);
    }
    
    inventoryManager.deleteInventories(this);
    inventoryManager.loadInventory(this, filePagination, PaginationInventory.class);
}
```

### Open Inventory

Maintenant que vous avez enregistré votre inventaire, vous pouvez l'ouvrir. Vous disposez de plusieurs méthodes [openInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#openInventory\(org.bukkit.entity.Player,fr.maxlego08.menu.api.Inventory\)) pour ouvrir l'inventaire, vous avez donc le choix d'ouvrir un inventaire. La méthode la plus simple est celle-ci : [openInventory](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html#openInventory\(org.bukkit.entity.Player,org.bukkit.plugin.Plugin,java.lang.String\))(player, plugin, inventoryName)
