# Fast Events

In the default configuration, you have FastEvents enabled by default. Instead of using the bukkit API for events, you can save an interface named FastEvent with methods for each plugin event. Or you can disable this option in config.json and use bukkit events normally.



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
