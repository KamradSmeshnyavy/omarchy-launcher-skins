# Omarchy Launcher Skins

[🇷🇺 Русский](README.ru.md)

Full-screen skins for the [Omarchy](https://omarchy.org) menu and app launcher. A clone of the stock
`omarchy.menu`: every menu, search and action works as before — the skin decides how the list is drawn.
Each skin is recoloured from the active theme every time it opens.

![Skins](screenshots/skins.webp)

| Skin | |
|---|---|
| `constellation` | apps as stars on a sky map |
| `terminal` | a theme-tinted CRT shell prompt |
| `tarot` | a fan of cards; `tarot-hack` deals them from `xxd apps.deck.bin` |
| `orrery` | apps orbiting a sun |
| `aquarium` | apps as fish |
| `lanterns` | floating lanterns under the moon |
| `metro` | a subway line map |
| `drum` | a rotating drum |
| `bookshelf` | apps as books on shelves |
| `matrix` | falling code; `matrix-term` in the terminal palette |
| `list` | the stock card |

Every skin except `constellation` and `terminal` also has a minimal terminal-style twin: `drum-hack`,
`tarot-hack`, `metro-hack`, `orrery-hack`, `matrix-hack`, `bookshelf-hack`, `lanterns-hack`, `aquarium-hack`.

![Terminal skin](screenshots/terminal.webp)

## Install

```sh
omarchy plugin add https://github.com/KamradSmeshnyavy/omarchy-launcher-skins --enable
omarchy restart shell
echo '{"skin": "orrery"}' > ~/.config/omarchy/extensions/menu-skin.json
```

The file is watched — you can switch skins even while the menu is open. Open it as usual: Super+Space
(menu), Super+Alt+Space (apps). Optional `"backdrop": 0.94` sets how much of the desktop shows through.
Back to the stock menu: `omarchy plugin enable omarchy.menu`.

Tested on Omarchy 4.0.6 with Quickshell 0.3.2.

## Keys

Typing searches, as in the stock menu. On top of that:

| Keys | |
|---|---|
| ↑ ↓ / Ctrl+J Ctrl+K | along the list, or around the ring |
| ← → / Ctrl+H Ctrl+L / PgUp PgDn | pages (on plain lists: back / open) |
| Home / End | first / last |
| Alt+1…9 | quick-launch the numbered item |
| Enter / Backspace / Esc | open / back / close |

## Writing a skin

A skin is a QML file that extends `SkinBase.qml` and is registered in `SkinConfig.qml` (`files`).
`ThemePalette.qml` gives it the whole `colors.toml` of the current theme. A skin that sets `pageSize`
(and `radial: true` for rings) gets paging from the base: `page`, `pages`, `pageStart`, `pageCount`,
`ringStep()`, `pageStep()` and an animated `ringPhase`. `variant` is `"hack"` / `"term"` for the twins.

## With the Customizer

[omarchy-customizer](https://github.com/KamradSmeshnyavy/omarchy-customizer) is one overlay (Super+Shift+T) with live preview for this plugin's settings and
the rest of the look & feel: themes, wallpapers, Hyprland animations, transparency, blur, screen shaders.
One command installs it and offers this plugin and the others:

```sh
curl -fsSL https://raw.githubusercontent.com/KamradSmeshnyavy/omarchy-customizer/main/install.sh | bash
```

## License

MIT. Based on `omarchy.menu` from [Omarchy](https://github.com/basecamp/omarchy) (MIT, © David Heinemeier
Hansson).

[My dotfiles](https://github.com/KamradSmeshnyavy/dotfiles) run a few more skins ported from
[omlauch](https://github.com/hamzaabde-langjk/omlauch) and
[omarchy-quickapps](https://github.com/bjarneo/omarchy-quickapps). They are not included here because those
projects have no license yet.
