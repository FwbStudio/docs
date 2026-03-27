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
# Server

This page documents the public server-side hacker helpers.

## FWB.Hacker

### Moderation

<details>
<summary><strong>Kick Player</strong></summary>

Short description: Kick a player through the active Bridge kick flow.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `reason` | `string` | Kick reason. Defaults to `You have been Kicked from the server.` |

Returns:

- compatibility-specific result
- `nil`

How to write it as function:

```lua
FWB.Hacker.Kick(source, reason)
```

How to write it as export:

```lua
exports['fs_bridge']:KickPlayer(source, reason)
```

Example as function:

```lua
FWB.Hacker.Kick(source, 'Exploit detected')
```

Example as export:

```lua
exports['fs_bridge']:KickPlayer(source, 'Exploit detected')
```

</details>

<details>
<summary><strong>Ban Player</strong></summary>

Short description: Ban a player through the active Bridge ban flow.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `source` | `number` | Target player source |
| `reason` | `string` | Ban reason. Defaults to `You have been Banned from the server.` |

Returns:

- compatibility-specific result
- `false` when no ban integration is configured

How to write it as function:

```lua
FWB.Hacker.Ban(source, reason)
```

How to write it as export:

```lua
exports['fs_bridge']:Ban(source, reason)
```

Example as function:

```lua
FWB.Hacker.Ban(source, 'Exploit detected')
```

Example as export:

```lua
exports['fs_bridge']:Ban(source, 'Exploit detected')
```

</details>
