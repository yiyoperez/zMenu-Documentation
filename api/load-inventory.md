---
icon: loader
---

# Load Inventory

To load an inventory you have many methods present in the `InventoryManager` interface. But I advise you to use the `loadInventoryOrSaveResource` method. It allows you to retrieve the file in the resources of your plugin and save it.

```java
try {
    // Attempt to load or save a custom inventory configuration from a YAML file
    this.inventoryManager.loadInventoryOrSaveResource(this.plugin, "inventories/paginate_inventory.yml");
} catch (InventoryException exception) {
    // Log any exceptions that occur during inventory loading
    exception.printStackTrace();
}
```
