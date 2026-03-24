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

# &#9888; Common Errors

Below you'll find the most common Bridge-related errors and what they usually mean.

Click an error to expand it.

* * *

<details>
<summary><strong>Bridge keeps spamming "waiting to start load properly"</strong></summary>

This usually means Bridge is waiting for the framework you selected, but that framework is not the correct one for your server setup.

Make sure:

- you purchased or installed the correct framework version
- the Bridge framework matches your server
- your server is actually using `ESX`, `QBCore`, or `Qbox` as expected

If the wrong framework version is installed, Bridge can keep waiting for something that never loads.

</details>

<details>
<summary><strong>I have the items, but the console says they were not found in ESX, QBCore, or Qbox</strong></summary>

This usually means your installation order is wrong and Bridge did not detect your inventory correctly.

Check these first:

- make sure your supported inventory starts before `fs_bridge`
- make sure your <mark style="color:#f0fdf4;background-color:#166534;">[fs]</mark> group is near the bottom of <mark style="color:#f0fdf4;background-color:#166534;">server.cfg</mark>
- make sure `fs_bridge` is ensured last
- restart the full server after changing the order

If Bridge does not detect the correct inventory, item checks can fail even when the items exist.

</details>

<details>
<summary><strong>The console says an export was not found in <code>esx_skin</code>, <code>qb_skin</code>, or a clothing resource</strong></summary>

This usually means Bridge was not ensured last and could not detect the clothing resource correctly.

Check these first:

- make sure your clothing resource starts before `fs_bridge`
- make sure `fs_bridge` is ensured last
- restart the full server after changing the order

If Bridge starts too early, it may try to use exports before the supported clothing resource is available.

</details>

<details>
<summary><strong>The console says "attempt to index a nil value"</strong></summary>

If this happens right after uploading or starting an escrowed resource, it usually points to an escrow upload problem.

Recommended fix:

1. re-upload the resource using `WinSCP`
2. avoid tools that may damage escrowed files during upload
3. restart the server after uploading again

If the escrowed files were corrupted during transfer, Bridge or the connected resource may fail with nil-value errors.

</details>
