# A Quick Guide on Writing LaTeX in Neovim


In last post, I shared a minimal configuration of `LaTeX Workshop`.

<!--more-->

Now, I would like to share something about setting `Neovim` for
`VimTeX`, `texlab`, `LuaSnip` and auto-completion.

## Step 0: Preparations

### operating system

I am using `Neovim` on `macOS`, and these configurations should work well on `Linux`.

For `Windows` user, I recommend to install [WSL](https://doi.org/10.1070/IM8983).

### terminal

Use a modern terminal, such as `kitty`, `alacritty` and `iTerm2`.

On macOS, the next thing that I recommend you to do is installing `Homebrew`.

For the instructions, see [Homebrew](https://brew.sh).

If you are using an M1 Mac,
please check [here](https://mac.install.guide/homebrew/index.html) for more details,
especially export `/opt/homebrew/` to your `$PATH`.

If you are new to Neovim, I suggest you to start with [this configuration](https://github.com/nvim-lua/kickstart.nvim.git).

Or, [here](https://github.com/mathjiajia/config.nvim) is my current configuration.

### `TeX`

As in the last post, we need to install a `TeX` distribution.

### `Vim` / `Neovim` usage

Follow this [repo](https://github.com/iggredible/Learn-Vim).

## Step 1: VimTeX

VimTeX is a powerful tool to

## Step 2: LuaSnip

LuaSnip is a snippet engine, which provides the actual snippets
for various file types.

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

