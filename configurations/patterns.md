# Patterns

Les paternes vous permettent d'avoir une liste de boutons qui peuvent être utilisés dans plusieurs inventaires. Parfait pour gérer la décoraction de vos inventaires sans avoir à recopier des dizaines de fois la même chose.

Les paternes se trouvent dans le dossier des motifs et vous pouvez en créer autant que vous le souhaitez.

[Exemple](../plugins-files.md#pattern1) :

```yaml
name: "pattern1"
size: 54
items:
    ...
```

Un motif doit contenir un `name`, qui sera utilisé dans les inventaires pour identifier le motif.

Vous avez ensuite une `size`, qui est celle de l'inventaire, vous devez mettre des patrons de la même taille avec les inventaires, un patron de taille 18 ne peut pas aller avec un inventaire de taille 27 par exemple.

Vous avez alors une liste d'éléments, c'est la même chose que pour [inventories](inventaires.md#items).
