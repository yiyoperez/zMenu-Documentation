---
description: Informazioni sui valori nel file config.json
---

# Config.json

```
enableDebug: true/false
```

Abilita il debug, ti permette di mostrare errori nella console che normalmente sarebbero nascosti.



```
enableDebugTime: true/false
```

Abilita il tempo di debug, consente di visualizzare il tempo di esecuzione del codice in nano secondi, perfetto per testare l'efficacia del plugin.


```
enableLogStorageFile: true/false
```

Abilita il salvataggio o il caricamento del registro dei file nella console


```
enableInformationMessage: true/false
```

Abilita i messaggi informativi, ti consente di visualizzare i messaggi che ti informano su un inventario o che un ordine è stato caricato con successo.


```
enableOpenMessage: true/false
```

Abilita la notifica di quando apri un menu, valore predefinito per il comando `/zm open <inventory name> <player> <display message>`



```
enableMiniMessageFormat: true/false
```

Abilita il formato minimessage, permette di attivare il formato mini message, disponibile dalla 1.17 in poi, maggiori informazioni qui: [https://docs.advntr.dev/minimessage/index.html](https://docs.advntr.dev/minimessage/index.html)



```
enablePlayerCommandInChat: true/false
```

Abilita il comando del giocatore in chat, Ti permette di assicurarti che quando un giocatore esegue un comando, lo esegua dalla chat e non dalla console. Se hai comandi "fake", che non vengono salvati in spigot, devi abilitare questa opzione.



```
secondsSavePlayerData: Int
```

Secondi necessari per il salvataggio dati: il tempo in secondi per il backup automatico dei dati del giocatore.


```
secondsSavePlayerInventories: Int
```

Secondi necessari per il salvataggio dati: il tempo in secondi per il backup automatico dei menu.



```
autoSaveFileInventoryOnUpdate: true/false
```

Salvataggio automatico dell'inventario dei file all'aggiornamento: consente di salvare automaticamente il file degli inventari dei giocatori.


```
mainMenu: "example"
```

Nome predefinito dei menu



```
useSwapItemOffHandKeyToOpenMainMenu: true
```

Apri il menu principale quando il tasto f è premuto



```
useSwapItemOffHandKeyToOpenMainMenuNeedsShift: true
```

Apri il menu principale quando il tasto f e shift sono premuti



```
specifyPathMenus: [
  "example",
]
```

Carica menu specifici



```
generateDefaultFile: true/false
```

Genera configurazione predefinita
