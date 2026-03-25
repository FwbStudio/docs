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

<table><thead><tr><th>Resource</th><th>Install</th><th>Framework</th><th data-hidden>Link</th></tr></thead><tbody><tr><td>ox_lib</td><td>required</td><td>ESX/QB</td><td><a href="https://github.com/overextended/ox_lib">https://github.com/overextended/ox_lib</a></td></tr><tr><td>Bridge</td><td>required</td><td>ESX/QB</td><td></td></tr></tbody></table>

### Note:

Useable food never work alone what ever foods are added in this script are used by our other food business scripts or any food mlo or food truck scripts please make sure to install food business if you want to use foods this is just a dependecy of our food scripts.\
\
If You still want to use this script for your own food then you have to add item in your server what ever you make and and prop related to that food in useable foods.

### Inventories Installation:

{% tabs %}
{% tab title="ox\_Inventory" %}

* **Step 1:**\
  Install all following items into ox\_inventory/data/items.lua.

```lua
["fs_drunktester"] = {
    label = "Drunk Tester",
    weight = 1,
    stack = true,
    close = true,
},
```

* Step 2:

Drag fs\_useablefoods into your resource folder and ensure it after ox\_lib.

* Step 3:

install any food business which you like
{% endtab %}

{% tab title="ak47\_Inventory" %}

* **Step 1:**\
  Install all following items into ak47\_inventory/shared/items.lua.

{% code fullWidth="true" %}

```lua
["fs_drunktester"] = {
    name = "fs_drunktester",
    label = "Drunk Tester",
    weight = 1,
    type = "item",
    close = true,
},
```

{% endcode %}

* Step 2:

Go in ak47\_inventory/configs/config.lua

Find this:<br>

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2FbVgctZiOIAbSTnO40VsB%2FScreenshot%202024-10-02%20092938.png?alt=media&#x26;token=67ac2456-aa7a-40f0-aa1e-6f283d7c0316" alt=""><figcaption></figcaption></figure>

and add these lines at last <br>

{% code fullWidth="true" %}

```lua
    -- fs_useablefoods
    Bite = true,
    Sip = true,
    Expiry = true
```

{% endcode %}

Finally It will Look Like:<br>

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2FPwaZXInk7D3TQ0TKwcXm%2FScreenshot%202024-10-02%20093058.png?alt=media&#x26;token=c985b521-98ab-45aa-a077-5de1a26a0064" alt=""><figcaption></figcaption></figure>

* Step 3:

Drag fs\_useablefoods into your resource folder and ensure it after ox\_lib.

* Step 4:

install any food business which you like
{% endtab %}

{% tab title="qs\_Inventory" %}

* **Step 1:**\
  Install all following items into qs\_inventory/shared/items.lua.

{% code fullWidth="true" %}

```lua
fs_drunktester = {  
    name = "fs_drunktester", 
    label = "Drunk Tester", 
    weight = 10, 
    type = 'item', 
    image = 'fs_drunktester.png', 
    unique = true, 
    useable = true, 
    shouldClose = true, 
    combinable = nil, 
    description = "This is description." 
},
```

{% endcode %}

* Step 2:

Go in qs\_inventory/configs/metadata.js

Find this: {see if your version has it or not}\ <br>

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2FAAVk6Oq5BBQ07yKwSW6c%2FScreenshot%202024-10-02%20094553.png?alt=media&#x26;token=37b92d79-2d82-4d79-81f7-7fec9dc7b60a" alt=""><figcaption></figcaption></figure>

if your are not able to find it then please at this at end of file&#x20;

```javascript
const tableToString = (data) => {
    let table = '<table class="table table-striped table-dark">';
    for (const [key, value] of Object.entries(data)) {
        table += `<tr><td>${key}</td><td>${value}</td></tr>`;
    }
    table += '</table>';
    return table;
}
```

Finally it will look like this :<br>

\-- if you not feeling fine to pasting then please contact qs inventory discord to ask this code by default its missing in inventory files.

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2F8VWMhyv87HCOjWLLHltH%2FScreenshot%202024-10-02%20094553.png?alt=media&#x26;token=7cf43016-9d32-4d3e-b509-8522e4a5d776" alt=""><figcaption></figcaption></figure>

* Step 3:

Drag fs\_useablefoods into your resource folder and ensure it after ox\_lib.

* Step 4:

install any food business which you like
{% endtab %}

{% tab title="New qb-Inventory" %}

* **Step 1:**\
  Install all following items into qb-inventory/data/items.lua.

{% code fullWidth="true" %}

```lua
fs_drunktester = {  
    name = "fs_drunktester", 
    label = "Drunk Tester", 
    weight = 10, 
    type = 'item', 
    image = 'fs_drunktester.png', 
    unique = true, 
    useable = true, 
    shouldClose = true, 
    combinable = nil, 
    description = "This is description." 
},
```

{% endcode %}

* Step 2:

Drag fs\_useablefoods into your resource folder and ensure it after ox\_lib.

* Step 3:

install any food business which you like
{% endtab %}

{% tab title="Old qb\_inventory" %}

* **Step 1:**\
  Install all following items into qb-inventory/data/items.lua.

{% code fullWidth="true" %}

```lua
fs_drunktester = {  
    name = "fs_drunktester", 
    label = "Drunk Tester", 
    weight = 10, 
    type = 'item', 
    image = 'fs_drunktester.png', 
    unique = true, 
    useable = true, 
    shouldClose = true, 
    combinable = nil, 
    description = "This is description." 
},
```

{% endcode %}

* Step 2:

Go in qb-inventory/html/app.js and go on line 398 or find this

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2FlcSzpgw8QyWfFKjbDqXC%2Fimage.png?alt=media&#x26;token=57e6b79b-4a65-4bee-b7af-48eca55188b6" alt=""><figcaption></figcaption></figure>

Replace 398 line with this it with this :&#x20;

```javascript
let itemDescr = itemData.info.description || itemData.description;
```

**Finally It will look like this :**

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2Fwgf64vb8f7Rte5vmUCxP%2Fimage.png?alt=media&#x26;token=00b5e4a0-1d4b-4354-bbc5-f3b22a217356" alt=""><figcaption></figcaption></figure>

* Step 3:

Drag fs\_useablefoods into your resource folder and ensure it after ox\_lib.

* Step 4:

install any food business which you like
{% endtab %}
{% endtabs %}
