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
# Client

This page documents the public client-side Text UI helper.

## FWB.TextUi

### Text UI

<details>
<summary><strong>Show Text UI</strong></summary>

Short description: Show a text UI prompt through the active Bridge text UI integration.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `text` | `string` | Prompt text. When omitted, Bridge uses `No text provided` |
| `options` | `table` | Optional text UI configuration |
| `options.type` | `string` | Prompt type such as `inform`, `success`, `warning`, or `error`. Defaults to `inform` |
| `options.position` | `string` | Position such as `right-center`, `left-center`, `top-center`, or `bottom-center`. Defaults to `right-center` |
| `options.icon` | `string` | Optional icon |
| `options.iconColor` | `string` | Optional icon color |
| `options.iconAnimation` | `string` | Optional icon animation |

Returns:

- integration-specific result
- `nil`

How to write it as function:

```lua
FWB.TextUi.Show(text, options)
```

How to write it as export:

```lua
exports['fs_bridge']:ShowTextUi(text, options)
```

Example as function:

```lua
FWB.TextUi.Show('Press [E] to talk', {
    type = 'inform',
    position = 'right-center',
    icon = 'fa-solid fa-comments'
})
```

Example as export:

```lua
exports['fs_bridge']:ShowTextUi('Press [E] to talk', {
    type = 'inform',
    position = 'right-center',
    icon = 'fa-solid fa-comments'
})
```

</details>

<details>
<summary><strong>Hide Text UI</strong></summary>

Short description: Hide the current Bridge text UI prompt.

Arguments:

| Name | Type | Notes |
|---|---|---|
| `none` | - | This function does not take any arguments |

Returns:

- integration-specific result
- `nil`

How to write it as function:

```lua
FWB.TextUi.Hide()
```

How to write it as export:

```lua
exports['fs_bridge']:HideTextUi()
```

Example as function:

```lua
FWB.TextUi.Hide()
```

Example as export:

```lua
exports['fs_bridge']:HideTextUi()
```

</details>
