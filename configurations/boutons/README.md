---
description: Toutes les informations sur les boutons
---

# Boutons

## Informations

Les boutons vous permettent de personnaliser les actions de votre inventaire. Vous devez spécifier le type du bouton à chaque fois et configurer les éléments spécifiques au type de bouton. Ici vous trouvez les boutons qui sont intégrés par défaut dans le plugin, d’autres plugins peuvent également ajouter de nouveaux types de boutons.

Pour chaque bouton vous devrez spécifier un ItemStack, pour savoir comment configurer un itemstack go [ici](https://zmenu.groupez.dev/configurations/items).

## Par défaut:

Voici les éléments de configuration communs à tous les types de boutons. Vous pouvez les utiliser partout.

```yaml
example: 
  # Sélectionnez le type de bouton, NONE par défaut
  type: <type du bouton>
  # Définir la fente du bouton, 0 par défaut
  slot: <slot>
  # Mettre des emplacements pour le bouton, vide par défaut
  slots: <liste de slot>
  # Définir la page du bouton, 1 par défaut
  page: <page>
  # Définir si le bouton doit apparaître sur toutes les pages
  isPermanent: <true ou false>
  # Article qui sera affiché, veuillez consulter la documentation des articles
  item: <itemstack>
  # Joué un son en cliquant
  sound: <son de XSound>
  # Volume du son
  volume: <volume du son>
  # Pitch du son
  pitch: <pitch du son>
  # Messages envoyés pendant les clics
  messages: <liste de messages>
  # Affiche un lien dans la liste des messages
  openLink: 
    link: <lien>
    message: <message>
    replace: <placeholder à remplacer>
    hover: <liste de message>
  # Fermer l'inventaire en cliquant
  closeInventory: <true ou false>
  # Rafraîchir le nom et l'histoire de l'objet au clic
  refreshOnClick: <true ou false>  
  # Afficher la tête du joueur, besoin d'un placeholder ou d'un nom de joueur
  playerHead: <placeholder>
  # Vous pouvez définir une ou plusieurs permissions pour l'affichage de l'élément
  permission: <permission>
  # Afficher un autre bouton s'il n'est pas coché (contrôle du placeholder, permissions ou autres)
  else: <else button>
  # Placeholder
  placeholder: <placeholder>
  # Valeur du placeholder
  value: <value for placeholder>
  # Action du placeholder
  action: <action for placeholder>
  # Liste de placeholders
  placeholders: <liste de placeholders>
  # Bouton de mise à jour au clic (tout mettre à jour)
  update: <true ou false>
  # Commande envoyée par les joueurs
  commands: <list of text>
  # Commande envoyée par la console lors d'un clic
  consoleCommands: <list of text>
  # Commande envoyée par la console lors d'un clic droit
  consoleRightCommands: <list of text>
  # Commande envoyée par la console lors d'un clic gauche
  consoleLeftCommands: <list of text>
  consolePermissionCommands: <list of text>
  consolePermission: <permissions>
  # Actions spécifiques au clic
  actions: <actions>
  # Mise à jour du nom et de l'histoire de l'objet lorsque le joueur clique sur l'inventaire
  updateOnClick: <true ou false>
  # Définit les requirements que le joueur doit avoir pour voir le bouton. 
  view_requirement: <requirement>
  # Définit les requirements que le joueur doit avoir pour cliquer sur le bouton. 
  click_requirement: <requirement>
```

***

### Type

```yaml
type: <type du bouton>
```

Le type du bouton, par défaut le type sera NONE.

***

### Slot

```yaml
slot: <nombre compris entre 0 et la limite de la taille de l'inventairet>
```

```yaml
slot: <page>-<slot>
```

Positionnez le slot sur laquelle votre bouton sera affiché.

{% hint style="info" %}
* Les créneaux commencent à **0**.
* Vous pouvez spécifier le numéro de page directement dans la fente. Vous devez procéder comme suit : \<page>-\<slot>. Par exemple, pour un bouton à la page **2** et à l'emplacement **8**, nous avons : **`2-8`**.
* Pour avoir plusieurs éléments sur le **même emplacement**, vous devez utiliser le bouton "else".
{% endhint %}

<figure><img src="../../.gitbook/assets/slot.png" alt=""><figcaption><p>Double chest slots</p></figcaption></figure>

Pour afficher un bouton sur plusieurs emplacements, vous pouvez procéder comme suit :

```yaml
slots:
  - 0
  - 1
  - 2
  - 3
  - 4
  ...
```

Vous pouvez également créer des plages de créneaux de cette manière: `<début du slot>-<fin du slot>`

```yaml
slots:
  - 0-9 # Du slot 0 au sot 9
  - 18
  - 17
  - 26
  - 27
  - 35
  - 36
  - 44-53 # Du slot 44 au slot 53
```

***

### Page

```yaml
page: <numéro de la page>
```

Permet de spécifier la page où le bouton sera affiché. Par défaut, la page sera la page **1**.

***

### IsPermanent

```yaml
isPermanent: <true ou false>
```

Vous permet de spécifier si le bouton doit être affiché sur toutes les pages de l'inventaire. Si votre inventaire ne comporte qu'une seule page, vous n'avez pas besoin de l'utiliser.

***

### Item

```yaml
item: <itemstack>
```

Permet de spécifier l'élément qui sera affiché, plus d'informations [ici](https://zmenu.groupez.dev/configurations/items).

***

### Sound

```yaml
sound: ENTITY_COW_HURT
pitch: 1.5
volume: 0.5
```

Permet d'envoyer un son au lecteur lorsqu'il clique. Vous devez utiliser les sons présents dans [XSound](https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java). Vous pouvez ensuite régler le pitch et le volume du son.

***

### Messages

```yaml
messages:
  - <line 1>
  - <line 2>
  ...
```

Allows you to send a list of messages to the player when clicking.

***

### Openlink

```yaml
link: <link>
message: <message>
replace: <replace string>
hover:
  - <line 1>
  - <line 2>
  ...
```

Permet d'envoyer un message cliquable au joueur. Vous devez mettre dans votre liste de messages un texte qui sera remplacé par le lien cliquable. Vous avez un exemple ci-dessous.&#x20;

> Exemple:

```yaml
messages:
  - "&8(&6zMenu&8) &fAjouter votre serveur au site &3Serveur Minecraft Vote"
  - "&8(&6zMenu&8) %link% &d!"
openLink:
  link: "https://serveur-minecraft-vote.fr/utiliser/un/code/cadeau?code=ZMENU"
  message: "&b&lClic ici"
  replace: "%link%"
  hover:
    - "&bClick sur moi !"
```

***

### CloseInventory

```yaml
closeInventory: <true ou false>
```

Permet de fermer l'inventaire après avoir cliqué.

***

### RefreshOnClick

```yaml
refreshOnClick: <true ou false>
```

Permet de rafraîchir le bouton après un clic. Vous pouvez par exemple l'utiliser pour créer une boutique. Un exemple est fourni dans la configuration par défaut of zShop.

***

### PlayerHead

```yaml
playerHead: <placeholder>
```

Permet d'afficher la tête d'un joueur en fonction d'un placeholder. Vous pouvez mettre le placeholder `%player%` pour obtenir le joueur qui ouvre l'inventaire. Un système de cache permet d'afficher directement le skin des têtes.



***

### Permission

```yaml
permission: <permission>
```

Permet de définir une permission que le joueur doit avoir pour afficher le bouton. Vous pouvez inverser la permission en ajoutant `!` devant la permission. Le plugin vérifiera alors que le joueur n'a pas la permission. Vous pouvez également définir une liste de permissions que le joueur doit avoir :

```yaml
permission:
  - "first.permission"
  - "!second.permission"
```

***

### Or Permission

Permet de définir une liste de permissions, mais le joueur ne doit avoir qu'une seule de ses permissions.

```yaml
orPermission:
  - "first.permission"
  - "!second.permission"
```

***

### Else

```yaml
else: <else button>
```

Permet d'afficher un autre bouton si le joueur n'en a pas la permission (ou autre élément qui va activer le else button). Vous pouvez mettre plusieurs else button à la suite sans problème. Vous avez un exemple d'utilisation dans la configuration par défaut.

***

### Placeholder

```yaml
  placeholder: <placeholder>
  value: <valeur du placeholder>
  action: <action du placeholder>
```

Permet de définir une autorisation à l'aide d'un placeholder. Vous devez spécifier le placeholder, l'action à effectuer avec la valeur et la valeur qui sera vérifiée.

**Action:**

* `BOOLEAN` : Vérifier si une valeur est vraie ou fausse
* `EQUALS_STRING` : Permet de vérifier si le texte est strictement égal au texte
* `EQUALSIGNORECASE_STRING` : Permet de vérifier si le texte est égal en ignorant la casse du texte
* `CONTAINS_STRING` : Permet de vérifier si le texte est contenu dans la valeur
* `SUPERIOR` : Permet de vérifier si un nombre est strictement supérieur à la valeur
* `LOWER` : Permet de vérifier si un nombre est strictement inférieur à la valeur
* `SUPERIOR_OR_EQUAL` : Permet de vérifier si un nombre est supérieur ou égal à la valeur
* `LOWER_OR_EQUAL` : Permet de vérifier si un nombre est inférieur ou égal à la valeur
* `EQUAL_TO` : Permet de vérifier que deux nombres sont identiques

Vous pouvez également définir une liste de placeholder comme ceci:

```yml
placeholders:
  - placeholder: <votre placeholder>
    value: <votre valeur>
    action: <votre action>
  - placeholder: <votre placeholder>
    value: <votre valeur>
    action: <votre action>
```

***

### Update

```yaml
update: <true ou false>
```

Permet de mettre à jour automatiquement le nom et le lore de l'ItemStack automatiquement. Pour définir l'intervalle, vous devez le faire à partir de [ici](../inventaires.md#update-interval).

### updateOnClick

***

```yaml
updateOnClick: <true ou false>
```

Permet de mettre à jour le bouton lorsqu'un joueur clique sur un autre bouton de l'inventaire.

### Commands

```yaml
commands: <liste de commandes>
```

Permet au joueur d'exécuter une liste de commandes.

***

### Console Commands

```yaml
consoleCommands: <liste de commandes>
consoleRightCommands: <liste de commandes>
consoleLeftCommands: <liste de commandes>
consolePermissionCommands: <liste de commandes>
consolePermission: <permissions>
```

Vous pouvez exécuter des commandes depuis la console en fonction du clic du joueur. Egalement des commandes si le joueur a les permissions.

### View Requirement

Définit les exigences que le joueur doit avoir pour voir le bouton. Plus d’informations [ici](broken-reference).

***

### Click Requirement

Définit les exigences que le joueur doit avoir pour cliquer sur le bouton. Plus d’informations [ici](broken-reference).

***

### Actions

Vous pouvez définir une liste d’actions à effectuer en cliquant. Plus d’informations [ici](broken-reference).

```yaml
actions:
  - type: message
    messages:
      - "exemple"
```

***

## NONE

Le type `NONE` est le type par défaut, il permet d'afficher un bouton. Il n'est pas nécessaire de le spécifier, il sera automatiquement choisi si le plugin ne trouve pas de type.

***

## Inventory

Le type `INVENTORY` permet au joueur d'ouvrir un nouvel inventaire.

```yaml
inventory: <nom du fichier d'inventaire>
plugin: <nom du plugin>
```

Vous devez spécifier le nom de l'inventaire. Le nom de l'inventaire sera le nom du fichier où se trouve l'inventaire. Nous vous conseillons également de préciser le nom du plugin d'où provient l'inventaire afin d'éviter toute confusion si deux inventaires portent le même nom.

***

## Back

Le type `BACK` permet de revenir à l'inventaire précédent.

***

## HOME

Le type `HOME` permet de revenir à l'inventaire principal, celui qui a été ouvert en premier.

***

## NEXT

Le type `NEXT` permet de passer à la page suivante si elle existe. Vous pouvez utiliser l'élément else pour afficher un autre bouton s'il n'y a pas de page suivante.

> Exemple :

```yaml
next:
  type: NEXT
  isPermanent: true
  slot: 50
  item:
    material: ARROW
    name: "&fNext"
  else: # Affiche un autre bouton s'il n'y a pas de page suivante.
    slot: 50
    type: NONE
    isPermanent: true
    item:
      material: BLACK_STAINED_GLASS_PANE
```

***

## PREVIOUS

Le type `PREVIOUS` permet d'aller à la page précédente si elle existe. Vous pouvez utiliser l'élément else pour afficher un autre bouton s'il n'y a pas de page précédente.

```yaml
next:
  type: PREVIOUS
  isPermanent: true
  slot: 50
  item:
    material: ARROW
    name: "&fNext"
  else: # Affiche un autre bouton s'il n'y a pas de page suivante.
    slot: 50
    type: NONE
    isPermanent: true
    item:
      material: BLACK_STAINED_GLASS_PANE
```

***

## MAINMENU

Le `MAINMENU` vous permet de retourner à l'inventaire principal que vous avez choisi dans le fichier config.json.
