## Gitu keybindings & commands

Gitu's keybinds mimic [Magit](https://magit.vc/), while staying Vim-like. This
is a full reference generated from [`src/default_config.toml`](../src/default_config.toml),
the default configuration file. All of these can be overridden in your own
`~/.config/gitu/config.toml` (see the [README](../README.md#configuration)).

Press `h` or `?` at any time to open the in-app help menu (or set
`general.always_show_help.enabled = true` to always show it).

### CLI

```
gitu [OPTIONS] [COMMAND]
```

| Command | Description |
|---|---|
| `gitu` | Open the TUI at the status screen |
| `gitu show <reference>` | Open the TUI straight at a `show` screen for a commit/ref |
| `gitu blame <file> [-r/--rev <rev>]` | Open the TUI straight at a `blame` screen for a file |
| `gitu completion <shell>` | Print a shell completion script to stdout (`bash`, `elvish`, `fish`, `powershell`, `zsh`) |

| Option | Description |
|---|---|
| `-k, --keys <KEYS>` | Send keys on startup, e.g. `gitu -k ll` (single chars, special keys like `<enter>`, `<up>`, `<esc>`, and modifiers like `<ctrl+a>`) |
| `--print` | Print one frame and exit (useful for debugging) |
| `--log` | Enable logging to `gitu.log` |
| `--version` | Print version |
| `-c, --config <FILE>` | Config file to use |

### Navigation (root context)

| Key | Action |
|---|---|
| `k` / `up` | Move up |
| `j` / `down` | Move down |
| `ctrl+k` / `ctrl+up` | Move up one line |
| `ctrl+j` / `ctrl+down` | Move down one line |
| `alt+k` / `alt+up` | Move to previous section |
| `alt+j` / `alt+down` | Move to next section |
| `alt+h` / `alt+left` | Move to parent section |
| `tab` | Toggle (collapse/expand) section |
| `ctrl+u` | Half page up |
| `ctrl+d` | Half page down |
| `ctrl+y` | Scroll view up |
| `ctrl+e` | Scroll view down |
| `g g` | Move to top |
| `G` | Move to bottom |
| `/` | Search |
| `n` | Search next |
| `N` | Search previous |
| `g r` | Refresh |
| `q` / `esc` | Quit (or close current screen) |
| `h` / `?` | Open help menu |

### Global actions (root context)

These act on whatever item is currently selected (a file, hunk, line, commit, ref, stash, etc.):

| Key | Action |
|---|---|
| `enter` | Show — view a commit, or open `$VISUAL`/`$EDITOR`/`$GIT_EDITOR` at the selected line/file |
| `s` | Stage (file / hunk / line) |
| `u` | Unstage (file / hunk / line) |
| `K` | Discard (file / hunk / line) |
| `a` | Apply |
| `v` | Reverse |
| `y` | Copy hash |
| `B` | Blame |
| `Y` | Show refs — list all local branches, remote branches, and tags |

### Menus

Menus are opened with a key from the root context and closed with `q` or `esc`. Many menu items also take toggleable flag arguments (shown with their default off-state key, e.g. `-a`).

#### Branch menu — `b`
| Key | Action |
|---|---|
| `b` | Checkout branch/revision |
| `c` | Checkout new branch |
| `s` | Spinoff branch |
| `m` | Rename branch |
| `K` | Delete branch |

#### Commit menu — `c`
| Key | Action |
|---|---|
| `c` | Commit |
| `a` | Amend |
| `e` | Extend |
| `f` | Fixup |
| `F` | Instant fixup |
| `-a` | Toggle `--all` |
| `-e` | Toggle `--allow-empty` |
| `-v` | Toggle `--verbose` |
| `-n` | Toggle `--no-verify` |
| `-R` | Toggle `--reset-author` |
| `-s` | Toggle `--signoff` |

#### Fetch menu — `f`
| Key | Action |
|---|---|
| `a` | Fetch from all remotes |
| `u` | Fetch from upstream |
| `p` | Fetch from push-remote |
| `e` | Fetch from elsewhere |
| `-p` | Toggle `--prune` |
| `-t` | Toggle `--tags` |

#### Log menu — `l`
| Key | Action |
|---|---|
| `l` | Log current branch |
| `o` | Log other |
| `-n` | Set number of commits shown |
| `-F` | Set `--grep` filter |

#### Merge menu — `m`
| Key | Action |
|---|---|
| `m` | Merge |
| `a` | Abort merge |
| `c` | Continue merge |
| `-f` | Toggle `--ff-only` |
| `-n` | Toggle `--no-ff` |

#### Pull menu — `F`
| Key | Action |
|---|---|
| `u` | Pull from upstream |
| `p` | Pull from push-remote |
| `e` | Pull from elsewhere |
| `-r` | Toggle `--rebase` |

#### Push menu — `P`
| Key | Action |
|---|---|
| `u` | Push to upstream |
| `p` | Push to push-remote |
| `e` | Push to elsewhere |
| `-f` | Toggle `--force-with-lease` |
| `-F` | Toggle `--force` |
| `-h` | Toggle `--no-verify` |
| `-n` | Toggle `--dry-run` |

#### Rebase menu — `r`
| Key | Action |
|---|---|
| `i` | Rebase interactively |
| `a` | Abort rebase |
| `c` | Continue rebase |
| `e` | Rebase onto elsewhere |
| `f` | Autosquash |
| `-k` | Toggle `--keep-empty` |
| `-p` | Toggle `--preserve-merges` |
| `-d` | Toggle `--committer-date-is-author-date` |
| `-a` | Toggle `--autosquash` |
| `-A` | Toggle `--autostash` |
| `-i` | Toggle `--interactive` |
| `-h` | Toggle `--no-verify` |

#### Remote menu — `M`
| Key | Action |
|---|---|
| `a` | Add remote |
| `K` | Remove remote |
| `r` | Rename remote |

#### Reset menu — `X`
| Key | Action |
|---|---|
| `s` | Reset soft |
| `m` | Reset mixed |
| `h` | Reset hard |

#### Revert menu — `V`
| Key | Action |
|---|---|
| `V` | Revert commit(s) |
| `a` | Abort revert |
| `c` | Continue revert |
| `-e` | Toggle `--edit` |
| `-E` | Toggle `--no-edit` |
| `-s` | Toggle `--signoff` |

#### Cherry-pick menu — `A`
| Key | Action |
|---|---|
| `A` | Cherry-pick commit(s) |
| `a` | Abort cherry-pick |
| `c` | Continue cherry-pick |
| `-n` | Toggle `--no-commit` |
| `-s` | Toggle `--signoff` |
| `-e` | Toggle `--edit` |

#### Stash menu — `z`
| Key | Action |
|---|---|
| `z` | Stash both (index & worktree) |
| `i` | Stash index |
| `w` | Stash worktree |
| `x` | Stash, keeping index |
| `p` | Pop stash |
| `a` | Apply stash |
| `k` | Drop stash |
| `-a` | Toggle `--all` |
| `-u` | Toggle `--include-untracked` |

### Picker (used for prompts like checkout/branch selection)

| Key | Action |
|---|---|
| `down` / `ctrl+n` / `tab` | Next item |
| `up` / `ctrl+p` / `backtab` | Previous item |
| `enter` | Confirm selection |
| `esc` / `ctrl+c` | Cancel |
