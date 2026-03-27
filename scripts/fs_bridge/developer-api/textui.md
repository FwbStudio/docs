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
# Text UI

This page documents the public `FWB.TextUi` helpers.

## Public Calls

```lua
FWB.TextUi.Show(text, options)
FWB.TextUi.Hide()

exports['fs_bridge']:ShowTextUi(text, options)
exports['fs_bridge']:HideTextUi()
```

## Common Options

- `type` -> `inform`, `error`, `success`, `warning`
- `icon`
- `iconColor`
- `position` -> `right-center`, `left-center`, `top-center`, `bottom-center`
- `iconAnimation`

## Notes

- This module is client-side.
- `FWB.ShowTextUi` and `FWB.HideTextUi` still exist as deprecated compatibility aliases.
- Bridge routes the request to the selected text UI resource.

## Example

```lua
FWB.TextUi.Show('Press [E] to interact', {
    type = 'inform',
    position = 'right-center'
})

FWB.TextUi.Hide()
```

