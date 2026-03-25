# FWB.Player.Job

`FWB.Player.Job` is the client-side job namespace for reading the local player's current job name, labels, grade details, and normalized job data.

## Public Calls

```lua
FWB.Player.Job.Name()
FWB.Player.Job.Label()
FWB.Player.Job.GradeLabel()
FWB.Player.Job.GradeLevel()
FWB.Player.Job.Data()
```

<details>
<summary><strong>Read Job Name And Labels</strong></summary>

Short description: Read the current local player job name and display labels.

Signature:

```lua
FWB.Player.Job.Name()
FWB.Player.Job.Label()
FWB.Player.Job.GradeLabel()

exports.fs_bridge:GetPlayerJob()
exports.fs_bridge:GetPlayerJobLabel()
exports.fs_bridge:GetPlayerJobGradeLabel()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Job.Name()` | none | Internal job name such as `police` |
| `FWB.Player.Job.Label()` | none | Display label such as `Police` |
| `FWB.Player.Job.GradeLabel()` | none | Current grade label or grade name |

Returns:

- `string` or `nil`

Example usage:

```lua
local jobName = FWB.Player.Job.Name()
local jobLabel = FWB.Player.Job.Label()
local gradeLabel = FWB.Player.Job.GradeLabel()

print(jobName, jobLabel, gradeLabel)
```

Notes:

- values come from the active framework player data
- `GradeLabel()` reflects ESX or QBCore/Qbox naming for the active framework

</details>

<details>
<summary><strong>Read Job Grade Level</strong></summary>

Short description: Read the numeric grade level of the local player's current job.

Signature:

```lua
FWB.Player.Job.GradeLevel()
exports.fs_bridge:GetPlayerJobGradeLevel()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Job.GradeLevel()` | none | Returns the current grade level |

Returns:

- `number` or `nil`

Example usage:

```lua
local gradeLevel = FWB.Player.Job.GradeLevel()

if gradeLevel and gradeLevel >= 3 then
    print('High enough grade')
end
```

Notes:

- QBCore and Qbox return the grade level from the nested job grade structure

</details>

<details>
<summary><strong>Read Normalized Job Data</strong></summary>

Short description: Read the Bridge-normalized job data table for the local player.

Signature:

```lua
FWB.Player.Job.Data()
exports.fs_bridge:GetPlayerJobData()
```

Arguments:

| Call | Arguments | Notes |
|---|---|---|
| `FWB.Player.Job.Data()` | none | Returns a normalized job table |

Returns:

- job data table

Example usage:

```lua
local job = FWB.Player.Job.Data()

if job then
    print(job.name, job.label, job.gradeLevel)
end
```

Notes:

- use this when you want one normalized job object instead of reading individual fields

</details>
