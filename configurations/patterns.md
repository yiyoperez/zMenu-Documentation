# Schemi

## Inventario

Gli schemi consentono di avere un elenco di pulsanti che possono essere utilizzati in diversi inventari. Perfetto per gestire la decorazione dei tuoi inventari senza dover copiare la stessa cosa decine di volte.

I modelli si trovano nella cartella dei modelli e puoi crearne quanti ne vuoi.

[Esempio](../plugins-files.md#pattern1):

```yaml
name: "pattern1"
size: 54
# Displays the pattern on multiple pages, false by default
enableMultiPage: <true/false>
items:
    ...
```

Uno schema deve contenere `name`, il suo nome verrà utilizzato nei menu per identificare lo schema.&#x20;

Poi la `size`, che è quello dell'inventario, devi mettere i schemi della stessa con menu della stessa grandezza, uno schema di grandezza 18 non può essere utilizzato con uno di 27. Esempio:

Hai una lista di items, è lo stesso per gli [inventari](inventories.md#items).

## Pulsanti

Puoi creare uno schema per i tuoi pulsanti per evitare di dover ripetere la stessa cosa centinaia di volte. Risparmierai ore di configurazione con questo sistema.
### How to create a pattern ?

È necessario creare un file yml nella cartella pattern, il nome del file è importante. Verrà utilizzato nel file di inventario. Nel file è necessario specificare il nome, la tipologia e il pulsante. Un file predefinito sarà simile al seguente:
```yaml
name: "<your name>"
type: BUTTON
button:
```

Potrai quindi configurare il tuo pulsante come fai per gli inventari. Solo che qui potrai definire le variabili dal file di inventario che verrà utilizzato qui. Puoi definire un numero infinito di variabili, tutto dipende dalle tue necessità.
Ecco un esempio di uno schema con il nome e lo slot che cambiano.
```yaml
name: 'Example'
type: BUTTON
button:
  slot: '%slot%'
  item:
    material: PAPER
    name: "&c%name%"
```

Una variabile può avere prefissi per modificarne l'uso.



<table data-full-width="true"><thead><tr><th>Prefix</th><th>Definition</th></tr></thead><tbody><tr><td>%upper_&#x3C;key>%</td><td>Displays the text in uppercase</td></tr><tr><td>%lower_&#x3C;key>%</td><td>Displays the text in lowercase</td></tr><tr><td>%capitalize_&#x3C;key>%</td><td>Display the text in capital</td></tr><tr><td>%add_one_&#x3C;key>%</td><td>Allows to add one to the value, attention the value must be a number.</td></tr><tr><td>%remove_one_&#x3C;key>%</td><td>Allows to remove one has the value, attention the value must be mandatory a number.</td></tr></tbody></table>

### Come usare uno schema

Usare uno schema è molto semplice. Visualizza semplicemente la configurazione dello schema nel pulsante, imposta il nome del file e inserisci i placeholders. Per l'esempio se sopra avremo:
```yaml
name: 'Example'
size: 54
items:
  example1:
    pattern:
      fileName: "<your file name>"
      slot: 10
      name: 'Example 1'
  example2:
    pattern:
      fileName: "<your file name>"
      slot: 12
      name: 'Example 1'
```

Lo schema può essere utilizzato all'infinito nell'inventario. Ciò consente di creare configurazioni molto ottimizzate senza dover ripetere la stessa cosa più volte. Solo gli articoli importanti saranno nel tuo file di inventario.
### Esempio

Questo esempio proviene da un [Vote Menu](https://builtbybit.com/resources/vote-menu-zmenu-configurations.41468/).

#### Inventory Shop

```yaml
name: '&l#8fa3e8ᴠᴏᴛᴇ sʜᴏᴘ'
size: 54
items:

  shop1:
    pattern:
      fileName: "vote_shop" # 
      slot: 20
      point: 10
      material: DIAMOND_BLOCK
      name: ' #3f3f3f▷ #6ff8edDiamond Blocks #3f3f3f◁'
      description:
        - '#3f3f3f• &fx16 Diamond Blocks'
      commands:
        - 'give %player% diamond_block 16'

  shop2:
    pattern:
      fileName: "vote_shop"
      slot: 21
      point: 20
      material: EMERALD_BLOCK
      name: ' #3f3f3f▷ #40f082Emerald Blocks #3f3f3f◁'
      description:
        - '#3f3f3f• &fx16 Emerald Blocks'
      commands:
        - 'give %player% emerald_block 16'

  shop3:
    pattern:
      fileName: "vote_shop"
      slot: 22
      point: 6
      material: IRON_BLOCK
      name: ' #3f3f3f▷ #e3e3e3Iron Blocks #3f3f3f◁'
      description:
        - '#3f3f3f• &fx16 Iron Blocks'
      commands:
        - 'give %player% iron_block 16'
```

#### Schema

```yaml
name: 'Vote Reward'
type: BUTTON
button:
  slot: '%slot%'
  view_requirement:
    requirements:
      - type: placeholder
        placeholder: "%zmenu_player_value_vote_points%"
        value: '%point%'
        action: LOWER
  updateOnClick: true
  actions:
    - type: sound
      sound: ENTITY_VILLAGER_NO
  item:
    material: '%material%'
    name: '%name%'
    lore:
      - ''
      - '#ffd353⛃ ᴅᴇsᴄʀɪᴘᴛɪᴏɴ#3f3f3f:'
      - '%description%'
      - ''
      - '#ffd353🌟 ᴘʀɪᴄᴇ#3f3f3f: #8fa3e8%point% points'
      - ''
      - '#ff0000✘ ʏᴏᴜ ᴅᴏɴ’ᴛ ʜᴀᴠᴇ ᴇɴᴏᴜɢʜ ᴠᴏᴛᴇ ᴘᴏɪɴᴛs'
  else:

    updateOnClick: true
    refreshOnClick: true
    click_requirement:
      right_click:
        clicks:
          - ALL
        requirements:
          - type: placeholder
            placeholder: "%zmenu_player_value_vote_points%"
            value: '%point%'
            action: SUPERIOR_OR_EQUAL
        deny:
          - type: sound
            sound: VILLAGER_NO
          - type: message
            messages:
              - "#3f3f3f[#ff0000✘#3f3f3f] #ff0000An error has occurred, please re-open the inventory."
          - type: close
        success:
          - type: data
            action: SUBTRACT
            key: 'vote_points'
            value: '%point%'
          - type: console_command
            commands:
              - '%commands%'
          - type: sound
            sound: ENTITY_PLAYER_LEVELUP

    item:
      material: '%material%'
      name: '%name%'
      lore:
        - ''
        - '#ffd353⛃ ᴅᴇsᴄʀɪᴘᴛɪᴏɴ#3f3f3f:'
        - '%description%'
        - ''
        - '#ffd353🌟 ᴘʀɪᴄᴇ#3f3f3f: #8fa3e8%point% points'
        - ''
        - '#ffd353➥ ᴄʟɪᴄᴋ ᴛᴏ ᴘᴜʀᴄʜᴀsᴇ'
```
