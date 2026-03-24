# Resource Order

Bridge works best when the startup order is deliberate.

## Recommended Layout

A common layout is:

```text
resources/
└── [fs]/
    ├── fs_bridge
    ├── your_fs_script_1
    └── your_fs_script_2
```

## Recommended Start Order

1. `oxmysql`
2. `es_extended`, `qb-core`, or `qbx_core`
3. supported resources Bridge may use
4. `fs_bridge`
5. your own resources that depend on Bridge

## Why This Matters

Bridge needs to start after the things it detects.

Your own Bridge-based scripts need Bridge to already be running.

## Quick Rule

Think of it like this:

```text
framework -> integrations -> fs_bridge -> your scripts
```
