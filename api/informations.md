---
description: API Information
---

# ℹ️ Informations

The zMenu API will allow you to create your own inventory and button. You can have the same configuration system for all your plugins.

Javadocs: [https://javadocs.groupez.dev/zmenu/index.html](https://javadocs.groupez.dev/zmenu/index.html)

Example: [https://github.com/Maxlego08/zMenuExample](https://github.com/Maxlego08/zMenuExample)



Last version here: [https://github.com/Maxlego08/zMenu-API/tags](https://github.com/Maxlego08/zMenu-API/tags)

## Maven

```xml
<repositories>
	<repository>
		<id>jitpack.io</id>
		<url>https://jitpack.io</url>
	</repository>
</repositories>

<dependencies>
	<dependency>
		<groupId>com.github.Maxlego08</groupId>
		<artifactId>zMenu-API</artifactId>
		<version>VERSION</version>
	</dependency>
</dependencies>
```

## Gradle

```bash
allprojects {
	repositories {
		...
		maven { url 'https://jitpack.io' }
	}
}

dependencies {
		implementation 'com.github.Maxlego08:zMenu-API:VERSION'
}
```

## First step

The first step is to get the [InventoryManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html) and [ButtonManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html) interface with the spigot service provider system.

```java
@Override
public void onEnable() {
    InventoryManager inventoryManager = getProvider(InventoryManager.class);
    ButtonManager buttonManager = getProvider(ButtonManager.class);
}

private <T> T getProvider(Class<T> classz) {
    RegisteredServiceProvider<T> provider = getServer().getServicesManager().getRegistration(classz);
    return provider == null ? null : provider.getProvider() != null ? (T) provider.getProvider() : null;
}
```
