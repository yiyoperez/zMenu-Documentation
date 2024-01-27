---
description: Informations sur les valeurs du fichier config.json
---

# Config.json

```
enableDebug: true/false
```

Activer le débogage, permet d'afficher dans la console des erreurs qui seraient normalement cachées.



```
enableDebugTime: true/false
```

Activer le temps de débogage, vous permet d'afficher le temps d'exécution du code en nano seconde, parfait pour tester l'efficacité du plugin.



```
enableLogStorageFile: true/false
```

Activer l'enregistrement ou le chargement de fichiers dans la console



```
enableInformationMessage: true/false
```

Activer le message d'information, vous permet d'afficher des messages qui vous informent sur un inventaire ou sur le fait qu'une commande a été chargée avec succès.



```
enableOpenMessage: true/false
```

Activer le message ouvert, valeur par défaut de la commande `/zm open <inventory name> <player> <display message>`



```
enableMiniMessageFormat: true/false
```

Activer le format mini message, permet d'activer le format mini message, disponible à partir de la version 1.17, plus d'informations ici : [https://docs.advntr.dev/minimessage/index.html](https://docs.advntr.dev/minimessage/index.html)



```
enablePlayerCommandInChat: true/false
```

Activer les commandes du joueur dans le chat, vous permet de vous assurer que lorsqu'un joueur exécute une commande, il l'exécute depuis le chat et non depuis la console. Si vous avez de "fausses" commandes, qui ne sont pas sauvegardées dans le spigot, vous devez activer cette option.



```
secondsSavePlayerData: Int
```

Sauvegarde des données du joueur en quelques secondes: Temps en secondes pour la sauvegarde automatique des données du lecteur.



```
secondsSavePlayerInventories: Int
```

Sauvegarde des données du joueur en quelques secondes : Le temps en secondes pour la sauvegarde automatique des données de l'inventaire.



```
autoSaveFileInventoryOnUpdate: true/false
```

Sauvegarde automatique du fichier d'inventaire lors de la mise à jour : permet de sauvegarder automatiquement le fichier des inventaires des joueurs.



```
mainMenu: "example"
```

Nom du menu par défaut



```
useSwapItemOffHandKeyToOpenMainMenu: true
```

Ouvrir le menu principal en appuyant sur la touche f



```
useSwapItemOffHandKeyToOpenMainMenuNeedsShift: true
```

Ouvrir le menu principal lorsque l'on appuie sur la touche de substitution et sur la touche d'effacement.



```
specifyPathMenus: [
  "example",
]
```

Inventaires spécifiques au chargement



```
generateDefaultFile: true/false
```

Générer une configuration par défaut
