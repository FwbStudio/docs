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

Before installing, check the [Compatibility](compatibility.md) page to confirm your framework, inventory, and zone engine are supported.

## Framework

Safezone Creator supports the following frameworks:

* `ESX`
* `QBCore`
* `Qbox`

Make sure your server is already running one of the supported frameworks before continuing.

## Dependencies

Install the following dependencies before setting up Safezone Creator:

| Resource | Install | Description |
| --- | --- | --- |
| [ox\_lib](https://github.com/overextended/ox_lib) | Required | UI helpers and zone handling |
| [oxmysql](https://github.com/overextended/oxmysql) | Required | Database storage for safezones and runtime settings |
| [PolyZone](https://github.com/mkafrin/PolyZone) | Optional | Optional replacement / fallback for `ox_lib` zone handling |

Safezone Creator already includes its own internal bridge files for frameworks, inventories, notifications, and zone handling. You do not need to install `fs_bridge` separately for this resource.

## 1. Download

Download the resource from the Cfx Portal / Keymaster linked to your purchase.

## 2. Extract The Files

Use WinRAR or another archive tool to unzip the downloaded file.

After extracting it, make sure the resource folder is named `fs_safezonecreator`.

## 3. Place It In Your Resources

Go to your server resources directory.

If you do not already have an `[fs]` folder inside `resources`, create one.

Then move `fs_safezonecreator` into that `[fs]` folder.

Example structure:
`resources` -> `[fs]` -> `fs_safezonecreator`

## 4. Check Dependency Order

Make sure your dependencies are already installed and started before Safezone Creator.

This is especially important for:

* `ox_lib`
* `oxmysql`

## 5. Update server.cfg

Open your `server.cfg`.

Near the bottom of the file, make sure your FS resources are started last.

If you use folder-based ensures, place `ensure [fs]` at the bottom.

This allows the server to start all resources inside your `[fs]` folder, including `fs_safezonecreator`.

If you do not use folder-based ensures, then make sure `fs_safezonecreator` is ensured after its required dependencies.

## 6. Restart The Server

Restart your server after adding the resource and updating `server.cfg`.

This allows the framework, internal bridge layer, database, and Safezone Creator resource to load in the correct order.

## 7. Open The In-Game Menu
This resource is configured in-game.

Open the in-game admin menu with `/safezonemenu`.

After opening the menu, follow the in-game setup flow to configure:

* safezones
* permissions
* built-in bridge options
* notifications
* logs
* icons and blips
* debug settings

Weapon whitelist settings and safezone behavior can also be managed from the same setup flow.

## 8. Ready

Once the menu opens correctly, the resource is installed and ready to use.
