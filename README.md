# MinimalCord Reborn

A lightweight, dark-only rewrite of [MinimalCord](https://github.com/DiscordStyles/MinimalCord) by Gibbu for the current Discord client and [Vencord](https://vencord.dev). It keeps the original's flat, rounded-card look, but is built from a small set of colour-variable overrides and a few selectors instead of a large pile of rules, so it stays light on your PC.

Supports the Dark, Darker and Midnight themes. Light mode is intentionally not supported.

## What is styled

Server list, channel list, DM list and user panel, chat and message cards (with rounded mention bars and hover), member list, friends page and Active Now cards, voice-channel text chat, forum post cards, profiles, context menus and the User Settings pages. Everything else follows Discord's own variables, which the theme recolours.

## Download

- **Vencord:** add this link under Online Themes in Vencord's Themes tab, or download the file and put it in the themes folder:

  ```
  https://raw.githubusercontent.com/MEWPASCO/MinimalCord-Reborn/deploy/MinimalCord.theme.css
  ```

- **BetterDiscord:** download `MinimalCord.theme.css` from the link above and put it in BetterDiscord's themes folder (the header at the top of the file works for both clients).

The GitHub workflow builds the file. If your workflow publishes to a different branch than `deploy`, adjust the link.

For the Inter font, add this link under Online Themes in the same tab. Without it Discord uses its own font:

```
https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap
```

## Develop

```
npm install
npm run watch
```

`watch` rebuilds `src/index.scss` into `%APPDATA%/Vencord/themes/MinimalCord-Local.theme.css` on every save. Enable "MinimalCord-Local" in Vencord's Themes tab once. If a change does not show up, press Ctrl+R in Discord.

```
npm run build
```

writes `dist/MinimalCord.theme.css`. `dist/` is git-ignored because the GitHub workflow builds it, so do not commit it.

## Settings

`src/_config.scss` holds the options: accent colour, background hue / saturation / lightness, border radius, message padding and spacing, mention colour, message hover strength, font, and switches for message cards, auto-hiding scrollbars and the performance options (hide header effects, disable blur).

## How it is built

| File | What it does |
| --- | --- |
| `_config.scss` | Your settings |
| `_palette.scss` | Derives every background and text colour from the settings |
| `_brand.scss` | Builds Discord's brand colour scale from the accent |
| `_surfaces.scss` | Overrides Discord's own colour variables (most of the theme) |
| `_hooks.scss` | **Every Discord class name the theme uses, in one place** |
| `_base.scss` | Selection colour, auto-hiding scrollbars |
| `_frame.scss` | Flat server list, sidebar and user panel |
| `_channels.scss` | Channel list with the accent bar |
| `_dms.scss` | DM panel colour and brighter names in the DM list |
| `_friends.scss` | Friends list and Active Now cards, without divider lines |
| `_profiles.scss` | Hides the scrollbar under the profile tabs |
| `_chat.scss` | Channel header and message box |
| `_forums.scss` | Voice-channel chat surface and forum post cards |
| `_settings.scss` | Brighter unselected page names in User Settings |
| `_search.scss` | Search results panel and result cards |
| `_messages.scss` | Message cards, mentions, code blocks |
| `_members.scss` | Member list |
| `_menus.scss` | Context menu highlight |
| `_performance.scss` | Optional speed-ups |

## When Discord updates break something

Fix it in `src/_hooks.scss`. Most hooks match on a class name and ignore Discord's changing hash; the few that need the exact class are marked there.

## Credits

Original theme by Gibbu. Rewrite by Wolfÿ.
