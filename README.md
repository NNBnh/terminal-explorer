<h1 align="center"><i>Terminal Explorer</i></h1>
<p align="center">Bring file manager's copy/paste to the CLI</p>
<p align="center"><img src="https://img.shields.io/github/license/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=for-the-badge" alt="License: GPL-3.0"> <img src="https://img.shields.io/github/languages/top/NNBnh/terminal-explorer?logo=gnu-bash&labelColor=073551&color=4EAA25&logoColor=FFFFFF&style=for-the-badge" alt="Shell: 100%"> <img src="https://img.shields.io/badge/development-completed-%234EAA25.svg?labelColor=073551&style=for-the-badge&logoColor=FFFFFF" alt="Development completed"></p>
<p align="center"><img src="https://img.shields.io/github/watchers/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"> <img src="https://img.shields.io/github/stars/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"> <img src="https://img.shields.io/github/forks/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"> <img src="https://img.shields.io/github/issues/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"></p>

## About
**Terminal explorer** is a files manager tool written in [`pure sh`](https://github.com/dylanaraps/pure-sh-bible) that mimic the way GUI's file manager do copy/cut/paste.

## Features
- **Minimum**: with exactly [**200** lines of `sh`](https://github.com/NNBnh/terminal-explorer/blob/main/te#L200) and [minimum dependencies](#dependencies).
- **Register**: you can operate in any specific register.
- **Smart cut**: after cutting the file to a new path, the file's new path will be automatically copied for future operation.
- **Customizable**: you can change the commands to set/get the clipboard, commands to copy/cut files, see more [here](#configuration).

## Contents
- [About](#about)
- [Features](#features)
- [Contents](#contents)
- [Setup](#setup)
  - [Dependencies](#dependencies)
  - [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Credits](#credits)

## Setup
### Dependencies
- `sh` to process
- One of these clipboard managers:
  - [`clipb`](https://github.com/NNBnh/clipb) clipboard managers warper
  - [`wl-clipboard`](https://github.com/bugaevc/wl-clipboard) for [Wayland](https://wayland.freedesktop.org)
  - [`xclip`](https://github.com/astrand/xclip) or [`xsel`](http://www.kfish.org/software/xsel) for [X.org](https://www.x.org)

### Installation
#### Manually
- Option 1: using `curl`

```sh
curl https://raw.githubusercontent.com/NNBnh/terminal-explorer/main/te > ~/.local/bin/te
chmod +x ~/.local/bin/te
```

- Option 2: using `git`

```sh
git clone https://github.com/NNBnh/terminal-explorer.git ~/.local/share/terminal-explorer
ln -s ~/.local/share/terminal-explorer/te ~/.local/bin/te
```

#### Package manager
`#TODO`

## Usage
Run `te` in the terminal:

```sh
te ACTION[REGISTER] FILES
```

Or:

```sh
te PASTE[REGISTER] [COMMAND]
```

```console
ACTION:
  c, y          copy FILES into REGISTER's clipboard and set paste's action to copy
  x, d          copy FILES into REGISTER's clipboard and set paste's action to cut
  l, s          copy FILES into REGISTER's clipboard and set paste's action to symlink
  h             copy FILES into REGISTER's clipboard and set paste's action to hardlink
```

```console
PASTE:
  v, V, p, P    paste FILES from REGISTER's clipboard, using custom COMMAND if defined
  C, Y          ignore paste's action, copy     FILES from REGISTER's clipboard
  X, D          ignore paste's action, cut      FILES from REGISTER's clipboard
  L, S          ignore paste's action, symlink  FILES from REGISTER's clipboard
  H             ignore paste's action, hardlink FILES from REGISTER's clipboard
```

```console
REGISTER if leave empty will use system clipboard,
otherwise it's name can be anything that doesn't include '/'.
```

Examples:

```console
~/
├─ 1/
├─ 2/
├─ foo
└─ bar
```

```sh
cd ~/
te x foo      # Cut foo
te ctest bar  # Copy bar to 'test' register

cd ~/1/
te p      # Paste foo then copy ~/1/foo
te ptest  # Paste bar from 'test' register
te ptest  # Paste bar from 'test' register again

cd ~/2/
te p # Paste foo from ~/1/foo
```

Result:

```console
~/
├─ 1/
│ ├─ foo
│ ├─ bar
│ └─ bar (2)
│
├─ 2/
│ └─ foo
│
└─ bar
```

## Configuration
Terminal explorer is configured through environment variables: `export TERMINALEXPLORER_<SETTING>="<value>"`

|Value|Invalid|Default|Description|
|-|-|-|-|
|`TERMINALEXPLORER_CLIPBOARD_SET_COMMAND`|`<commands>`|`clipb copy`|Command to set the clipboard|
|`TERMINALEXPLORER_CLIPBOARD_GET_COMMAND`|`<commands>`|`clipb paste`|Command to get the clipboard|
|`TERMINALEXPLORER_COPY_COMMAND`|`<commands>`|`cp`|Command to copy files|
|`TERMINALEXPLORER_CUT_COMMAND`|`<commands>`|`mv`|Command to cut files|
|||||
|`TERMINALEXPLORER_TEMPORARY`|`<path/to/file>`|`/tmp/terminal-explorer`|Temporary file's location|

Examples:

```sh
export TERMINALEXPLORER_CLIPBOARD_SET_COMMAND='xclip -in -selection clipboard'
export TERMINALEXPLORER_CLIPBOARD_GET_COMMAND='xclip -out -selection clipboard'
export TERMINALEXPLORER_COPY_COMMAND='rsync --recursive --archive -hh --partial --info=stats1 --info=progress2 --modify-window=1'
export TERMINALEXPLORER_CUT_COMMAND='rsync --recursive --archive -hh --partial --info=stats1 --info=progress2 --modify-window=1 --remove-source-files'
```

## Credits
Special thanks to:
- [**File URI Specification**](https://www.freedesktop.org/wiki/Specifications/file-uri-spec) by [Freedesktop.org](https://www.freedesktop.org)

<br><br><br><br>

---

> <h1 align="center">Made with :heart: by <a href="https://github.com/NNBnh"><i>NNB</i></a></h1>
>
> <p align="center"><a href="https://www.buymeacoffee.com/nnbnh"><img src="https://img.shields.io/badge/buy_me_a_coffee%20-%23F7CA88.svg?logo=buy-me-a-coffee&logoColor=333333&style=for-the-badge" alt="Buy Me a Coffee"></p>
