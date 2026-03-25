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

# General Issues

This page covers common setup problems that are not limited to a single script.

## Bridge Does Not Detect A Supported Resource

Check these first:

1. make sure the supported resource starts before `fs_bridge`
2. make sure `fs_bridge` is ensured last in your `server.cfg`
3. keep selectors on `1` for auto detect unless support tells you to force a manual option
4. restart the server after changing setup order

You can then check detection output in `F8`, the server console, `/fs_bridge_c`, and `fs_bridge_s`.

## A Config Change Does Not Apply

If nothing changes after editing config files:

1. save the file correctly
2. restart the resource or restart the full server
3. confirm you edited the correct config file
4. check for syntax errors in the console

## Folder Structure Causes Confusion

A messy resource layout makes troubleshooting harder.

Recommended rule:

* keep framework resources together
* keep standalone dependencies together
* keep Beta resources together inside `[fs]`

This makes startup order and detection problems much easier to spot.

## Console Looks Fine But The Script Still Does Not Work

Some problems only appear on one side.

Always check:

* `F8` for client-side prints and errors
* server console for server-side prints and errors

If needed, test again after a full restart instead of only restarting a single resource.
