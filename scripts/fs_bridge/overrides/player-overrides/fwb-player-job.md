# FWB.Player.Job

This namespace is part of the normal public player API.

In the current bridge build, job lookups are handled by the built-in framework layer. Most servers do not need unlocked override code for this namespace.

## Public Calls

Client:

```lua
FWB.Player.Job.Name()
FWB.Player.Job.Label()
FWB.Player.Job.GradeLabel()
FWB.Player.Job.GradeLevel()
FWB.Player.Job.Data()
```

Server:

```lua
FWB.Player.Job.Data(source)
FWB.Player.Job.Name(source)
FWB.Player.Job.GradeLevel(source)
FWB.Player.Job.Set(source, jobName, grade)
FWB.Player.ToggleDuty(source)
FWB.Player.IsOnDuty(source)
FWB.Player.IsBoss(source)
FWB.Job.PlayerCount(jobName)
```

<details>
<summary><strong>Read Current Job State</strong></summary>

Short description: Read the active job, labels, and grade details from the active framework.

Signature:

```lua
FWB.Player.Job.Name()
FWB.Player.Job.Label()
FWB.Player.Job.GradeLabel()
FWB.Player.Job.GradeLevel()
FWB.Player.Job.Data()
```

Arguments:

- none on client

Returns:

- string job name
- string labels
- numeric grade level
- job data table

Override code:

```lua
-- No unlocked override block is normally required here.
-- This namespace is backed by the active framework adapter.
```

Example usage:

```lua
local jobName = FWB.Player.Job.Name()
local grade = FWB.Player.Job.GradeLevel()
```

Notes:

- use this page as the public reference for job reads
- use supported framework config before considering deeper customization

</details>

<details>
<summary><strong>Set Job And Duty State</strong></summary>

Short description: Update a player's job or toggle their duty state on the server.

Signature:

```lua
FWB.Player.Job.Set(source, jobName, grade)
FWB.Player.ToggleDuty(source)
FWB.Player.IsOnDuty(source)
FWB.Player.IsBoss(source)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Player source |
| `jobName` | `string` | For set only | Job name |
| `grade` | `number` | For set only | Grade level |

Returns:

- framework-dependent success or job-state result

Override code:

```lua
-- No unlocked override block is documented for job write helpers at this time.
-- Use the built-in framework support for ESX, QBCore, or VORP.
```

Example usage:

```lua
FWB.Player.Job.Set(source, 'police', 2)
local onDuty = FWB.Player.IsOnDuty(source)
```

Notes:

- if your framework is fully custom, treat this namespace as framework-level customization work, not a normal unlocked-file override

</details>

<details>
<summary><strong>Count Players By Job</strong></summary>

Short description: Count online players inside a job.

Signature:

```lua
FWB.Job.PlayerCount(jobName)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `jobName` | `string` | Yes | Job to count |

Returns:

- `number`

Override code:

```lua
-- No unlocked override block is documented for this helper.
```

Example usage:

```lua
local policeOnline = FWB.Job.PlayerCount('police')
```

Notes:

- useful for gating robberies, alerts, and services

</details>
