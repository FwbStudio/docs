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
# Integrations

## <mark style="color:green;">Client Side:</mark>

### Unlocked File Path:

<mark style="color:yellow;">fs\_switch/client/unlocked.lua</mark>

### Notification:

Notification can be changed in this function

```lua
--bydefault we add ox_lib notification you can edit according to your need
function notification(title, text, duration, type, icon)    
        lib.notify({
            title = title,
            description = text,
            type = type,
            duration = duration,
            icon = icon,
            position = 'top'
        })
end
```
