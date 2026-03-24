# Basic Server Knowledge

This page covers the basic setup habits that help most FiveM resources work correctly.

## 1. Keep Your Resource Folders Organized

Use clear resource groups in your `resources` folder so startup order is easier to read and maintain.

Example:

```text
resources/
|-- [framework]
|-- [standalone]
`-- [fs]
```

For Beta resources, it is recommended to keep related scripts together inside `[fs]`.

## 2. Understand `server.cfg` Start Order

Resources should start in dependency order.

That means:

- `oxmysql` first
- your framework before dependent scripts
- required integrations before the scripts that detect them
- Bridge after the resources it needs to detect

If the start order is wrong, detection issues are very common.

## 3. Edit Config Files With A Proper Code Editor

Use a code editor such as Visual Studio Code, Notepad++, or another editor that keeps formatting clean.

Avoid editing Lua config files in tools that may break formatting or save with strange encoding.

## 4. Restart After Important Changes

When changing framework setup, integrations, or escrowed files, a full server restart is usually safer than only restarting one resource.

This helps refresh detection and avoids stale state from previous starts.

## 5. Import SQL Only When A Resource Includes It

If a script includes `.sql` files, import them into your server database before starting the resource.

General flow:

1. open your database tool
2. select your server database
3. open a query tab
4. paste the SQL file contents
5. execute the query once

## 6. Always Check Both Client And Server Logs

When testing a resource:

- check `F8` for client-side output
- check the server console for server-side output

Looking at only one side can hide the real problem.
