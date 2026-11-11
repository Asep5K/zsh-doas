# zsh-doas

This is a modification of [`ohmyzsh/sudo`](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sudo), incorporating `doas` and  [`doasedit`](https://codeberg.org/TotallyLeGIT/doasedit) as replacements for `sudo` and `sudoedit/sudo -e`.

Easily prefix your current or previous commands with `doas` or [`doasedit`](https://codeberg.org/TotallyLeGIT/doasedit) by pressing <kbd>esc</kbd> twice.


## Installation

### Manual

First, clone this repository (make sure to include submodules).
```zsh
git clone --recursive https://codeberg.org/Asep5K/zsh-doas ~/somewhere
```
Then add the following line to your ~/.zshrc.
```zsh
source ~/somewhere/zsh-doas.plugin.zsh
```

### Using Zinit

```zsh
zinit ice depth"1" from"codeberg.org"
zinit light Asep5K/zsh-doas
```
---
## Usage

### Current typed commands

Say you have typed a long command and forgot to add `doas` in front:

```console
$ emerge sys-devel/gcc
```

By pressing the <kbd>esc</kbd> key twice, you will have the same command with `doas` prefixed without typing:

```console
$ doas emerge sys-devel/gcc
```

The same happens for editing files with your default editor (defined in `$DOAS_EDITOR`, `$VISUAL` or `$EDITOR`, in that order):

If the editor defined were `vim`:

```console
$ vim /etc/hosts
```

By pressing the <kbd>esc</kbd> key twice, you will have the same command with `doasedit` instead of the editor, that would open that editor with root privileges:

```console
$ doasedit /etc/hosts
```

### Previous executed commands

Say you want to delete a system file and denied:

```console
$ rm some-system-file.txt
rm: cannot remove 'some-system-file.txt': Permission denied
$
```

By pressing the <kbd>esc</kbd> key twice, you will have the same command with `doas` prefixed without typing:

```console
$ rm some-system-file.txt
rm: cannot remove 'some-system-file.txt': Permission denied
$ doas rm some-system-file.txt
doas (user@hostname) password: 
$
```

The same happens for file editing, as told before.

## Key binding

By default, the `zsh-doas` plugin uses <kbd>Esc</kbd><kbd>Esc</kbd> as the trigger.
If you want to change it, you can use the `bindkey` command to bind it to a different key:

```sh
bindkey -M emacs '<seq>' doas-command-line
bindkey -M vicmd '<seq>' doas-command-line
bindkey -M viins '<seq>' doas-command-line
```

where `<seq>` is the sequence you want to use. You can find the keyboard sequence
by running `cat` and pressing the keyboard combination you want to use.

<!-- vi: nowrap
