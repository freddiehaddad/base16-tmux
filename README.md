# base16-tmux

[base16][1] template for [tmux][3].

See the [base16 repository][1] for more information.

This repository is meant to work with [base16-shell][2]. It provides a hook and
template that can be used to dynamically load base16 color schemes in tmux.

## Installation (Manual)

Once you've cloned this repo (i.e. `~/.config/base16-tmux`), you can source the
theme you want to use from within your `tmux.conf` file.

```tmux
source-file $HOME/.config/base16-tmux/colors/base16-default-dark.conf
```

### Installation with [Tmux Plugin Manager][4]

Add plugin to the list of TPM plugins in `tmux.conf`:

```tmux
set -g @plugin 'freddiehaddad/base16-tmux'
```

Make sure to source your newly updated `tmux.conf`. Hit `prefix + I` to fetch
the plugin and source it. The plugin should now be working.

All the base16 themes are provided so you can pick and choose via `tmux.conf`
option:

- `set -g @colors-base16 'default-dark'` (the default)

## Usage with [base16-shell][2]

Your base16-tmux theme can be switched automatically alongside your other
base16-shell plugins by copying the hook to your [base16-shell][2] hooks
directory:

```text
cp ./hooks/10_tmux.sh ~/.config/base16-shell/hooks
```

You'll also need to update your `tmux.conf` file with the following option:

```tmux
set -g allow-passthrough on
```

## Troubleshooting Neovim

When opening neovim inside tmux, it's possible that you won't see the correct
theme colors. If you experience this behavior, open neovim inside tmux and type
`:checkhealth`. You'll see some information about terminal configuration. The
general fix is to open a non-tmux terminal window and check the value of
`$TERM`. Then add that value to your `tmux.conf` in the following format
replacing `XXX` with the value returned by `$TERM`.

```tmux
set-option -sa terminal-overrides ',XXX:RGB'
```

Based on the work of [tinted-theming][1].

[1]: https://github.com/tinted-theming/home
[2]: https://github.com/freddiehaddad/base16-shell
[3]: https://github.com/tmux/tmux
[4]: https://github.com/tmux-plugins/tpm
