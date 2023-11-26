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
    - type: placeholder
      placeholder: "%player_gamemode%" # need PAPI ecloud Player
      value: "CREATIVE"
      action: equals_string
    - type: regex
      input: "%player_item_in_hand%" # need PAPI ecloud Player
      regex: "(NETHERITE_|DIAMOND_|IRON_|GOLDEN_|STONE_|WOODEN_|LEATHER_|BOW|CROSSBOW|FISHING_ROD|SHEARS|SHIELD|TRIDENT|TURTLE_HELMET|ELYTRA|FLINT_AND_STEEL)"      
  
  # Success actions
  success:
    - type: sound
      sound: ENTITY_PLAYER_LEVELUP
      
  # Deny
  deny:    
    - type: message
      messages:
        - "&cYou doesn't have an item in your hand."
```

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
</code></pre></td><td>Allows you to define a permission using a placeholder. You must specify the placeholder, the action to be performed with the value, and the value that will be checked. More information <a href="./#placeholder">here</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: regex
  regex: &#x3C;regex>
  input: &#x3C;placeholder>
</code></pre></td><td><p>Checks if the regex matches the input. The input can be a placeholder.</p><p>Visit <a href="https://regexr.com/">regexr.com</a> for create your regex.</p></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: item
  material: &#x3C;material>
  amount: &#x3C;amount of item>
</code></pre></td><td>Check if the player has an item in his inventory.</td></tr></tbody></table>

