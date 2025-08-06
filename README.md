# Neovim Configuration

This repository contains my personal configuration for Neovim. The configuration is based on the setup [Kickstart](https://github.com/nvim-lua/kickstart.nvim).
To ease maintenance and readability, the plugin configuration has been cut into multiple files.

The aim of this repository is to provide a minimalist configuration for Neovim that works out-of-the-box.

## Current version compatibility

Neovim 0.11.3

This repository will be updated for any Neovim new version.

## Features

- [blink](https://github.com/Saghen/blink.nvim)
- [conform](https://github.com/stevearc/conform.nvim)
- [kanagawa-paper](https://github.com/thesimonho/kanagawa-paper.nvim)
- [lualine](https://github.com/nvim-lualine/lualine.nvim)
- [nvim-lint](https://github.com/mfussenegger/nvim-lint)
- [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)
- [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
- [telescope](https://github.com/nvim-telescope/telescope.nvim)
- [which-key](https://github.com/folke/which-key.nvim)

## Installation

To set up the Neovim configuration on your system, you can follow the instructions below.

### Manual Installation

1. Install Neovim and the external dependencies:

   You will the following packages:
   - neovim
   - git
   - unzip
   - npm
   - terraform or opentofu (optional)

   Both `unzip` and `npm` are mainly needed by Mason to install the LSP.
   Use your distribution package manager. In my case, I will be using pacman.

   For terraform/opentofu, it will be use by [conform](https://github.com/Lamphie/neovim-dotfiles/blob/56afc790d8447126ad285a42441e4a7a7db91e8f/lua/plugins/conform.lua#L52) to autoformat tf file.

   ```bash
   sudo pacman -S neovim git unzip npm
   ```

2. Make a backup of your current Neovim configuration:

   ```bash
   cp -r ~/.config/nvim/ ~/.config/nvim_backup
   ```

3. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/Lamphie/neovim-dotfiles.git ~/.config/nvim
   ```

## Configuration

### First use and periodic maintenance

The Neovim configuration use Lazy and Mason to ease the maintenance.
You will need to call `:Lazy` and `:Mason` from time to time to update plugin and LSP.

### Save your Neovim configuration

Put your Neovim configuration into a remote git repository like gitlab.com or github.com. Never try to install a plugin or LSP manually with `Lazy` or `Mason`.

Instead, make the change in the configuration file. That will tell `Lazy` and `Mason` to install the wanted plugin/LSP.

### Custom Ansible Lint Configuration

A custom Ansible lint configuration can be utilized. You can place the Ansible lint configuration file at the following location: [nvim-lspconfig.lua](https://github.com/Lamphie/neovim-dotfiles/blob/04135e6ce967b82f926ddecfb141cd1311b86ac5/lua/plugins/nvim-lspconfig.lua#L237).

For more details on configuring Ansible Lint, you can refer to the official documentation [here](https://ansible.readthedocs.io/projects/lint/configuring/).

### Adding a new feature/plugin

Any new plugin file added in the `~/.config/nvim/lua/p lugins` will be loaded automatically thanks to this [plugin call](https://github.com/Lamphie/neovim-dotfiles/blob/1b6a0262a6e784c85b03360bd89247c277ee3352/lua/config/lazy.lua#L23).
If you want to add a plugin, just copy an easy plugin file like [kanagawa-paper](https://github.com/Lamphie/neovim-dotfiles/blob/main/lua/plugins/kanagawa-paper.lua) and adjust to your new plugin.

### Adding and debugging a LSP

To add a LSP, do not install it manually with `Mason`. Instead, add the needed LSP [here](https://github.com/Lamphie/neovim-dotfiles/blob/56afc790d8447126ad285a42441e4a7a7db91e8f/lua/plugins/nvim-lspconfig.lua#L215).
`Mason` will install the LSP for you and `mason-lspconfig` will make it usable.

To debug a LSP installation, you can look at the error with `:Mason` but read the log file with `:MasonLog` or at `~/.local/state/nvim/mason.log`.

To debug a LSP, you just need to open a file with the right extension/filetype and then call `:LspInfo` to see it the LSP is correctly loaded.
