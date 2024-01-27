# Fast Events

Dans la configuration par défaut, les FastEvents sont activés par défaut. Au lieu d'utiliser l'API bukkit pour les événements, vous pouvez enregistrer une interface nommée FastEvent avec des méthodes pour chaque événement du plugin. Ou vous pouvez désactiver cette option dans config.json et utiliser les événements bukkit normalement.



## Register FastEvent

```java
inventoryManager.registerFastEvent(plugin, youFastEventClass)
```

Example:

```java
import fr.maxlego08.menu.api.InventoryManager;
import fr.maxlego08.menu.api.event.FastEvent;
import fr.maxlego08.menu.api.event.events.ButtonLoadEvent;
import fr.maxlego08.menu.api.event.events.InventoryLoadEvent;
import fr.maxlego08.menu.api.event.events.PlayerOpenInventoryEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class ExampleEvent extends FastEvent {

    @Override
    public void onButtonLoad(ButtonLoadEvent event) {

    }

    @Override
    public void onInventoryLoad(InventoryLoadEvent event) {

    }

    @Override
    public void onPlayerOpenInventory(PlayerOpenInventoryEvent event) {

    }
}
```

```java
import fr.maxlego08.menu.api.InventoryManager;
import org.bukkit.plugin.java.JavaPlugin;

public class ExamplePlugin extends JavaPlugin {

    @Override
    public void onEnable() {
        InventoryManager inventoryManager = getServer().getServicesManager().getRegistration(InventoryManager.class).getProvider();
        inventoryManager.registerFastEvent(this, new ExampleEvent());
    }
}
```
