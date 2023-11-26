# Commands

## Informations

The plugin has an `commands` folder that will contain all your commands. You can create an infinite number of commands. A command will contain the name of the command, its aliases, its permission and the name of the inventory to open.\
You can put several commands per file and create an unlimited number of files.

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
    arguments: # argument name, true or false, plugin name : inventory name
      - name,false,zmenu:example2      
```

***

### Command

```yaml
command: <command>
```

Main command

***

### Aliases

```yaml
aliases:
  - <aliase 1>
  - <aliase 2>
  - ...
```

The aliases of the command.

***

### Permission

```yaml
permission: <permission>
```

The permission the player must have to open the inventory.

***

### Inventory

```yaml
inventory: <inventory name>
```

Name of the inventory that will be opened.

You can also specify the name of the plugin this way:

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

Allows you to add arguments to your commands. You can use the arguments with the following placeholder: `%zmenu_argument_<argument name>%`&#x20;

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

Here you have the command **`/punish <target> <reason`**> . So you can run the command this way: `/punish Maxlego08 Cheat (fly)`.

With the placeholders you will be able to retrieve the arguments:

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

You have:

* argument name
* true or false, set argument required or not
* inventory name. You can set the inventory name and plugin name
