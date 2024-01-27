# Requirements

Les requirements vous permettront d’effectuer des actions basées sur une vérification d’autorisation.

## Requirements

### Syntax

```yaml
# open_requirement
# click_requirement
view_requirement:

  # Définissez le nombre minimum de requirement pour pouvoir dire que c’est un succès.
  # Par défaut, la valeur sera la même que le nombre de requirements.
  miniumRequirement: <number>
  
  # Liste des requirements, toutes les informations sur chaque type ci-dessous
  requirements:
    - type: permission
      permission: "example.permission"
    - type: placeholder
      placeholder: "%player_gamemode%" # Besoin du PAPI ecloud Player
      value: "CREATIVE"
      action: equals_string
      deny:
        - type: message
          messages:
            - "&cVous devez être en créatif !"            
    - type: regex
      input: "%player_item_in_hand%" # Besoin du PAPI ecloud Player
      regex: "(NETHERITE_|DIAMOND_|IRON_|GOLDEN_|STONE_|WOODEN_|LEATHER_|BOW|CROSSBOW|FISHING_ROD|SHEARS|SHIELD|TRIDENT|TURTLE_HELMET|ELYTRA|FLINT_AND_STEEL)"      
      deny:
        - type: message
          messages:
            - "&cVous n'avez pas d'item dans votre main !"      
  
  # Actions réussies
  success:
    - type: sound
      sound: ENTITY_PLAYER_LEVELUP
      
  # Action en cas d'échec
  deny:    
    - type: message
      messages:
        - "&cYou doesn't have an item in your hand."
```

En plus des actions de deny et de success globale, vous pouvez définir des actions de deny et de success pour chaque requirements.

### View Requirement

Définissez les requirements pour afficher un bouton dans l’inventaire.

#### Exemple:

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

Définir les requirements pour ouvrir l’inventaire.

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

Dans l’exemple ci-dessous, vous avez un contrôle de l’objet dans la main du joueur. Si l’article correspond au regex, il peut ouvrir l’inventaire, sinon il recevra un message et l’inventaire ne s’ouvrira pas.

### Click Requirement

Définissez plusieurs requirements pour cliquer sur le bouton. Vous devez définir plusieurs exigences et spécifier les clics.

Vous pouvez utiliser directement tous les clics en faisant ceci :

```yaml
clicks:
  - ALL # ou ANY
```

Vous pouvez mettre `ALL` ou `ANY` dans clicks pour mettre directement tous les clics. Vous pouvez gérer la liste des clics qui seront ajoutés dans le fichier config.json.

#### Example:

```yaml
click_requirement:
  left_click: # Vous devez mettre un nom pour votre requirement, il ne sera pas utilisé.
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
  right_click: # Vous devez mettre un nom pour votre requirement, il ne sera pas utilisé.
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
</code></pre></td><td>Vérifiez si le joueur a la permission. Pour inverser le besoin, vous devez mettre un <code>!</code> devant la permission, comme ceci : <code>!&#x3C;permission></code></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: placeholder
  placeholder: &#x3C;placeholder>
  value: &#x3C;placeholder value>
  action: &#x3C;placeholder action>
</code></pre></td><td>Permet de définir une autorisation à l’aide d’un espace réservé. Vous devez spécifier l’espace réservé, l’action à effectuer avec la valeur et la valeur qui sera vérifiée. Plus d’informations <a href="./#placeholder">ici</a>.</td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: regex
  regex: &#x3C;regex>
  input: &#x3C;placeholder>
</code></pre></td><td><p>Vérifie si la regex correspond à l’entrée. L’entrée peut être un espace réservé.</p><p>Allez sur <a href="https://regexr.com/">regexr.com</a> pour créer votre regex.</p></td></tr><tr><td><pre class="language-yaml"><code class="lang-yaml">- type: item
  material: &#x3C;material>
  amount: &#x3C;amount of item>
</code></pre></td><td>Vérifiez si le joueur a un objet dans son inventaire.</td></tr></tbody></table>

