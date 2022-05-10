# A Quick Guide on Writing LaTeX in Neovim


In last post, I shared a minimal configuration of `LaTeX Workshop`.

<!--more-->

Now, I would like to share something about setting `Neovim` for
`VimTeX`, `texlab`, `LuaSnip` and auto-completion.

This may not be suitable for everyone, especially for those who are not familiar with [TUI](https://en.wikipedia.org/wiki/Text-based_user_interface).

## Step 0: Preparations

### operating system

I am using `Neovim` on `macOS`, and these configurations should also work well on `Linux`.

For `Windows` user, I recommend to install [WSL](https://doi.org/10.1070/IM8983).

### terminal

Use a modern terminal, such as `kitty`, `alacritty` and `iTerm2`.

On macOS, the next thing that I recommend you to do is installing `Homebrew`.
[Here](https://brew.sh) is the installation guide.

If you are using an M1 Mac,
please check [here](https://mac.install.guide/homebrew/index.html) for more details,
especially export `/opt/homebrew/` to your `$PATH`.

### `TeX`

As in the [last post](https://mathjiajia.github.io/vscode-and-latex/), we need to install a `TeX` distribution.

For `macOS` users, you may download `mactex-no-gui` via `Homebrew`:

```sh
brew install mactex-no-gui
```

### Install `Neovim`

[Here](https://github.com/neovim/neovim/wiki/Installing-Neovim) is the official instructions for installing `Neovim` on different platforms.

For `macOS` users, you can install `Neovim` with `Homebrew`:

```sh
brew install neovim
```

Note that `Neovim 0.7` was released on April 15, 2022.
Please ensure that you have the correct version (>= 0.7).

### `Vim` / `Neovim` usage

Since `Neovim` is a fork of `Vim`, the basic usage is the same.

Follow this [repo](https://github.com/iggredible/Learn-Vim) to learn how to use `Vim` and `Neovim`.

If you are new to Neovim, I suggest you to start with [this configuration](https://github.com/nvim-lua/kickstart.nvim.git).

[Here](https://github.com/mathjiajia/config.nvim) is my current configuration.

### `Lua` *(optional)*

Since `Lua` is the first-class language in `Neovim`, some basic knowledge of `Lua` will be better.
If you want to costuming your own `Neovim`, you may want to learn [nvim-lua-guide](https://github.com/nanotee/nvim-lua-guide).

## Step 1: VimTeX

VimTeX is a powerful tool to

## Step 2: LuaSnip

LuaSnip is a snippet engine, which provides the actual snippets
for various file types.

I will use the following examples to explain how to use `LuaSnip`.

```lua
s({ trig = 'mk', name = 'inline math', dscr = 'Insert inline Math Environment.' }, {
        t '\\(',
        i(1),
        t '\\)',
    }, {
        condition = tex.in_text,
        callbacks = {
            [-1] = { [events.leave] = appended_space_after_insert },
        },
    })
```

I set `mk` as the trigger for inline math environments.
Also, this is an auto-sinppet, which means that you can just type `mk` and it will be replaced with `\(|\)` automatically.
Note that `|` above is used to indicate the position of the cursor.
After the `mk` is typed, you can type the math formulas you need and then press `Ctrl + j` to escape the inline math environment.
Now the real magic is here.
After escaping the inline math environment, you will see something like this: `\(formula\)|`, where `|` is the cursor as before.
Then `LusSnip` with insert `space` when the next character after snippet is a letter.
Note that for `non-letter` characters, `LusSnip` will not insert `space`.

```lua
s({ trig = 'ref', name = 'cross refrence' }, {
        t '\\cite[',
        i(1),
        t ']{',
        i(2),
        t '}',
    }, {
        condition = tex.in_text,
        show_condition = tex.in_text,
        callbacks = {
            [2] = {
                [events.enter] = function()
                    require('telescope').extensions.bibtex.bibtex(
                        require('telescope.themes').get_dropdown { previewer = false }
                    )
                end,
            },
        },
    })
```

I use `ref` as the trigger for cross-references snippet.
Because cross-references are not often used in the text, I set `ref` as a normal snippet:
after typing `ref`, you need to press `Ctrl + j` to expand the snippet and get something like `\cite[|]{}`.
Then you can input some text in the square brackets, and then press `Ctrl + j` to jump to the curly braces.
According to the settings, you will see a dropdown with the list of all the references in the document.
This is a powerful feature, thanks to `LuaSnip` and `telescope-bibtex`.

## Step 3: cmp

When writing LaTeX source files, auto-completion is crucial for fast editing
and improve our efficiency dramatically.
VimTeX and LSP support auto-completion.

## TODO

- [ ] finish Preparations
- [ ] finish VimTeX
- [ ] finish LuaSnip
- [ ] finish cmp

## References

1. [A Complete Guide on Writing LaTeX with Vimtex in Neovim](https://jdhao.github.io/2019/03/26/nvim_latex_write_preview/)

1. [How I'm able to take notes in mathematics lectures using LaTeX and Vim](https://castel.dev/post/lecture-notes-1/)

1. [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim.git)

1. [config.nvim](https://github.com/mathjiajia/config.nvim)

1. ...

