# Update Bridge

Use this guide when you want to update Bridge safely without losing your current setup.

## Recommended Update Flow

1. make a backup of your current `fs_bridge`
2. create a `.zip` backup so you can restore it quickly if the new version does not work correctly
3. download a fresh copy of the new Bridge version
4. drag and drop the fresh version into your server

## Important Backup Note

Before replacing Bridge, keep a full backup of your current resource.

That way, if the new version causes problems on your server, you can restore the previous working version immediately.

## Use A Fresh Copy

For updates, it is recommended to use a fresh Bridge copy instead of trying to merge old and new files manually.

This keeps the update cleaner and reduces the chance of missing changed files.

## If You Use Override Files

If you use manual compatibility code or any override snippets, replace your `unlocked` folder with your own previous `unlocked` folder after updating.

That keeps your custom manual compatibility code in place.

## Final Check

After updating:

1. restart the server
2. check Bridge output in `F8`
3. check Bridge output in the server console
4. confirm your supported resources and custom manual compatibility still work correctly
