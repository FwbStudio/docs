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

# Update Bridge

Use this guide when you want to update Bridge safely without losing your current setup.

## 🗂 Back Up Your Current Bridge

Before anything else, make a full backup of your current `fs_bridge` resource.

This gives you a safe restore point if the new version does not work correctly on your server.

## 📦 Keep A Zip Copy

It is also recommended to create a `.zip` backup of your current Bridge before replacing it.

A zipped backup is faster to store, easier to move, and easier to restore if you need to roll back quickly.

## ⬇️ Use A Fresh Copy

Download a fresh copy of the new Bridge version and drag it into your server instead of trying to merge old and new files manually.

A clean replacement keeps the update process simpler and reduces the chance of missing changed files.

## 🧩 Restore Your Custom Files

If you use manual compatibility code or override snippets, replace the fresh `unlocked` folder with your own previous `unlocked` folder after the update.

That keeps your custom compatibility code in place.

## ✅ Check Everything After Updating

After the update:

1. restart the server
2. check Bridge output in `F8`
3. check Bridge output in the server console
4. confirm your supported resources still detect correctly
5. confirm your manual compatibility still works if you use it