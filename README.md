<h1 align="center"><i>Terminal Explorer</i></h1>
<p align="center">Bring file manager's copy/paste to the CLI</p>
<p align="center"><img src="https://img.shields.io/github/license/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=for-the-badge" alt="License: GPL-3.0"> <img src="https://img.shields.io/github/languages/top/NNBnh/terminal-explorer?logo=gnu-bash&labelColor=073551&color=4EAA25&logoColor=FFFFFF&style=for-the-badge" alt="Shell: 100%"> <img src="https://img.shields.io/github/last-commit/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=for-the-badge"></p>
<p align="center"><img src="https://img.shields.io/github/watchers/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"> <img src="https://img.shields.io/github/stars/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"> <img src="https://img.shields.io/github/forks/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"> <img src="https://img.shields.io/github/issues/NNBnh/terminal-explorer?labelColor=073551&color=4EAA25&style=flat-square"></p>

## About
**Terminal explorer** is a files manager tool that mimic the way GUI's file manager do copy/cut/paste.

## Features

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
te PASTE[REGISTER] FILES
```

## Configuration
Terminal explorer is configured through environment variables: `export TERMINALEXPLORER_<SETTING>="<value>"`

|Value|Invalid|Default|Description|
|-|-|-|-|
|`CLIPBOARD_SET_COMMAND`|`<commands>`|`xclip -in -selection clipboard`|Command to set the clipboard|
|`CLIPBOARD_GET_COMMAND`|`<commands>`|`xclip -out -selection clipboard`|Command to get the clipboard|
|`TERMINALEXPLORER_COPY_COMMAND`|`<commands>`|`cp`|Command to copy files|
|`TERMINALEXPLORER_CUT_COMMAND`|`<commands>`|`mv`|Command to cut files|
|||||
|`TERMINALEXPLORER_TEMPORARY`|`<path/to/file>`|`/tmp/bfetch`|Temporary file's location|

## Credits
Special thanks to:
- [**Pure sh bible**](https://github.com/dylanaraps/pure-sh-bible) also by [Dylan](https://github.com/dylanaraps)

<br><br><br><br>

---

> <h1 align="center">Made with :heart: by <a href="https://github.com/NNBnh"><i>NNB</i></a></h1>
>
> <p align="center"><a href="https://www.buymeacoffee.com/nnbnh"><img src="https://img.shields.io/badge/buy_me_a_coffee%20-%23F7CA88.svg?logo=buy-me-a-coffee&logoColor=333333&style=for-the-badge" alt="Buy Me a Coffee"></p>
