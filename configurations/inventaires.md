---
description: Toutes les informations sur les inventaires.
---

# Inventaires

## Informations

Le plugin dispose d’un dossier d’inventaires qui contiendra tous vos inventaires. Chaque inventaire sera représenté par un fichier. Vous pouvez créer autant d’inventaires que vous le souhaitez ainsi que des sous-dossiers pour trier vos inventaires.

Dans la configuration par défaut, vous avez ceci :

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

## Syntax

```yaml
name: "<nom de l'invetaire>"
size: <taille de l'inventaire>
fillItem: <itemstack>
updateInterval: <intervale de mise à jour>
clearInventory: <true/false>
items: <buttons>
open_requirement: <requirement>
```

### Name

```yaml
name: "<nom de l'inventaire>"
```

Le nom de l'inventaire qui sera affiché. Veuillez noter qu'en fonction de votre version, vous avez une limite de caractères. Vous pouvez utiliser des couleurs et des caractères de remplacement.

Si votre inventaire comporte plusieurs pages, vous pouvez afficher la page actuelle et la dernière page à l'aide des espaces réservés suivants : \
`%page%` - Page actuelle \
`%maxPage%` - Dernière page

### Size

```yaml
size: <taille de l'inventaire>
```

Définit la taille de l'inventaire. Par défaut, la valeur est de `54`. La taille de l'inventaire doit être un multiple de `9` entre **9** et **54**. Vous devez choisir une taille d'inventaire dans la liste suivante :

* 9
* 18
* 27
* 36
* 45
* 54

### Fill Item

```yaml
fillItem: <itemstack>
```

Permet de remplir tous les emplacements d'un même ItemStack. Voir les informations sur les ItemStacks [ici](https://zmenu.groupez.dev/configurations/items).

### Update Interval

```yaml
updateInterval: <intervale de mise à jour>
```

Permet de définir le temps en secondes pour l'actualisation des boutons dans l'inventaire. Pour que les boutons soient mis à jour, l'option de mise à jour doit être activée. Plus d'informations [ici](https://zmenu.groupez.dev/configurations/buttons).

### Clear Inventory

```yaml
clearInventory: <true/false>
```

Permet de supprimer l'inventaire du joueur à l'ouverture et de le restaurer à la fermeture. Permet par exemple d'utiliser une image sur son inventaire sans être gêné par les objets des joueurs.

### Items

```yaml
items: <buttons>
```

Liste des boutons, toutes les informations [ici](https://zmenu.groupez.dev/configurations/buttons).

### OpenWithItem

Permet d'ouvrir l'inventaire avec l'interaction d'un item. Vous devez définir les informations de l'item qui va être utilisé, les actions à effectuer (liste complète [ici](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html)) et le type de vérification.

```yaml
# Ouvrez ce menu en cliquant sur un élément spécifique
#
openWithItem:
  # Définir l’élément qui sera cliqué
  item:
    material: clock
  # https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/block/Action.html
  actions:
    - LEFT_CLICK_BLOCK
    - LEFT_CLICK_AIR
  # Définissez ensuite le type de vérification.
  # Selon votre configuration et vos besoins, vous définirez un certain type de vérification. Voici tous les types qui existent :
  # - full -> Permet de vérifier l’itemStack en entier, utilisera la méthode ItemStack#isSimilar.
  # - material -> Permet de vérifier uniquement le material
  # - name -> Permet de vérifier uniquement le nom d’affichage
  # - lore -> Permet de vérifier seulement le lore
  # - modelid -> Permet de vérifier uniquement l’ID de modèle personnalisé
  type: material
```

### Open Requirement

Plus d'information [ici](broken-reference).
