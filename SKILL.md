---
name: find-my
description: Use the macOS Find My app through Peekaboo to locate people, devices, or items and play sounds for lost items.
metadata:
  os: [darwin]
  requires:
    bins: [peekaboo, jq]
    env:
      PEEKABOO_BRIDGE_SOCKET: "Path to OpenClaw.app Peekaboo bridge socket (default: ~/Library/Application Support/OpenClaw/bridge.sock)"
    env_optional:
      FM_OUTPUT_DIR: "Directory for screenshot output (default: /tmp)"
  contains_scripts: true
  privacy:
    screenshots: true
    location_data: true
    ui_automation: true
---

# Find My

Control the native Find My app with the bundled scripts. Run them from
`{skillDir}` with Find My and OpenClaw.app open.

This workflow exposes private location data and saves local screenshots. Show
only the location needed for the user's request and do not send screenshots or
location data elsewhere without authorization. Visible UI automation controls the
mouse while it runs.

## Locate something

Find My does not reliably expose sidebar names through accessibility APIs, so
selection is positional:

1. Run `./scripts/fm-list.sh people|devices|items` and inspect its screenshot.
2. Identify the requested entry's position. Do not guess when the screenshot is
   ambiguous.
3. Run `./scripts/fm-locate.sh POSITION people|devices|items` and inspect the
   resulting location screenshot.
4. Run `./scripts/fm-info.sh` only when the user needs the selected entry's
   details or actions.

For an explicit request to make an AirTag or item audible, run
`./scripts/fm-play-sound.sh POSITION`. Report when the script could not identify
the Play Sound control instead of claiming it succeeded.

For script roles, coordinate fallback, and failures, read
[references/troubleshooting.md](references/troubleshooting.md).
