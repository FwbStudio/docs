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
# Money As Item in Ox Inventory

## Ox\_Inventory Part:

find money item in ox\_inventory/data/items.lua which looks like this by default

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2F2cHhPkvcE8eb9hLnw95Q%2Fimage.png?alt=media&#x26;token=02c5ef1f-6ae3-4213-bebf-4346f21a056d" alt=""><figcaption></figcaption></figure>

Now Just Replace it With this&#x20;

{% code overflow="wrap" fullWidth="true" %}

```lua
-- this will make three button 1000,10000, 1000000
['money'] = {
        label = 'Money',
		buttons = {
			{
				label = "Place 1000 on Ground",
				action = function(slot)
					exports.ox_inventory:closeInventory();
                    TriggerEvent("fs_placeables:placeitemhook", "money", 1000);
				end
			},
			{
				label = "Place 10000 on Ground",
				action = function(slot)
					exports.ox_inventory:closeInventory();
                    TriggerEvent("fs_placeables:placeitemhook", "money", 10000);
				end
			},
			{
				label = "Place 1000000 on Ground",
				action = function(slot)
					exports.ox_inventory:closeInventory();
                    TriggerEvent("fs_placeables:placeitemhook", "money", 1000000);
				end
			},
		}
	},

```

{% endcode %}

## fs\_placeables Part:

this should be added under Config.Items in fs\_placeables/config.lua

```lua

 ['money'] = {
        [1000] = `prop_cash_pile_01`,
        [10000] = `prop_money_bag_01`,
        [1000000] = `prop_cash_case_01`,
    },

```
