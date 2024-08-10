---
description: Information about the values in the config.json file
---

# 🦬 Config.json

```
enableDebug: true/false
```

Enable debug, allows you to display errors in the console that would normally be hidden.



```
enableDebugTime: true/false
```

Enable debug time, allows you to display the code execution time in nano second, perfect for testing the effectiveness of the plugin.



```
enableLogStorageFile: true/false
```

Enable save or load file log in console



```
enableInformationMessage: true/false
```

Enable information message, allows you to view messages that tell you about an inventory or that an order has been successfully loaded.



```
enableOpenMessage: true/false
```

Enable open message, default value for the command `/zm open <inventory name> <player> <display message>`



```
enableMiniMessageFormat: true/false
```

Enable mini message format, allows you to activate the mini message format, available from 1.17 onwards, more information here: [https://docs.advntr.dev/minimessage/index.html](https://docs.advntr.dev/minimessage/index.html)



```
enablePlayerCommandInChat: true/false
```

Enable player command in chat, Allows you to ensure that when a player executes a command, they execute it from the chat and not from the console. If you have "fake" command, which are not saved in spigot you need to enable this option.



```
secondsSavePlayerData: Int
```

Seconds save player data: The time in seconds for automatic backup of player data.



```
secondsSavePlayerInventories: Int
```

Seconds save player data: The time in seconds for automatic backup of inventories data.



```
autoSaveFileInventoryOnUpdate: true/false
```

Auto save file inventory on update: allows you to save the file of jouueurs inventories automatically.



```
mainMenu: "example"
```

Default menu name



```
useSwapItemOffHandKeyToOpenMainMenu: true
```

Open main menu when f key is press



```
useSwapItemOffHandKeyToOpenMainMenuNeedsShift: true
```

Open main menu when swap item offhand key is press and sneak key



```
specifyPathMenus: [
  "example",
]
```

Load specific inventories



```
generateDefaultFile: true/false
```

Generate default configuration
