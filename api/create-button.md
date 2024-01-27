---
description: How to create a button
---

# Create button

## Informations

L'une des grandes caractéristiques de zMenu est la personnalisation des boutons. Vous pourrez créer des boutons pour vos plugins, ce qui permettra aux utilisateurs de n'avoir qu'un seul plugin d'inventaire pour l'ensemble du serveur. L'objectif de zMenu est de faire en sorte que le plus grand nombre possible de plugins utilisent son API, afin que les utilisateurs n'aient qu'un seul type de configuration d'inventaire pour l'ensemble de leur serveur.

Pour créer un bouton, vous aurez besoin d'au moins deux classes. Une première pour le bouton et une seconde pour le modifier. Vous pouvez également créer une interface pour implémenter votre bouton, mais ce n'est pas obligatoire.

Le code final est disponible ici : [https://github.com/Maxlego08/zMenuExample](https://github.com/Maxlego08/zMenuExample)

## Création d'un bouton classique

Nous allons créer un simple bouton avec une action qui sera exécutée lorsqu'il sera cliqué.

#### 1. Créer une classe de boutons

Il faut d'abord créer une classe qui sera étendue à partir de `ZButton` :

```java
public class SpecialButton extends ZButton {
}
```

Vous venez de créer un bouton, il ne vous reste plus qu'à implémenter les méthodes et à l'enregistrer.

#### 2. Implementation

Pour l'exemple, nous ferons en sorte que lorsque le joueur clique, l'inventaire se ferme, un message lui est envoyé et il est envoyé dans le ciel.

Pour détecter le clic d'un joueur, vous devez implémenter la méthode [onClick](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html#onClick\(org.bukkit.entity.Player,org.bukkit.event.inventory.InventoryClickEvent,fr.maxlego08.menu.inventory.inventories.InventoryDefault,int\)).

```java
@Override
public void onClick(Player player, InventoryClickEvent event, InventoryDefault inventory, int slot) {
}
```

Dans cette méthode, nous avons le lecteur, l'événement click et l'objet InventoryDefault. Cet objet permet de gérer toutes les actions de l'inventaire. Il vous permettra de récupérer des informations sur la page, sur l'objet Inventory du spigot et bien d'autres choses.&#x20;

Nous pouvons maintenant implémenter cette méthode :

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

Vous pouvez voir que dans cet exemple, nous faisons référence à this.plugin. Il est important de savoir que le constructeur de votre bouton peut avoir un constructeur vide ou un constructeur avec l'attribut [Plugin](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/plugin/Plugin.html). Vous pouvez ensuite intégrer l'interface du plugin dans votre plugin. (Cf #3 Register button)

Voici la classe avec toutes les implémentations :

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

#### 3. Bouton d'enregistrement

Vous devez maintenant enregistrer le bouton. Pour enregistrer un bouton, vous avez besoin d'un [ButtonLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html). Dans cet exemple, nous n'avons pas besoin d'un chargeur complexe. Nous pouvons donc utiliser la fonction [NoneLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/button/loader/NoneLoader.html). Ce loader vous permettra de charger un bouton très simplement. Comme nous l'avons dit dans la deuxième partie, la fonction [NoneLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/button/loader/NoneLoader.html) vous permettra de charger votre classe avec ou sans l'élément [Plugin](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/plugin/Plugin.html).

Allez dans votre classe principale. Vous devrez obtenir le fichier [ButtonManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html) et utiliser la méthode d'enregistrement pour [register](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html#register\(fr.maxlego08.menu.api.loader.ButtonLoader\)) un bouton.

Pour récupérer le fournisseur, voici une méthode très utile :

```java
private <T> T getProvider(Class<T> classz) {
    RegisteredServiceProvider<T> provider = getServer().getServicesManager().getRegistration(classz);
    return provider == null ? null : provider.getProvider() != null ? (T) provider.getProvider() : null;
}
```

Il suffit d'utiliser les méthodes pour enregistrer un bouton. Avant d'enregistrer vos boutons, il est conseillé de supprimer tous les boutons de votre plugin à l'aide de la méthode [unregisters](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html#unregister\(fr.maxlego08.menu.api.loader.ButtonLoader\)).

```java
@Override
public void onEnable() {
    ButtonManager buttonManager = this.getProvider(ButtonManager.class);
    buttonManager.unregisters(this);
    buttonManager.register(new NoneLoader(this, SpecialButton.class, "ZMENUEXAMPLE_SPECIAL"));
}
```

Avec le NoneLoader, vous devez spécifier le nom de votre bouton. Nous vous conseillons de mettre le `<nom de votre plugin>_<le nom du bouton>`

## Créer un bouton complexe

#### 1. Créer une classe de boutons

Nous allons créer un bouton pour faire de la pagination. Le bouton affichera les éléments sur plusieurs emplacements en fonction de la page. Nous devons donc créer un bouton qui sera étendu à partir de ZButton. Nous allons également créer une interface PaginationButton qui sera étendue à partir de [SlotButton](file:///D:/Users/Maxence/Desktop/docs/fr/maxlego08/menu/api/button/buttons/SlotButton.html).

```java
public interface PaginationButton extends ZButton {
}
```

```java
public class ZPaginationButton extends ZButton implements PaginationButton {
}
```

#### 2. Implementation

zMenu utilise le TemplatePlugin. Ce plugin possède donc de nombreuses classes utilitaires. Ici, nous utiliserons la classe [Pagination](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/zcore/utils/inventory/Pagination.html). Cette classe permet de trier une liste en fonction d'un nombre d'éléments et d'une page.

Voici la classe complète :

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

Un inventaire qui sera étendu à partir de slotButton aura un rendu spécial avec la méthode [onRender](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html#onRender\(org.bukkit.entity.Player,fr.maxlego08.menu.inventory.inventories.InventoryDefault\)). Vous pouvez activer le rendu spécial à l'aide de la méthode [hasSpecialRender](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/button/Button.html#hasSpecialRender\(\)).

#### 3. Bouton d'enregistrement

Pour enregistrer ce bouton, nous devons créer une class [ButtonLoader](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html).

```java
public class PaginationLoader implements ButtonLoader {
}
```

Vous devez ensuite mettre en œuvre les 4 méthodes. La méthode [getButton](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html#getButton\(\)) vous devez retourner le bouton, ici vous devez retourner le PaginationButton.class

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

Nous vous conseillons de mettre le `<nom de votre plugin>_<le nom du bouton>`

Pour la méthode [load](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html#load\(org.bukkit.configuration.file.YamlConfiguration,java.lang.String\)) le plugin vous fournira une YamlConfiguration et le chemin d'accès à la configuration. Vous devez ensuite renvoyer l'implémentation de votre bouton. Pour pouvoir charger une liste de slots, vous disposez de la méthode [loadeSlot](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/loader/ButtonLoader.html#loadSlot\(java.util.List\)) qui, à partir d'une liste de chaînes de caractères, renvoie une liste d'entiers.

Ensuite, comme dans le premier exemple, vous devez enregistrer le bouton.

```java
buttonManager.register(new PaginationLoader(this));
```

4\. Inventory

Vous devez maintenant créer un inventaire pour pouvoir gérer la pagination.
