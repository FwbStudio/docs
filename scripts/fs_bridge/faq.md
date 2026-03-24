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

# ❓ FAQ

Below you'll find answers to the most common Bridge setup and usage questions.

Click a question to expand it.

***

<details>

<summary><strong>Do I need to edit locked Bridge files?</strong></summary>

No. A normal public setup should use:

* `config/sh_config.lua`
* `unlocked/client.lua`
* `unlocked/server.lua`

Locked Bridge files should be left unchanged in normal installs.

</details>

<details>

<summary><strong>Should I keep supported selectors on 1?</strong></summary>

Yes. `1` is the recommended default because it lets Bridge auto-detect supported resources.

Only switch to a manual option if a support team member tells you to.

</details>

<details>

<summary><strong>When do I need to write an override?</strong></summary>

Use an override when:

* your resource is unsupported
* auto-detect cannot resolve your setup
* you need custom integration behavior

</details>

<details>

<summary><strong>When do I not need an override?</strong></summary>

If your resource is already supported and Bridge works correctly through config and auto-detect, you normally do not need an override.

</details>

<details>

<summary><strong>Where do I paste override snippets?</strong></summary>

Client override snippets go in `unlocked/client.lua`.

Server override snippets go in `unlocked/server.lua`.

</details>

<details>

<summary><strong>How do I check what Bridge detected?</strong></summary>

Restart the server and review Bridge output in `F8` and the server console.

You can also use:

* `/fs_bridge_c` for client-side detection
* `fs_bridge_s` for server-side detection

</details>

<details>

<summary><strong>What frameworks are currently covered in the public docs?</strong></summary>

The current public docs focus on:

* `ESX`
* `QBCore`
* `Qbox`

</details>

<details>

<summary><strong>What should my own scripts use?</strong></summary>

Use the public APIs and namespaces, such as:

* `FWB.Player.Job.Name()`
* `FWB.Blip.Create(options)`
* `FWB.Ped.Create(options)`
* `FWB.Vehicle.Create(...)`
* `FWB.Entity.Vehicle.Closest(extras)`

For unsupported systems, use overrides instead of editing locked files.

</details>
