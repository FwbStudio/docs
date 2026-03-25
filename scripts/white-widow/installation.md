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

| Resource                                                                                                      | Install  | Description                              |
| ------------------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------- |
| [ox\_lib](https://github.com/overextended/ox_lib)                                                             | Required | callbacks,notifications                  |
| [fs\_placeables](../item-placeables/installation.md) | Required | Drag and Drop {for place item on ground} |
| [fs\_smoking](../smoking/installation.md)       | Required | Drag and Drop {for smoking items}        |

### 1 - Start

```
1. Download your resource from FiveM's Keymaster.
2. Unzip fs_whitewidow.zip folder and place it into your resource folder.
```

### 2 - Items

{% code overflow="wrap" %}

```
All items are in install me file we recommened use of ox inventory but incase if you don't use ox inventory then u can enable placeable menu to place all items.
```

{% endcode %}

### 3 - Job

```
job file is in install_me_first run sql to install job
```

### 3 - Configuration

{% code overflow="wrap" %}

```
* You must go through all configuration options & settings in all config files
* you can start any script in any arrangement just make sure to add ox lib before all resources 

* Best order of ensure is 

ensure ox_lib

ensure fs_placeables
ensure fs_smoking
ensure fs_whitewidow

if you restart any of script then some issues can be accur but make sure to restart whole server after confiuration 
```

{% endcode %}

### 4 - Ready

Congratulations, you've successfully installed the resource. Restart the server and you will be all set.
