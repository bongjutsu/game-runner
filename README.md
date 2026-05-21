# Game Runner
Script to allow launching Steam installed games via `wmenu`/`dmenu`/tiling WM application launcher

## How It Works
1. Run `game-runner`
2. Make a selection in the `wmenu` prompt that appears
3. ???
4. Profit

Steam maintains a file called `libraryfolders.vdf` which contains all of your Steam libraries. I have my games installed across multiple partitions, and thus use multiple libraries. First, the script processes `libraryfolders.vdf` to get all local libraries, then it iterates through those directories to parse the `appmanifest_XXXXXX.acf` files inside those libraries. The `appmanifest_XXXXXX.acf` files contain information about installed games - most notably for this use case, the `appid` and `name` keys. You can use `appid` values to launch games using Steam's own protocol - eg, `steam://rungameid//570` for Dota 2. But people prefer to read the `name`, so I convert that to lower case for autocompletion laziness, then when the script runs I can just type `dota` to autocomplete for dota 2, and we're off to the races.

## Troubleshooting
If you use this script, and for some reason your `libraryfolders.vdf` isn't in the same location as mine, you can provide it as a command line argument:
```
game-runner /path/to/your/Steam/libraryfolders.vdf
```

## Use with other launchers
My script assumes you use `wmenu` (because I use `wmenu`). Presumably you could just find/replace `wmenu` in the script with your launcher of choice, eg `dmenu`, but I haven't tested that, so that's a you problem.

## Final Words
I consider this script to be feature complete so I'm not expecting to publish any meaningful updates unless it breaks. Right now, it does have one bug - if you have a Steam library with no games, awk will throw an error for that library, and add a dummy option to the selection (it's just a colon). It doesn't have any meaningful effect - you can run installed games just fine, so I won't bother fixing it.
