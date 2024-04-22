---
descrizione: Tutte le informazioni sugli inventari.
---

# Inventari

## Informazioni

Il plugin ha una cartella `inventories` che contiene tutti i tuoi inventari. Ogni inventario è rappresentato da un file. Puoi creare tutti gli inventari che desideri e le sottocartelle per ordinare i tuoi inventari.

Nella configurazione predefinita, hai questo:

```
|- inventories
  |- test
    |- test3
      - example3.yml
    - example2.yml
  - example.yml
  - example_shop.yml
  - example_punish.yml
```

***

## Sintassi

```yaml
name: "<inventory name>"
size: <inventory size>
fillItem: <itemstack>
updateInterval: <update interval>
clearInventory: <true/false>
items: <buttons>
open_requirement: <requirement>
```

***

### Nome

```yaml
name: "<inventory name>"
```

Il nome dell'inventario che verrà visualizzato. Tieni presente che a seconda della versione hai un limite di caratteri. Puoi utilizzare colori e segnaposto.
Se il tuo inventario ha più pagine, puoi visualizzare la pagina corrente e l'ultima pagina con i seguenti placeholders: \`%page%` - Current max \
`%maxPage%` - Last page

***

### Grandezza

```yaml
size: <inventory size>
```

Imposta la dimensione dell'inventario. Per impostazione predefinita il valore sarà `54`. La dimensione dell'inventario deve essere un multiplo di `9` compreso tra **9** e **54**. Quindi i seguenti valori:
* 9
* 18
* 27
* 36
* 45
* 54

***

### Fill Item

```yaml
fillItem: <itemstack>
```

Permette di riempire tutti gli slot dello stesso stack di oggetti. Vedi le informazioni necessarie [qui](https://zmenu.groupez.dev/configurations/items).
***

### Intervallo di Aggiornamento

```yaml
updateInterval: <update interval>
```

Permette di definire il tempo in millisecondi per l'aggiornamento dei pulsanti nell'inventario. Per aggiornare i pulsanti è necessario che l'opzione di aggiornamento sia abilitata. Maggiori informazioni [qui](https://zmenu.groupez.dev/configurations/buttons).
***

### Elimina l'inventario (temporaneamente)

```yaml
clearInventory: <true/false>
```

Permette di eliminare l'inventario del giocatore all'apertura e di ripristinarlo alla chiusura. Permette ad esempio di utilizzare un'immagine nel tuo inventario senza essere ostacolato dagli oggetti dei giocatori.
***

### Matrix

La configurazione matrix in un file YAML consente l'organizzazione intuitiva degli oggetti all'interno di un inventario di Minecraft fornendo una rappresentazione visiva della disposizione degli slot. Nell'esempio fornito, un inventario da 54 slot denominato "&8Test" utilizza una matrice di caratteri, dove "A" rappresenta gli slot pieni di diamanti, per creare un layout delimitato. Questo metodo migliora la chiarezza e l'efficienza del design, poiché ogni carattere nella matrice corrisponde a un elemento definito sotto la sezione `items`, consentendo una facile personalizzazione dei layout di inventario. L'uso di una matrix semplifica la creazione di progetti di inventario complessi mappando visivamente il posizionamento degli items.
```yaml
name: "&8Test"
size: 54
matrix:
  - "AAAAAAAAA"
  - "A       A"
  - "A       A"
  - "A       A"
  - "A       A"
  - "AAAAAAAAA"
items:
  A:
    item:
      material: DIAMOND
```

***

### Items

```yaml
items: <buttons>
```

Elenco dei pulsanti, tutte le informazioni [qui](https://zmenu.groupez.dev/configurations/buttons).
***

### ApriConItem

Apre l'inventario con l'interazione di un oggetto. È necessario definire le informazioni dell'item che verrà utilizzato, le azioni da eseguire (elenco completo [qui](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html )) e il tipo di verifica.
```yaml
# Open this menu by clicking a specific item
# You can use /zm giveopenitem <inventory> <player> to retrieve the item to use
#
openWithItem:
  # Define the item that will be clicked
  item:
    material: compass
    name: "&eOpen Basic Inventory"
    lore:
      - "&7Click on me !"
  # Look at https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html
  actions:
    - RIGHT_CLICK_BLOCK
    - RIGHT_CLICK_AIR
  # Define the type of verification.
  # Depending on your configuration and need you will define a certain type of verification. Here are all the types that exist:
  # - full -> Allows to check the itemStack in full, will use the ItemStack#isSimilar method.
  # - material -> Allows to check only the material
  # - name -> Allows to check only the display name
  # - lore -> Allows to check only the lore
  # - modelid -> Allows to check only the Custom Model Id
  type: full
```

***

### Open Requirement

Più informazioni [qui](buttons/requirements.md#open-requirement).
