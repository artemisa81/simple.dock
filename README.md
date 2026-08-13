# simple.dock

A minimal, autohiding app dock for [Omarchy](https://omarchy.org) (Quickshell).

![Preview](preview.png)

## Features

- Centered dock card opposite the bar (default: bottom edge).
- Apps menu button that opens the Omarchy apps menu.
- Pinned apps (in your chosen order) followed by running apps.
- Left-click a running app to focus it (or launch a pinned app that isn't running).
- Right-click for a context menu: **Launch**, **Pin to Dock** / **Unpin from Dock**, and **Close Window(s)**.
- Pin state persists in `~/.config/omarchy/dock.json` across shell restarts.
- Autohide: the dock hides and reveals itself when the cursor touches the bottom edge of the screen.

## Requirements

- An Omarchy system (omarchy-shell with Quickshell support).

## Installation

Clone this repository into the Omarchy user plugin directory:

```sh
git clone git@github.com:nightdevil00/simple.dock.git \
  ~/.config/omarchy/plugins/simple.dock
```

Enable the plugin and restart the shell:

```sh
omarchy plugin enable simple.dock
omarchy restart shell
```

The dock appears at the bottom of the primary monitor. Touch the bottom edge
of the screen with the cursor to reveal it.

## Configuration

Pinned apps are stored in `~/.config/omarchy/dock.json`:

```json
{
  "pinned": ["vesktop", "foot", "org.gnome.Nautilus"]
}
```

Entries are desktop-file ids (the `.desktop` suffix is optional). The file is
created automatically the first time you pin an app; edits you make to it are
picked up while the shell is running.

## Files

- `manifest.json` — plugin manifest (`id: simple.dock`, `kind: overlay`, kept loaded).
- `Dock.qml` — the dock UI (a full-screen overlay whose interactive region is
  limited to the dock card, the context menu, and the bottom reveal strip).
- `DockModel.js` — pure helpers for the model and persistence.

## License

MIT
