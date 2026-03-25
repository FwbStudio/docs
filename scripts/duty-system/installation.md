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

### 1 - Start

```
1. Download your resource from FiveM's Keymaster.
2. Unzip fs_dutysystem.zip folder and place it into your resource folder.
3. Install off duty jobs if ur using ESX. for Qbcore it uses framework duty system
```

### 2 - SQL

{% tabs %}
{% tab title="Off Police ESX" %}

```sql

INSERT INTO `addon_account` (name, label, shared) VALUES
	('society_offpolice', 'Off Police', 1)
;

INSERT INTO `datastore` (name, label, shared) VALUES
	('society_offpolice', 'Off Police', 1)
;

INSERT INTO `addon_inventory` (name, label, shared) VALUES
	('society_offpolice', 'Off Police', 1)
;

INSERT INTO `jobs` (name, label) VALUES
	('offpolice', 'Off Police')
;

INSERT INTO `job_grades` (job_name, grade, name, label, salary, skin_male, skin_female) VALUES
	('offpolice',0,'recruit','Recruit',20,'{}','{}'),
	('offpolice',1,'officer','Officer',40,'{}','{}'),
	('offpolice',2,'sergeant','Sergeant',60,'{}','{}'),
	('offpolice',3,'lieutenant','Lieutenant',85,'{}','{}'),
	('offpolice',4,'boss','Chief',100,'{}','{}')
;

```

{% endtab %}

{% tab title="Off Ambulance  ESX" %}

````lua
INSERT INTO `addon_account` (name, label, shared) VALUES
	('society_offambulance', 'Off Ambulance', 1)
;

INSERT INTO `datastore` (name, label, shared) VALUES
	('society_offambulance', 'Off Ambulance', 1)
;

INSERT INTO `addon_inventory` (name, label, shared) VALUES
	('society_offambulance', 'Off Ambulance', 1)
;

INSERT INTO `jobs` (name, label) VALUES
	('offambulance', 'Off Ambulance')
;

INSERT INTO `job_grades` (job_name, grade, name, label, salary, skin_male, skin_female) VALUES
	('offambulance',0,'ambulance','Paramedic',20,'{}','{}'),
	('offambulance',1,'doctor','Doctor',40,'{}','{}'),
	('offambulance',2,'chief_doctor','Chief Doctor',60,'{}','{}'),
	('offambulance',3,'boss','Director',85,'{}','{}')
;

```
````

{% endtab %}

{% tab title="ALL QB Jobs" %}

```lua
-- no sql need script use ingame duty system
```

{% endtab %}
{% endtabs %}

### 3 - Configuration

```
* You must go through all configuration options & settings in config/Config.lua
* Make sure to add Webhhoks to get logs in config/Webhooks.lua
```

### 4 - Ready

Congratulations, you've successfully installed the resource. Restart the server and you will be all set.
