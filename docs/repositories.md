# Repositories

Japanese: [repositories.ja.md](repositories.ja.md)

## Three-Repository Structure

This system is organized as three repositories.

### `m5papers3-news-system`

Purpose:

- integration hub
- overall architecture overview
- setup order
- operation notes

### `M5PaperS3_NewsDashboard`

Purpose:

- M5PaperS3-side sketch
- design notes in `docs/`
- cache, UI, read-state display, and power policy

Example local path:

```text
/Users/tomato/Documents/Arduino/M5PaperS3_NewsDashboard
```

### `m5papers3-news-server`

Purpose:

- Raspberry Pi-side scripts
- PNG generation
- `index.version` generation
- `systemd` and HTTP delivery

Example local path:

```text
/Users/tomato/Documents/projects/m5papers3-news-server
```

## How Responsibilities Are Split

### What belongs in the integration hub

- overall system view
- setup navigation
- repository relationships

### What belongs in the M5 repository

- device-specific implementation
- display behavior
- touch and swipe behavior
- cache and power control

### What belongs in the Raspberry Pi repository

- generation and delivery logic
- `systemd` operations
- font requirements

## Public Repository Policy

- do not publish real NHK content images
- do not commit generated PNG output
- source code, config examples, README files, and docs are appropriate to publish
