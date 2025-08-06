# Neovim Configuration

This repository contains my personal configuration for Neovim. The configuration is based on setup [Kickstart](https://github.com/nvim-lua/kickstart.nvim).
To ease maintenance and readability, the plugin configuration has been cut into multiple files.

## Current version compatibility

Neovim 0.11.3

This repository will be updated for any Neovim new version.

## Features

- kanagawa-paper
- blink
- conform
- lualine
- nvim-lint
- nvim-treesitter
- telescope
- which-key
- nvim-lspconfig

## Installation

To set up the Neovim configuration on your system, you can follow the instructions below.

### Manual Installation

1. Install Neovim and the external dependencies:

   You will the following packages:
   - neovim
   - git
   - unzip
   - npm

   Both unzip and npm are mainly needed by Mason to install the LSP.
   Use your distribution package manager. In my case, I will be using pacman.

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

### Custom Ansible Lint Configuration

A custom Ansible lint configuration can be utilized. You can place the Ansible lint configuration file at the following location: [nvim-lspconfig.lua](https://github.com/Lamphie/neovim-dotfiles/blob/04135e6ce967b82f926ddecfb141cd1311b86ac5/lua/plugins/nvim-lspconfig.lua#L237).

For more details on configuring Ansible Lint, you can refer to the official documentation [here](https://ansible.readthedocs.io/projects/lint/configuring/).

### Adding a new feature/plugin

Any new plugin file added in the `~/.config/nvim/lua/plugins` will be loaded automatically thanks to [plugin call](https://github.com/Lamphie/neovim-dotfiles/blob/1b6a0262a6e784c85b03360bd89247c277ee3352/lua/config/lazy.lua#L23).
If you want do add a plugin, just copy an easy plugin file like [kanagawa-paper](https://github.com/Lamphie/neovim-dotfiles/blob/main/lua/plugins/kanagawa-paper.lua) and adjust to your new plugin.
