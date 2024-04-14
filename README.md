# sway-interactive-screenshot

`sway-interactive-screenshot` is Python helper script that enables users to take
screenshots and video captures interactively with [Sway](https://swaywm.org).

![fuzzel-sway-interactive-screenshot](https://user-images.githubusercontent.com/19509728/236029456-d633c09d-94fa-498c-bf4f-477283e181db.png)


## Install

If you are using Arch Linux, you can install sway-interactive-screenshot with
the
[`sway-interactive-screenshot`](https://aur.archlinux.org/packages/sway-interactive-screenshot)
 AUR package (e.g. `yay -S sway-interactive-screenshot`). You can otherwise download the [`sway-interactive-screenshot`](https://raw.githubusercontent.com/moverest/sway-interactive-screenshot/master/sway-interactive-screenshot) file, set it as executable and add it to your `$PATH` (e.g. putting it into your `/usr/bin`)

## Dependencies

For the program to work, you will need the following dependencies installed:

- Python 3.7+.
- [`swaywm`](https://swaywm.org).
- [`fuzzel`](https://codeberg.org/dnkl/fuzzel) to prompt what you want to take
  a screenshot of.
- [`grim`](https://github.com/emersion/grim) to take the screenshot.
- [`slurp`](https://github.com/emersion/slurp) to select an area on the screen.
- [`notify-send`](https://gitlab.gnome.org/GNOME/libnotify) to send a notification to the notification daemon (such as
  [`mako`](https://github.com/emersion/mako)).
- [`wl-clipboard`](https://github.com/bugaevc/wl-clipboard) to copy the
  screenshot to the clipboard.
- [`rofi`](https://github.com/lbonn/rofi) (optional) to use rofi instead of fuzzel
- [`swappy`](https://github.com/jtheoof/swappy) (optional) to edit the captured
  screenshot.
- [`dragon`](https://github.com/mwh/dragon) (optional) to drag and drop the
  captured screenshot.
- [`xdg-utils`](https://www.freedesktop.org/wiki/Software/xdg-utils/)
  (optional) to open the captured screenshot with the default image viewer.
- [`wf-recorder`](https://github.com/ammen99/wf-recorder) (optional) to capture
  videos.
- [`tomli`](https://github.com/hukkin/tomli) if not using Python 3.11+.

## Bind to the `Print` key

To bind this script to the `Print` key, just add this to your `~/.config/sway/config`:

```
bindsym Print exec /path/to/sway-interactive-screenshot
```

You can also add this to do video capture:

```
bindsym Shift+Print exec /path/to/sway-interactive-screenshot --video
```

## Edit the screenshot

You can edit a screenshot that was taken by running the default action on the
notification. With [`mako`](https://github.com/emersion/mako)'s default
settings, this is done by just clicking on the notification.

## Settings

`sway-interactive-screenshot` can be configured through the `~/.config/sway-interactive-screenshot/config.toml` file. Here's an example:

```toml
[screenshot]

# Prompt string to use.
prompt = "📷> "

# Directory in which to save screenshots.
save_dir = "~"

# File name format.
# See: https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes
file_name = "screenshot_%Y-%m-%dT%H:%M:%S.png"

# Image format.
type = "png" # "jpeg", "ppm"

# JPEG quality value.
jpeg_quality = 80

# PNG compression level value.
png_level = 6

# Show or hide cursor.
cursor = false


[screencast]

# Prompt string to use.
prompt = "📹> "

# PID file used to keep track of a screencast in progress.
pid_file = "${XDG_RUNTIME_DIR}/sway-interactive-screenshot.${WAYLAND_DISPLAY}.video.pid"

# Directory in which to save screencast.
save_dir = "~"

# File name format.
# See: https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes
file_name = "screencast_%Y-%m-%dT%H:%M:%S.mkv"

# Record audio.
audio = "ask" # "yes", "no"

[notification_actions]
# Alternative name for dragon-drop binary
dragon.command = "dragon"

[rofi]
use_rofi = false
rofi_theme = ""

```

The `SWAY_INTERACTIVE_SCREENSHOT_SAVEDIR` environment variable, while still supported, is deprecated and will be removed in a future version.
