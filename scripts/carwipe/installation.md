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

| Resource                                                               | Install  | Description                |
| ---------------------------------------------------------------------- | -------- | -------------------------- |
| [ox\_lib](https://github.com/overextended/ox_lib)                      | Required | context,notifications      |
| [fs\_bridge](../fs_bridge/installation.md) | Required | callbacks and other stuffs |

### 1 - Start

```
1. Download your resource from FiveM's Keymaster.
2. Unzip fs_carwipe.zip folder and place it into your resource folder.
```

### 3 - Configuration

{% code overflow="wrap" %}

```
* You can add permanent wipe avoid zones in config filder in config file make sure don't touch config.json file otherwise it will start error

* Also you need to edit commands permissions and if you want to change command you can go into fs_carwipe/config/config.lua

* Other all Configs are inagme you can read readme file in script to understand all ingame config settings
```

{% endcode %}

### 5 - Ready

Congratulations, you've successfully installed the resource. Restart the server and you will be all set.
