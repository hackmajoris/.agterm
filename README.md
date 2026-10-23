# agterm config

Personal [agterm](https://github.com/umputun/agterm) config, shared between machines.

## Files

- `keymap.conf` — key bindings and custom commands
- `hooks.conf` — event hooks
- `ghostty.conf` — agterm-scoped ghostty overrides
- `restore-denylist.conf` — commands not re-run on restore
- `Brewfile` — agterm plus the tools the keymap opens

Not tracked: `agent-status/` (installed by the app) and app state in
`~/Library/Application Support/agterm` (windows, theme, font — set in Settings).

## Custom commands

All open as a floating overlay in the current session's directory.

| Chord      | Command |
|------------|---------|
| `ctrl+a>y` | yazi    |
| `ctrl+a>g` | lazygit |
| `ctrl+a>d` | revdiff |
| `ctrl+a>n` | nvim    |
| `ctrl+a>b` | btop    |

Paths are hardcoded to `/opt/homebrew/bin` (Apple Silicon Homebrew).

## Install

```sh
mv ~/.config/agterm ~/.config/agterm.bak 2>/dev/null
git clone https://github.com/hackmajoris/.agterm.git ~/.config/agterm
brew trust umputun/apps
brew bundle --file ~/.config/agterm/Brewfile
```

Then:

- agterm: Help ▸ Install Command Line Tool…
- agterm: Help ▸ Install Agent Status Hooks… (adds the `source` line to `~/.zshrc`)
- `agtermctl theme set Violite`
- `agtermctl keymap reload && agtermctl hooks reload && agtermctl config reload`

## Update

```sh
git -C ~/.config/agterm pull
agtermctl keymap reload && agtermctl hooks reload && agtermctl config reload
```
