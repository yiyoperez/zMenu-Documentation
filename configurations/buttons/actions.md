---
description: Actions that can be performed after a requirement
---

# ☢️ Actions

With a requirement, you can define actions for both success and failure. Here are the actions that can be performed.

**Example:** You will need to create an action list like this:

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

You can add a delay, in ticks, for each item in the list below. Do it like this:

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
  commandInChat: false # false by default
</code></pre></td><td>Executes commands as the player. You can also send the command in the player's chat.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: console_command
  commands:
    - "firstcommand"
    - "seconds commands %player%"
</code></pre></td><td>Executes commands as the console.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: message
  messages:
    - "my message"
    - "my second messages"
  minimessage: true # true by default
</code></pre></td><td>Sends a message to the player. You can use placeholders, color codes, and format codes. The MiniMessage format is enabled by default if your server supports it.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: broadcast
  messages:
    - "my message"
    - "my second message to %player%"
  minimessage: true # true by default
</code></pre></td><td>Sends a message to all online players. You can use placeholders, color codes, and format codes. The MiniMessage format is enabled by default if your server supports it.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: chat
  messages:
    - "my message"
</code></pre></td><td>Sends messages on behalf of the player. You can use placeholders, color codes, and format codes. MiniMessage format is enabled by default if your server supports it.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: close
</code></pre></td><td>Closes the player's inventory.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: inventory
  inventory: &#x3C;inventory name>
  plugin: &#x3C;plugin name>
  page: &#x3C;page>
  arguments: &#x3C;argument list>
</code></pre></td><td>Opens an inventory of zMenu.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: connect
  server: &#x3C;server name>
</code></pre></td><td>Allows sending the player to another server, only works with BungeeCord and Velocity.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: sound
  sound: &#x3C;xsound>
  pitch: &#x3C;sound pitch> # 1.0f by default
  volume: &#x3C;sound volume> # 1.0f by default
</code></pre></td><td>Send a sound to a player, you must use <a href="https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java">XSound</a> for sound.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: broadcast_sound
  sound: &#x3C;xsound>
  pitch: &#x3C;sound pitch> # 1.0f by default
  volume: &#x3C;sound volume> # 1.0f by default
</code></pre></td><td>Send a sound to the online players, you must use <a href="https://github.com/CryptoMorin/XSeries/blob/master/src/main/java/com/cryptomorin/xseries/XSound.java">XSound</a> for sound.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: data
  action: &#x3C;SET/REMOVE/ADD/SUBTRACT>
  key: &#x3C;data key>
  value: &#x3C;data value>
  seconds: &#x3C;expire seconds> # 0 by default
</code></pre></td><td>Update <a href="../player-data.md">player data</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: refresh  
</code></pre></td><td>Refresh current button. Works only in click requirement.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: back
</code></pre></td><td>Return to previous inventory.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: shopkeeper
  name: &#x3C;shopkeeper name>
</code></pre></td><td>Open a <a href="https://www.spigotmc.org/threads/shopkeepers.447969/">Shopkeeper</a> trading inventory</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: book
  author: "Maxlego08" # Book author
  title: "&#x26;cTest" # Book title
  lines: # Book pages
    1: # First page
      - '     #34ebe8zMenu'
      - ''
      - ''
      - '&#x3C;hover:show_text:"#34eba8Open an url !">&#x3C;click:open_url:"https://minecraft-inventory-builder.com/">#f0af24Open URL&#x3C;reset>'
</code></pre></td><td>Opens a book for the player. You can specify the title, author, and pages of the book.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: title
  title: "My title"
  subtitle: "And a sub title!"
  start: &#x3C;time>
  duration: &#x3C;time>
  end: &#x3C;time>
</code></pre></td><td><p>Allows you to send a title to the player. <br>Time must be in millis if using enableMiniMessageFormat, or else just use ticks.</p><pre><code>20 ticks = 1 second
1000 millis = 1 second
</code></pre></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml"><strong>- type: actionbar
</strong>  message: "my message"
  minimessage: true # true by default
</code></pre></td><td>Allows you to send a message in the action bar of the player. You can use placeholders and color/format codes here. MiniMessage format is enabled by default if your server supports it.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: withdraw
  amount: &#x3C;amount>
</code></pre></td><td>Allows you to withdraw money from the player’s account. Works with the <a href="https://www.spigotmc.org/resources/vault.34315/">Vault</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: deposit
  amount: &#x3C;amount>
</code></pre></td><td>Allows you to deposit money from the player’s account. Works with the <a href="https://www.spigotmc.org/resources/vault.34315/">Vault</a>.</td></tr></tbody></table>
