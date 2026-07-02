# Game Runner
Script to allow launching Steam installed games via `dmenu`-like window manager application launchers

## Dependencies
1. `steam`
2. `bash`
3. `wmenu` - you can use other launchers by tweaking the script, see [below](#usage)

## Usage
```
game-runner [-v path/to/libraryfolders.vdf] [-l launcher] 
```
1. You only need to supply the libraryfolders.vdf location if the script can't find it
2. If you want to use a launcher other than `wmenu`, specify it with the `-l` argument, eg `-l dmenu`

Tested with launchers `wmenu`, `dmenu` and `bemenu` but if your launcher of choice takes arbitrary lines from `stdin` and outputs the selection to `stdout` then it should work as well.

## Installation
Optional, but suggested: add the script to your $PATH

Add a hotkey in your window manager configuration to invoke the script. Example configuration line for sway:
```
bindsym $mod+g exec game-runner
```
