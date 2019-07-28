# sway-interactive-screenshot

sway-interactive-screenshot is as simple bash script to take screenshot easly on sway. Just launch the script and it will ask you what you want to take a screenshot.

## Dependencies

- `swaywm` obviously
- `jq` to parse `swaymsg` JSON response that lists windows
- `rofi` to prompt what you want to take a screenshot of
- `grim` to take the screenshot
- `slurp` to select an area on the screen
- `notify-send` to send a notification to notification daomon (such as [`mako`](https://github.com/emersion/mako))
- `wl-copy` to copy the screenshot to the clipboard

On Archlinux, you can install them all with `pacman -S jq rofi grim slurp notify-send wl-copy`.

## Bind it to the `Print` key

To bind this script to the `Print` key, just add this to your `~/.config/sway/config`:

```
bindsym Print exec /path/to/sway-interactive-screenshot
```
