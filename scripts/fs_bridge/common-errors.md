# Common Errors

This page covers the most common Bridge setup mistakes.

## Bridge Does Not Detect My Resources

Check these first:

1. Make sure the supported resources you want Bridge to detect start before `fs_bridge`
2. Make sure `selected_key = 1` is still used if you want auto-detect
3. Make sure the resource names match the supported names exactly
4. Restart the whole server after changing start order

## Bridge Starts Too Early

Bridge should not start before:

- `es_extended` or `qb-core`
- supported resources it needs to read from, such as target, inventory, dispatch, phone, or fuel systems

If Bridge starts too early, detection can fail.

## My Own Script Cannot Use Bridge On Startup

If your own resource calls Bridge during startup, it must start after `fs_bridge`.

Typical order:

```text
framework
supported resources
fs_bridge
your own Bridge-based resources
```

## Resource Placement Is Wrong

Recommended placement:

```text
resources/[fs]/fs_bridge
```

This keeps your Bridge and related resources grouped cleanly.

## Bridge In `server.cfg`

For normal setups, keep Bridge near the end of the resources it needs to detect, not before them.

Good rule:

- framework first
- supported integrations next
- `fs_bridge` after them
- your own Bridge-dependent scripts after `fs_bridge`

## Wrong Framework Branch In Config

Open `config/sh_config.lua` and make sure the framework section matches your server:

- `ESX`
- `QBCore`

If the wrong branch is being used, job and player functions may not behave correctly.

## I Edited Locked Files

For normal setups, do not edit locked Bridge files.

Use:

- `config/sh_config.lua`
- `unlocked/client.lua`
- `unlocked/server.lua`

## My Custom Script Is Not Supported

That does not always mean Bridge is broken.

If your script is unsupported:

1. keep the supported config clean
2. use the override pages
3. paste custom logic into unlocked files only
