---
description: API Information
---

# Informations

L'API zMenu vous permettra de créer votre propre inventaire et vos propres boutons. Vous pouvez avoir le même système de configuration pour tous vos plugins.

Javadocs: [https://javadocs.groupez.dev/zmenu/index.html](https://javadocs.groupez.dev/zmenu/index.html)

Exemple: [https://github.com/Maxlego08/zMenuExample](https://github.com/Maxlego08/zMenuExample)



Dernière version ici : [https://github.com/Maxlego08/zMenu-API/tags](https://github.com/Maxlego08/zMenu-API/tags)

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

## Première étape

La première étape consiste à obtenir le [InventoryManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/InventoryManager.html) et [ButtonManager](https://javadocs.groupez.dev/zmenu/fr/maxlego08/menu/api/ButtonManager.html) l'interface avec le système du fournisseur de services du spigot.

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
