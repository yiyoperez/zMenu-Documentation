# Commands

## Informations

Il plugin ha una cartella `commands` che conterrà tutti i tuoi comandi. Puoi creare un numero infinito di comandi. Un comando conterrà il nome del comando, i suoi alias, i suoi permessi e il nome dell'inventario da aprire.\
Puoi inserire diversi comandi per file e creare un numero illimitato di file.

```
|- commands
  |- punish
    - punish.yml
  |- example
    - example.yml    
  - commands.yml
```

## Sintassi

```yaml
commands:
  basic_command:
    command: basic_command
    inventory: basic_inventory
  advanced_command:
    command: advanced_command
    permission: "admin.use"
    aliases:
      - zai
    inventory: advanced_inventory
  pro_command:
    command: pro_command
    inventory: pro_inventory
  openbook:
    command: openbook
    actions:
      - type: book
        author: "Maxlego08" # Book author
        title: "&cTest" # Book title
        lines: # Book pages
          1: # First page
            - '     #34ebe8zMenu'
            - ''
            - ''
            - '<hover:show_text:"#34eba8Open an url !"><click:open_url:"https://minecraft-inventory-builder.com/">#f0af24Open URL<reset>'
  punish:
    command: punish
    permission: "admin.punish"
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - name: target
      - name: reason
        auto-completion:
          - cheat
          - chat
          - skin
          - other
        actions:
          - type: message
            messages:
              - "&7You will put a punishment to the player &f&n%target%&r &7with the reason&8: &f%reason%"            
```

***

### Comandi

```yaml
command: <command>
```

Comando principaale

***

### Alias

```yaml
aliases:
  - <aliase 1>
  - <aliase 2>
  - ...
```

Gli alias del comando

***

### Azioni

```yaml
actions:
  - ...  
```

Puoi utilizzare [azioni](buttons/actions.md) che verranno sempre eseguite durante l'esecuzione dell'ordine..

***

### Permessi

```yaml
permission: <permission>
```

Il permesso che il giocatore deve avere per aprire il menu.

***

### Inventario

```yaml
inventory: <inventory name>
```

Nome dell'inventario che verrà aperto.

Puoi anche specificare il nome del plugin in questo modo:

```yaml
inventory: "<plugin name>:<inventory name>"
```

***

### Arguments

```yaml
arguments:
  - <arg1>
  - <arg2>
  - ...
```

Ti permette di aggiungere arguments per i tuoi comandi. Puoi usare i arguments con questo placeholder: `%zmenu_argument_<argument name>%`&#x20;

#### Esempio

```yaml
commands:
  punish:
    command: punish
    permission: "admin.punish"
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - name: target
      - name: reason
        auto-completion:
          - cheat
          - chat
          - skin
          - other
        actions:
          - type: message
            messages:
              - "&7You will put a punishment to the player &f&n%target%&r &7with the reason&8: &f%reason%"
```

È possibile definire un'[azione](buttons/actions.md) e un elenco di completamento automatico per ciascuna azione.
Qui hai il comando **`/punish <target> <reason`**> . Quindi puoi eseguire il comando in questo modo: `/punish Maxlego08 Cheat (fly)`.

With the placeholders you will be able to retrieve the arguments:

| Placeholder               | Risultato     |
| ------------------------- | ------------- |
| `%zmenu_argument_target%` | `Maxlego08`   |
| `%zmenu_argument_reason%` | `Cheat (fly)` |

È possibile definire se il argument è facoltativo e se ha un inventario specifico.

#### **Esempio**

```yaml
arguments: # argument name, true or false, plugin name : inventory name
  - name,false,zmenu:example2
```

Hai:

* nome del argument
* true o false, scegli se il argument è obbligatorio o no
* nome dell'inventario. Puoi impostare il nome dell'inventario e del plugin
