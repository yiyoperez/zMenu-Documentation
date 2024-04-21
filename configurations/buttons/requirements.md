# Requirements

The requirements will allow you to perform actions based on a permission check.

## Requirements

### Syntax

```yaml
# open_requirement
# click_requirement
view_requirement:

  # Set the minimum number of requirements to be able to say this is a success.
  # By default the value will be the same as the number of requirements.
  miniumRequirement: <number>
  
  # List of requirements, all information about each type below
  requirements:
    - type: permission
      permission: "example.permission"
      deny:
        - type: message
          messages:
            - "&cYou don't have permission !"
    - type: placeholder
      placeholder: "%player_gamemode%" # need PAPI ecloud Player
      value: "CREATIVE"    
      action: equals_string
      # Specific deny actions
      deny:
        - type: message
          messages:
            - "&cYou mus be in creative"      
    - type: regex
      input: "%player_item_in_hand%" # need PAPI ecloud Player
      regex: "(NETHERITE_|DIAMOND_|IRON_|GOLDEN_|STONE_|WOODEN_|LEATHER_|BOW|CROSSBOW|FISHING_ROD|SHEARS|SHIELD|TRIDENT|TURTLE_HELMET|ELYTRA|FLINT_AND_STEEL)"      
      deny:
        - type: message
          messages:
            - "&cYou dont have items in your hand !"
  
  # Global Success actions
  success:
    - type: sound
      sound: ENTITY_PLAYER_LEVELUP
      
  # Global Deny actions
  deny:    
    - type: message
      messages:
        - "&cYou doesn't have an item in your hand."
```

In addition to deny and global success actions, you can define deny and success actions for each requirement.

### View Requirement

Define the requirements to see a button in the inventory.

#### Example:

```yaml
view_requirement:
  deny:
    - type: chat
      messages:
        - "Hey, my name is %player%"
  success:
    - type: sound
      sound: ENTITY_PLAYER_LEVELUP
  requirements:
    - type: permission
      permission: "admin.use"
    - type: placeholder
      placeholder: "%player_is_flying%"
      value: "yes"
      action: equals_string
```

### Open Requirement

Define the requirements to open the inventory.

#### Example

```yaml
open_requirement:
  requirements:
    - type: regex
      input: "%player_item_in_hand%"
      regex: "(NETHERITE_|DIAMOND_|IRON_|GOLDEN_|STONE_|WOODEN_|LEATHER_|BOW|CROSSBOW|FISHING_ROD|SHEARS|SHIELD|TRIDENT|TURTLE_HELMET|ELYTRA|FLINT_AND_STEEL)"
  deny:
    - type: message
      messages:
        - "&cYou doesn't have an item in your hand."
```

In the example if below, you have a check of the item in the player’s hand. If the item matches the regex then it can open the inventory, otherwise it will receive a message and the inventory will not open.

### Click Requirement

Define multiple requirements to click on the button. You need to define several requirements and specify clicks.

You can directly use all the clicks by doing this:

```yaml
clicks:
  - ALL # or ANY
```

You can put `ALL` or `ANY` in the type of clicks to directly put all the clicks. You can manage the list of clicks that will be added in the config.json file

#### Example:

```yaml
click_requirement:
  left_click: # You must put a name for your requirement, it will not be used.
    clicks:
      - LEFT
      - SHIFT_LEFT
    requirements:
      - type: placeholder
        placeholder: "%player_gamemode%"
        value: "CREATIVE"
        action: equals_string
    deny:
      - type: sound
        sound: VILLAGER_NO
        pitch: 0.5f
        volume: 1.5f
    success:
      - type: message
        messages:
          - "&aLeft click !"
  right_click: # You must put a name for your requirement, it will not be used.
    clicks:
      - RIGHT
      - SHIFT_RIGHT
    requirements:
      - type: placeholder
        placeholder: "%player_gamemode%"
        value: "CREATIVE"
        action: equals_string
    deny:
      - type: sound
        sound: VILLAGER_NO
        pitch: 1.5f
        volume: 0.5f
    success:
      - type: message
        messages:
          - "&aRight click !"
```

## Requirements type

<table data-full-width="true"><thead><tr><th width="519">Permissible</th><th>Description</th></tr></thead><tbody><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: permission
  permission: &#x3C;permission>
</code></pre></td><td>Check if the player has permission. To reverse the need, you must put a <code>!</code> in front of the permission, like this: <code>!&#x3C;permission></code></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: placeholder
  placeholder: &#x3C;placeholder>
  value: &#x3C;placeholder value>
  action: &#x3C;placeholder action>
  target: &#x3C;player / placeholder with player name>
</code></pre></td><td>Allows you to define a permission using a placeholder. You must specify the placeholder, the action to be performed with the value, and the value that will be checked. More information <a href="./#placeholder">here</a>.<br>You can specify a player, otherwise the player who opens the inventory will be used.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: regex
  regex: &#x3C;regex>
  input: &#x3C;placeholder>
</code></pre></td><td><p>Checks if the regex matches the input. The input can be a placeholder.</p><p>Visit <a href="https://regexr.com/">regexr.com</a> for create your regex.</p></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: item
  material: &#x3C;material>
  amount: &#x3C;amount of item>
  modelId: &#x3C;model id> # default 0
</code></pre></td><td>Check if the player has an item in his inventory.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: job
  job: &#x3C;job name>
</code></pre></td><td>Allows to check if the player has the job. Works with <a href="https://www.spigotmc.org/resources/jobs-reborn.4216/">JobReborn</a> plugin.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: luckperm
  group: &#x3C;group name>
</code></pre></td><td>Allows to check if the player is in a group. Works with <a href="https://www.spigotmc.org/resources/luckperms.28140/">LuckPerms</a> plugin.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: playername
  playerName: &#x3C;placeholder>
</code></pre></td><td>Allows to check if a placeholder returns a text that can be a player nickname.</td></tr></tbody></table>

