---
description: Liste des commandes et leurs permissions
---

# Commandes et permissions

## Commandes

<table data-full-width="true"><thead><tr><th width="359.9193183740604">Commande</th><th width="160.96698547592337">Permission</th><th>Description</th></tr></thead><tbody><tr><td>/zm (alias: /zmenu)</td><td>zmenu.use</td><td>Affiche la liste des commandes.</td></tr><tr><td>/zm open &#x3C;menu> [&#x3C;player>] [&#x3C;display message>] [&#x3C;args>]</td><td>zmenu.open</td><td>Ouvre un inventaire</td></tr><tr><td>/zm reload</td><td>zmenu.reload</td><td>Rechargez les configurations.</td></tr><tr><td>/zm reload config</td><td>zmenu.reload</td><td>Rechargez les fichiers config.json et messages.yml</td></tr><tr><td>/zm reload inventory [&#x3C;inventory name>]</td><td>zmenu.reload</td><td>Recharger les fichiers d’inventaires</td></tr><tr><td>/zm reload command [&#x3C;command name>]</td><td>zmenu.reload</td><td>Recharger les fichiers de commandes</td></tr><tr><td>/zm version</td><td></td><td>Show plugin version.</td></tr><tr><td>/zm convert</td><td>zmenu.convert</td><td>Convertir DeluxeMenu en zMenu.</td></tr><tr><td>/zm list</td><td>zmenu.list</td><td>Liste des inventaire</td></tr><tr><td>/zm create &#x3C;file name> &#x3C;inventory size> &#x3C;inventory name></td><td>zmenu.create</td><td>Créez un nouveau fichier d’inventaire, il vous suffit d’ajouter des boutons par la suite.</td></tr><tr><td>/zm save &#x3C;nom de l'item></td><td>zmenu.save</td><td>Sauvegarder l'item que vous avez en main dans le formation de configuration du plugin.</td></tr><tr><td>/zm giveopenitem &#x3C;inventory> [&#x3C;player>]</td><td>zmenu.open.item</td><td>Permet de récupérer l'item qui doit être utilisé pour ouvrir l'inventaire lors d'un click</td></tr><tr><td>/&#x3C;command></td><td>Permission personnalisés</td><td>Ouvrez un fichier spécifique.</td></tr></tbody></table>

Liste des commandes pour le système de données du lecteur [ici](player-data.md).

## Commande /zm open avec argument

Vous pouvez utiliser la commande /zm open avec des arguments (comme [ici](commands.md#informations)).

Par exemple, avec l’exemple d’inventaire par défaut `example_punish`. Vous pourrez définir les deux arguments à utiliser. Vous pouvez le faire de deux façons.

* La première consiste à préciser les noms des arguments, comme suit : `<`nom de l'argument`>:<valeur de l'argument>`\
  Exemple: `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:test`\
  Résultat: `%zmenu_argument_target%` et`%zmenu_argument_reason%`\
  Vous pouvez également ajouter d’autres arguments comme celui-ci : `/zm open zmenu:example_punish Maxlego08 false target:Maxlego09 reason:"this is a really long reason"`
* La seconde est d’utiliser directement la valeur, donc le nom de l’argument sera 0 pour la première valeur, 1 pour la seconde etc...\
  Exemple: `/zm open zmenu:example_punish Maxlego08 false Maxlego09 test`\
  Result: `%zmenu_argument_0%` and `%zmenu_argument_1%`

## Convertir

Pour convertir vos configurations **DeluxeMenu** en **zMenu**, vous devez utiliser l’extension **zMenuConvert**.

Téléchargement: [https://groupez.dev/resources/zmenuconvert.266](https://groupez.dev/resources/zmenuconvert.266)

Après avoir installé le plugin, vous devez exécuter la commande /zm convert. Vos menus et commandes seront créés dans les dossiers `inventories/convert` et`commands/convert`.

Attention, la conversion peut contenir des erreurs, vous devez vérifier vos fichiers pour vous assurer qu’il n’y a pas de problèmes.

Github: [https://github.com/Maxlego08/zMenuConvert](https://github.com/Maxlego08/zMenuConvert)
