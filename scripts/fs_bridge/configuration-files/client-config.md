# Client Config (`cl_config.lua`)

`config/cl_config.lua` currently handles client-side settings for Bridge zone creation helpers.

This is not a normal day-to-day file for most server owners, but it is useful when a resource uses the Bridge zone creation tools.

## Top-Level Section

| Key | Purpose |
|---|---|
| `zonecreation` | Client-side controls, hints, markers, and movement speed settings |

## Zone Creation Areas

The current file exposes these groups:

| Group | Purpose |
|---|---|
| `poly` | Polygon point creation controls and camera movement speed |
| `marker` | Marker placement controls and marker appearance |
| `placement` | Object placement controls, rotation, and movement speed |
| `place_target` | Target placement controls and radius adjustment |

## What You Can Change Here

This file currently controls:

- on-screen hint text
- control indexes for placement tools
- movement and rotation speed values
- marker size, offset, and color
- target placement radius speed

## Important Note

Only change this file if you are working with Bridge-supported zone creation tools or a script that specifically tells you to edit `cl_config.lua`.
