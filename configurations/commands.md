# Commands

## Informations

Le plugin possède un dossier `commands` qui contiendra toutes vos commandes. Vous pouvez créer un nombre infini de commandes. Une commande contiendra le nom de la commande, ses alias, sa permission et le nom de l'inventaire à ouvrir. Vous pouvez mettre plusieurs commandes par fichier et créer un nombre illimité de fichiers.

```
|- commands
  |- punish
    - punish.yml
  |- example
    - example.yml    
  - commands.yml
```

## Syntax

```yaml
commands:
  example1:
    command: examplea
    aliases:
      - exampleb
    inventory: example
  example2:
    command: exampled
    permission: "admin.use"
    aliases:
      - examplec
      - examplee
    inventory: example2
  punish:
    command: punish
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - target
      - reason    
  example3:
    command: openfiles
    inventory: example3
    arguments: # nom de l'argument, vrai ou faux, nom du plugin : nom de l'inventaire
      - name,false,zmenu:example2      
```

### Command

```yaml
command: <command>
```

Commande principale

### Aliases

```yaml
aliases:
  - <aliase 1>
  - <aliase 2>
  - ...
```

Les alias de la commande.

### Permission

```yaml
permission: <permission>
```

Permission que le joueur doit avoir pour ouvrir l'inventaire.

### Inventory

```yaml
inventory: <inventory name>
```

Nom de l'inventaire qui sera ouvert.

Vous pouvez également spécifier le nom du plugin de cette manière :

```yaml
inventory: "<nom du plugin>:<nom de l'inventaire>"
```

### Arguments

```yaml
arguments:
  - <arg1>
  - <arg2>
  - ...
```

Permet d'ajouter des arguments à vos commandes. Vous pouvez utiliser les arguments avec l'espace réservé suivant: `%zmenu_argument_<argument name>%`&#x20;

#### Example

```yaml
commands:
  punish:
    command: punish
    aliases:
      - sanction
    inventory: example_punish
    arguments:
      - target
      - reason
```

Ici, vous avez la commande **`/punish <target> <reason`**> . Vous pouvez donc exécuter la commande de la manière suivante: `/punish Maxlego08 Cheat (fly)`.

Avec les Placeholders, vous pourrez récupérer les arguments :

| Placeholder               | Result        |
| ------------------------- | ------------- |
| `%zmenu_argument_target%` | `Maxlego08`   |
| `%zmenu_argument_reason%` | `Cheat (fly)` |

You can define whether the argument is optional and whether the argument has a specific inventory.

#### **Example**

```yaml
arguments: # argument name, true or false, plugin name : inventory name
  - name,false,zmenu:example2
```

Vous avez :

* nom de l'argument
* vrai ou faux, argument requis ou non
* le nom de l'inventaire. Vous pouvez définir le nom de l'inventaire et le nom du plugin
