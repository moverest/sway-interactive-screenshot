# sway-interactive-screenshot

`sway-interactive-screenshot` is Python script that enable users to take
screenshot interactively with [Sway](https://swaywm.org).

## Install

If you are using Arch Linux, you can install sway-interactive-screenshot with
the
[`sway-interactive-screenshot`](https://aur.archlinux.org/packages/sway-interactive-screenshot)
 AUR package (e.g. `yay -S sway-interactive-screenshot`).

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
- [`swappy`](https://github.com/jtheoof/swappy) (optional) to edit the captured
  screenshot.
- [`dragon`](https://github.com/mwh/dragon) (optional) to drag and drop the
  captured screenshot.

## Bind to the `Print` key

To bind this script to the `Print` key, just add this to your `~/.config/sway/config`:

```
bindsym Print exec /path/to/sway-interactive-screenshot
```

## Edit the screenshot

You can edit a screenshot that was taken by running the default action on the
notification. With [`mako`](https://github.com/emersion/mako)'s default
settings, this is done by just clicking on the notification.

## Settings

By default, `sway-interactive-screenshot` saves the screenshots in the home
directory. You can change that by setting the
`SWAY_INTERACTIVE_SCREENSHOT_SAVEDIR` environment variable to another
directory.
