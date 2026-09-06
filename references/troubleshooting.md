# Find My script reference

| Script | Purpose |
|---|---|
| `fm-window.sh` | Return the Find My window ID and bounds. |
| `fm-screenshot.sh [path]` | Capture the Find My window. |
| `fm-tab.sh <tab>` | Switch among `people`, `devices`, and `items`. |
| `fm-list.sh [tab]` | Capture the selected tab for visual identification. |
| `fm-select-item.sh <position> [tab]` | Select a sidebar entry by position. |
| `fm-locate.sh <position> [tab]` | Select an entry and capture its map. |
| `fm-info.sh [path]` | Try to open the selected entry's info and capture it. |
| `fm-play-sound.sh <position>` | Try to activate Play Sound for an item. |
| `fm-click.sh <x> <y>` | Click relative to the current Find My window. |

The selection scripts own the approximate tab and sidebar coordinates. Use
`fm-click.sh` manually only after obtaining fresh window bounds with
`fm-window.sh`; window movement and macOS UI changes can invalidate old
coordinates.

If the window is not found, confirm Find My and OpenClaw.app are running and that
OpenClaw.app has Screen Recording and Accessibility permissions. If clicks miss,
bring Find My to the front and retry with fresh bounds.

The info and Play Sound controls are not always exposed to accessibility. When a
script reports that it could not find one, inspect the screenshot and tell the
user that manual interaction may be required.
