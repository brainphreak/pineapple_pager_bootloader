# Bootloader Theming Guide

Customize the bootloader's appearance by editing `launcher_config.json` and adding your own images and fonts.

## Quick Start

1. Edit `pagerctl_bootloader/launcher_config.json`
2. Put custom images in `pagerctl_bootloader/images/`
3. Put custom fonts in `pagerctl_bootloader/fonts/`
4. Put boot animation frames in `pagerctl_bootloader/boot_frames/`

## launcher_config.json

```json
{
    "title": "Bootloader",
    "show_title": true,
    "title_font": "fonts/title.TTF",
    "font": "fonts/menu.ttf",
    "title_font_size": 28,
    "item_font_size": 18,
    "bg_image": "images/my_bg.png",
    "colors": {
        "title": [100, 200, 255],
        "selected": [0, 255, 0],
        "unselected": [255, 255, 255],
        "highlight_bg": [30, 50, 80]
    }
}
```

All paths are relative to the `pagerctl_bootloader/` directory.

## Fields

| Field | Default | Description |
|-------|---------|-------------|
| `title` | "Bootloader" | Title text at the top of the menu |
| `show_title` | true | Set `false` if title is baked into your background image |
| `title_font` | fonts/title.TTF | Title font file |
| `font` | fonts/menu.ttf | Menu item font file |
| `title_font_size` | 28 | Title font size in pixels |
| `item_font_size` | 18 | Menu item font size in pixels |
| `bg_image` | (none) | Custom background image. If not set, uses the active Pager UI theme |
| `colors.title` | [100, 200, 255] | Title text color [R, G, B] |
| `colors.selected` | [0, 255, 0] | Selected item color |
| `colors.unselected` | [255, 255, 255] | Unselected item color |
| `colors.highlight_bg` | [30, 50, 80] | Reserved for future use |

## Background Image

By default the bootloader pulls its background from the active Pineapple Pager UI theme (Circuitry, Wargames, etc.). To use your own:

1. Create a **480x222** PNG image
2. Save it to `images/my_bg.png`
3. Set `"bg_image": "images/my_bg.png"` in `launcher_config.json`
4. Set `"show_title": false` if your background includes the title text

## Fonts

Replace the fonts in `fonts/`:

| File | Used for |
|------|----------|
| `fonts/title.TTF` | Title text at the top |
| `fonts/menu.ttf` | Menu items, settings, submenus |

Any `.ttf` or `.TTF` font file works. Reference it by filename in the config.

## Boot Animation

When **Boot on Start** is enabled, the bootloader replaces the default Hak5 boot animation with custom frames. Place your frames in `boot_frames/`:

```
boot_frames/
  frame1.png
  frame2.png
  frame3.png
  frame4.png
```

- Name files `frame1.png`, `frame2.png`, `frame3.png`, etc.
- Use as many frames as you want
- Images must be **480x222** landscape PNG
- Frames are automatically converted when you enable Boot on Start in Settings
- The animation loops at ~0.55 seconds per frame until the bootloader menu appears

## Colors

Colors are `[R, G, B]` arrays with values 0-255:

```json
"colors": {
    "title": [100, 200, 255],
    "selected": [0, 255, 0],
    "unselected": [255, 255, 255],
    "highlight_bg": [30, 50, 80]
}
```

| Color | Where it's used |
|-------|----------------|
| `title` | Title text |
| `selected` | Currently highlighted menu item |
| `unselected` | Non-highlighted menu items |
| `highlight_bg` | Reserved for future use |

## File Structure

```
pagerctl_bootloader/
  launcher_config.json    # Theme configuration
  fonts/
    title.TTF             # Title font
    menu.ttf              # Menu font
  images/                 # Custom backgrounds
    my_bg.png             # 480x222 PNG
  boot_frames/            # Boot animation frames
    frame1.png            # 480x222 PNG
    frame2.png
    frame3.png
    ...
```
