# MinimalCord Reborn

A lightweight rewrite of [MinimalCord](https://github.com/DiscordStyles/MinimalCord) by Gibbu for the current Discord client. Dark themes only (Dark, Darker, Midnight).

## Develop

```
npm install
npm run watch
```

`watch` rebuilds `src/index.scss` into your Vencord themes folder (`%APPDATA%/Vencord/themes/MinimalCord-Local.theme.css`) every time you save. Enable "MinimalCord-Local" in Vencord's Themes tab once. If a change does not show up, press Ctrl+R in Discord.

```
npm run build
```

writes `dist/MinimalCord.theme.css`.

## Settings

`src/_config.scss` has the same options as the original: accent colour, background hue / saturation / lightness, border radius, message padding and spacing. It also has switches for the message cards and the two performance options.

To get the Inter font, add this link in Vencord's Themes tab under Online Themes. Without it Discord falls back to its own font:

```
https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap
```

## How it is built

| File | What it does |
| --- | --- |
| `_config.scss` | Your settings |
| `_palette.scss` | Derives every background and text colour from the settings |
| `_brand.scss` | Builds Discord's brand colour scale from the accent |
| `_surfaces.scss` | Overrides Discord's own colour variables (most of the theme) |
| `_hooks.scss` | **Every Discord class name the theme uses, in one place** |
| `_base.scss` | Selection colour, scrollbars |
| `_frame.scss` | Flat server list, sidebar and user panel |
| `_channels.scss` | Channel list with the accent bar |
| `_chat.scss` | Channel header and message box |
| `_messages.scss` | Message cards, mentions, code blocks |
| `_members.scss` | Member list |
| `_menus.scss` | Context menu highlight |
| `_performance.scss` | Optional speed-ups |

When a Discord update breaks something, `_hooks.scss` is the place to fix it. Most hooks match on a class name and ignore Discord's changing hash; the few that need the exact class are marked there.

## Not ported yet

Settings pages, forum channels, friends list, discovery, search results, emoji picker and the other long-tail screens of the original. Discord's own variables (recoloured in `_surfaces.scss`) cover most of their colours. Send a DOM dump of a screen to have it ported properly.
