---
description: Player data system
---

# Player data

Avec zMenu vous pouvez stocker des données pour le joueur et les utiliser avec des placeholders. Vous pouvez ainsi créer des compteurs, des cooldowns et bien plus encore !

Chaque donnée contient une clé, une valeur et une date d'expiration. Si vous mettez **0**, les données n'expireront jamais. La date d'expiration est un timestamp.

## Commandes

L'autorisation d'utiliser ces commandes est: `zmenu.players`

<table><thead><tr><th width="410">Command</th><th>Description</th></tr></thead><tbody><tr><td>/zm players</td><td>Affiche la liste des commandes pour les données des joueurs.</td></tr><tr><td>/zm players set &#x3C;player> &#x3C;key> &#x3C;expiration> &#x3C;value></td><td>Définir les données du nouveau joueur. Vous devez définir le délai d'expiration en secondes. Mettez 0 pour ne pas avoir d'expiration.</td></tr><tr><td>/zm players remove &#x3C;player> &#x3C;key></td><td>Supprimer les données du lecteur.</td></tr><tr><td>/zm players get &#x3C;player> &#x3C;key></td><td>Obtenir des données sur les joueurs.</td></tr><tr><td>/zm players kets &#x3C;player></td><td>Renvoie la liste des clés d'un lecteur.</td></tr><tr><td>/zm players clear &#x3C;player></td><td>Effacer les données du joueur.</td></tr><tr><td>/zm players clearall</td><td>Effacer toutes les données des joueurs.</td></tr></tbody></table>

## Placeholders

Les Placeholders peuvent être utilisés dans un inventaire pour l'affichage d'un élément ou d'une autorisation. Vous pouvez bloquer l'accès à un bouton à l'aide d'un espace réservé. Vous pouvez voir un exemple [ici](../plugins-files.md).

<table><thead><tr><th width="426.56591923371104">Placeholder</th><th>Description</th></tr></thead><tbody><tr><td><code>%zmenu_player_value_&#x3C;key>%</code></td><td>Renvoie la valeur contenue dans une clé.</td></tr><tr><td><code>%zmenu_player_expire_format_&#x3C;key>%</code></td><td>Renvoie l'heure d'expiration formatée selon une clé.</td></tr><tr><td><code>%zmenu_player_expire_&#x3C;key>%</code></td><td>Renvoie le délai d'expiration en fonction d'une clé.</td></tr><tr><td><code>%zmenu_player_key_exist_&#x3C;key>%</code></td><td>Retourne true ou false. Permet de savoir si une clé existe.</td></tr></tbody></table>
