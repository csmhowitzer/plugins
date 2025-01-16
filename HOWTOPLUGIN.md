# LUA PATH

LUA requires a $LUA_PATH environment variable
If one isn't set it will look at defaults based on where or how Lua was
installed
    - LuaRocks seems to be the plugin that will handle the install if only going
off of NeoVim. However a separate install won't ruin anything
        - MacOS works differently than linux in a few minor ways so exploring
this will help troubleshooting

## What path should you add?

In my most recent fix, I added to my terminal rc file **.zshrc**, and I used the
build in build-in lua path wild cards so that I could use Busted via
Plenary.nvim

```bash
export LUA_PATH="$HOME/plugins/?.nvim/lua/?.lua"
```

- **ALL** plugins ( *hopefully* ) will end with *".nvim"* for their directory name. 
- **ALL** Plugins according the the neovim plugin spec will have a lua directory
