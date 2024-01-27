---
description: Actions that can be performed after a requirement
---

# Action

Avec les requirements, vous pouvez définir des actions sur le succès ou l’échec. Voici les actions qui peuvent être effectuées.

## Exemple

Vous devrez mettre une liste d’actions comme celle-ci :

```yaml
success_actions:
  - type: player_command
    commands:
      - "firstcommand"
      - "seconds commands %player%"
  - type: console_command
    commands:
      - "firstcommand"
      - "seconds commands %player%"      
  - type: message
    messages:
      - "firstcommand"
      - "seconds commands %player%"   
```

Vous pouvez ajouter un délai, en tick, pour chaque élément ci-dessous. Procédez comme suit :

```yaml
success_actions:
  - type: player_command
    delay: 10 # 10 ticks
    commands:
      - "firstcommand"
      - "seconds commands %player%"
```

<table data-full-width="true"><thead><tr><th width="544">Action</th><th>Description</th></tr></thead><tbody><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: player_command
  commands:
    - "firstcommand"
    - "seconds commands %player%"
  commandInChat: false # false par défaut
</code></pre></td><td>Exécutez les commandes en tant que joueur. Vous pouvez envoyer la commande dans le tchat du joueur.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: console_command
  commands:
    - "firstcommand"
    - "seconds commands %player%"
</code></pre></td><td>Exécuter les commandes en tant que console.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: message
  messages:
    - "my message"
    - "my second messages"
  minimessage: true # true par défaut
</code></pre></td><td>Envoyez un message au lecteur. Vous pouvez utiliser des espaces réservés et des codes couleur/format ici. Le format de message mini est activé par défaut si votre serveur le supporte.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: broadcast
  messages:
    - "my message"
    - "my second message to %player%"
  minimessage: true # true par défaut
</code></pre></td><td>Envoyez un message aux joueurs en ligne. Vous pouvez utiliser des espaces réservés et des codes couleur/format ici. Le format de message mini est activé par défaut si votre serveur le supporte.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: chat
  messages:
    - "my message"
</code></pre></td><td>Envoie des messages à la place du joueur.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: close
</code></pre></td><td>Ferme l’inventaire du joueur.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: inventory
  inventory: &#x3C;inventory name>
  plugin: &#x3C;plugin name>
</code></pre></td><td>Ouvre un inventaire de zMenu.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: connect
  server: &#x3C;server name>
</code></pre></td><td>Permet d’envoyer le joueur vers un autre serveur, ne fonctionne qu’avec BungeeCord et Velocity.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: sound
  sound: &#x3C;xsound>
  pitch: &#x3C;sound pitch> # 1.0f par défaut
  volume: &#x3C;sound volume> # 1.0f par défaut
</code></pre></td><td>Envoyer un son à un joueur, vous devez utiliser <a href="https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java">XSound</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: broadcast_sound
  sound: &#x3C;xsound>
  pitch: &#x3C;sound pitch> # 1.0f par défaut
  volume: &#x3C;sound volume> # 1.0f par défaut
</code></pre></td><td>Envoyer un son aux joueurs en ligne, vous devez utiliser <a href="https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java">XSound</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: data
  action: &#x3C;SET/REMOVE>
  key: &#x3C;data key>
  value: &#x3C;data value>
  seconds: &#x3C;expire seconds> # 0 par défaut
</code></pre></td><td>Mettre à jour le <a href="../player-data.md">player data</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: refresh  
</code></pre></td><td>Actualiser le bouton actuel. Fonctionne uniquement en le click requirement.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: back
</code></pre></td><td>Revenir à l'inventaire précédent.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: shopkeeper
  name: &#x3C;nom du shopkeeper>
</code></pre></td><td>Ouvrir un inventaire de trade du plugin <a href="https://www.spigotmc.org/threads/shopkeepers.447969/">Shopkeeper</a>.</td></tr></tbody></table>

