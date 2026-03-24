# FWB.Sounds

The current sound helpers are:

```lua
FWB.PlayUrlPos(source, position, distance, url, volume, loop)
FWB.Destroy(source, soundId)
FWB.GetSoundResourceName()
```

<details>
<summary><strong>Play Positional Audio</strong></summary>

Short description: Play a URL-based sound through a custom sound resource.

Signature:

```lua
Override.PlayUrlPos(source, soundId, position, distance, url, volume, loop)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Player target or `-1` |
| `soundId` | `string` | Yes | Generated bridge sound id |
| `position` | `vector3` | Yes | World position |
| `distance` | `number` | Yes | Hearing range |
| `url` | `string` | Yes | Audio URL |
| `volume` | `number` | Yes | Playback volume |
| `loop` | `boolean` | No | Loop mode |

Returns:

- resource-specific playback result

Override code:

```lua
function Override.PlayUrlPos(source, soundId, position, distance, url, volume, loop)
    return exports.my_sound:PlayAtPosition(source, soundId, url, volume, position, loop, distance)
end
```

Example usage:

```lua
local ok, soundId = FWB.PlayUrlPos(-1, vec3(441.2, -981.9, 30.7), 20.0, 'https://example.com/test.mp3', 0.3, false)
```

Notes:

- server-side override
- the bridge generates the `soundId` for you

</details>

<details>
<summary><strong>Destroy A Sound</strong></summary>

Short description: Stop and clean up a previously created sound.

Signature:

```lua
Override.DestroySound(source, soundId)
```

Arguments:

| Name | Type | Required | Notes |
|---|---|---|---|
| `source` | `number` | Yes | Player target or `-1` |
| `soundId` | `string` | Yes | Generated sound id |

Returns:

- optional cleanup result

Override code:

```lua
function Override.DestroySound(source, soundId)
    exports.my_sound:Destroy(source, soundId)
end
```

Example usage:

```lua
FWB.Destroy(-1, soundId)
```

Notes:

- use the same sound id returned by `FWB.PlayUrlPos`

</details>

<details>
<summary><strong>Report The Active Sound Resource</strong></summary>

Short description: Return the sound resource name used by your setup.

Signature:

```lua
Override.GetSoundResourceName()
```

Arguments:

- none

Returns:

- `string`

Override code:

```lua
function Override.GetSoundResourceName()
    return 'my_sound'
end
```

Example usage:

```lua
print(FWB.GetSoundResourceName())
```

Notes:

- used by diagnostics and support checks

</details>
