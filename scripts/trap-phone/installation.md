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

| Resource                                                | Install  | Description                     |
| ------------------------------------------------------- | -------- | ------------------------------- |
| [ox\_lib](https://github.com/overextended/ox_lib)       | Required | callbacks,notifications         |
| [ox\_target](https://github.com/overextended/ox_target) | optional | can be changed in unlocked file |

### 1 - Start

```
1. Download your resource from FiveM's Keymaster.
2. Unzip fs_trapphone.zip folder and place it into your resource folder.
```

### 2 - Items

{% tabs %}
{% tab title="Default ESX" %}

<pre class="language-sql"><code class="lang-sql"><strong>-- Run Sql by selecting ur database
</strong><strong>UPDATE INTO `items` (`name`, `label`, `weight`) VALUES
</strong>	('fs_trapphone', 'Trap Phone', 30)
;
</code></pre>

{% endtab %}

{% tab title="Default QBCore" %}

```lua
-- add item into qb_core items file under last item

['fs_trapphone'] = {
    ['name'] = 'fs_trapphone',
    ['label'] = 'Trap Phone',
    ['weight'] = 100,
    ['type'] = 'item',
    ['image'] = 'fs_trapphone.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Secure Phone for Drug sell'
}
```

{% endtab %}

{% tab title="Ox\_Inventory" %}

```lua
-- add item into ox_inventory/shared/items.lua under last item

["fs_trapphone"] = {
		label = "Trap Phone",
		weight = 30,
		stack = true,
		close = true,
		description = 'Secure Phone for Drug sell'
	},
```

{% endtab %}

{% tab title="qs inventory" %}

```lua
-- add item into ur inventory at the bottom of ur last added item

['fs_trapphone'] = {
    ['name'] = 'fs_trapphone',
    ['label'] = 'Trap Phone',
    ['weight'] = 100,
    ['type'] = 'item',
    ['image'] = 'fs_trapphone.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Secure Phone for Drug sell'
}
```

{% endtab %}
{% endtabs %}

### 3 - Configuration

```
* You must go through all configuration options & settings in shared/config.lua
```

### 4 - Logs

```
* You must setup webhook in discord and put webhook in shared/webhooks.lua file
```

### 5 - Ready

Congratulations, you've successfully installed the resource. Restart the server and you will be all set.
