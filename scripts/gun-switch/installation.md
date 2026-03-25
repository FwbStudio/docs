---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
---
# Installation

### **Framework**

* [ESX](https://github.com/esx-framework/esx_core)
* [QBCore](https://github.com/qbcore-framework/qb-core)

### Dependencies

| Resource                                          | Install  | Description            |
| ------------------------------------------------- | -------- | ---------------------- |
| [ox\_lib](https://github.com/overextended/ox_lib) | Required | callbacks,notification |

{% tabs %}
{% tab title="ESX Supported Inventories" %}

* [ox\_inventory](https://github.com/overextended/ox_inventory)
* [qs-inventory](https://buy.quasar-store.com/package/4770732)
  {% endtab %}

{% tab title="QBcore Supported Inventories" %}

* [ox\_inventory](https://github.com/overextended/ox_inventory)
* [qs-inventory](https://buy.quasar-store.com/package/4770732)
* [qb-inventory](https://github.com/qbcore-framework/qb-inventory)
* [ps-inventory](https://github.com/Project-Sloth/ps-inventory)
* [lj-inventory](https://github.com/loljoshie/lj-inventory)
  {% endtab %}
  {% endtabs %}

### 1 - Start

```
1. Download your resource from FiveM's Keymaster.
2. Unzip fs_switch.zip folder and place it into your resource folder.
3. Install items according to your inventory {you can copy items from below}
4. Install images that come with script in install_me_first/images folder
```

### 2 - Items

{% tabs %}
{% tab title="ox\_Inventory \[QB/ESX]" %}

```lua
-- add item into ox_inventory/shared/items.lua under last item

["fs_switch"] = {
	label = "Switch",
	weight = 1,
	stack = true,
	close = true,
	allowArmed = true,
	description = 'Switch',
},

["fs_redswitch"] = {
		label = "Red Switch",
		weight = 1,
		stack = true,
		close = true,
		allowArmed = true,
		description = 'Red Weapon Switch',
},

["fs_blueswitch"] = {
	label = "Blue Switch",
	weight = 1,
	stack = true,
	close = true,
	allowArmed = true,
	description = 'Blue Weapon Switch',
},

["fs_greenswitch"] = {
	label = "Green Switch",
	weight = 1,
	stack = true,
	close = true,
	allowArmed = true,
	description = 'Green Weapon Switch',
},

```

{% endtab %}

{% tab title="qs inventory \[ESX]" %}

```lua
-- add item into ur inventory at the bottom of ur last added item

['fs_switch']             = {
    ['name'] = 'fs_switch',
    ['label'] = 'Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_switch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

['fs_redswitch']             = {
    ['name'] = 'fs_redswitch',
    ['label'] = 'Red Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_redswitch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

['fs_blueswitch']             = {
    ['name'] = 'fs_blueswitch',
    ['label'] = 'Blue Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_blueswitch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

['fs_greenswitch']             = {
    ['name'] = 'fs_greenswitch',
    ['label'] = 'Green Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_greenswitch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

```

{% endtab %}

{% tab title="All QBCore Inventories Items" %}

```lua
-- add item into qb_core items file under last item
 
['fs_switch']             = {
    ['name'] = 'fs_switch',
    ['label'] = 'Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_switch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

['fs_redswitch']             = {
    ['name'] = 'fs_redswitch',
    ['label'] = 'Red Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_redswitch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

['fs_blueswitch']             = {
    ['name'] = 'fs_blueswitch',
    ['label'] = 'Blue Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_blueswitch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

['fs_greenswitch']             = {
    ['name'] = 'fs_greenswitch',
    ['label'] = 'Green Switch',
    ['weight'] = 50,
    ['type'] = 'item',
    ['image'] = 'fs_greenswitch.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Switch for Pistols'
},

```

{% endtab %}
{% endtabs %}

### 3 - Configuration

```
* You must go through all configuration options & settings in shared/config.lua
```

### 4 - Ready

Congratulations, you've successfully installed the resource. Restart the server and you will be all set.
