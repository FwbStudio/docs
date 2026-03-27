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
# Version

This page documents the public version helpers.

## Public Calls

Shared names:

```lua
FWB.GetResourceServerVersion(resource)
FWB.GetResourceServerVersionString(resource)
```

Server-only names:

```lua
FWB.GetResourceGithubVersion(resource)
FWB.GetResourceGithubVersionString(resource)
FWB.HasLatestVersion(resource)
```

## Notes

- `GetResourceServerVersion(resource)` returns a numeric version value from resource metadata.
- `GetResourceServerVersionString(resource)` returns the raw version string from metadata.
- GitHub version helpers are server-side and compare against the latest FwbStudio release.
- `HasLatestVersion(resource)` returns `true` when the installed version is current.

## Example

```lua
print(FWB.GetResourceServerVersionString('fs_bridge'))

if IsDuplicityVersion() then
    print(FWB.GetResourceGithubVersionString('fs_bridge'))
    print(FWB.HasLatestVersion('fs_bridge'))
end
```

