# 🗃️ project.nvim

**project.nvim** is an all in one neovim plugin written in lua that provides
superior project management.

![Telescope Integration](https://user-images.githubusercontent.com/36672196/129409509-62340f10-4dd0-4c1a-9252-8bfedf2a9945.png)

## ⚡ Requirements

- Neovim >= 0.5.0

## ✨ Features

- Automagically cd to project directory using nvim lsp
  - Dependency free, does not rely on lspconfig
- If no lsp then uses pattern matching to cd to root directory
- Telescope integration `:Telescope projects`
  - Access your recently opened projects from telescope!
  - Asynchronous file io so it will not slow down vim when reading the history
    file on startup.
- Nvim-tree.lua support/integration

## 📦 Installation

Install the plugin with your preferred package manager:

### [vim-plug](https://github.com/junegunn/vim-plug)

```vim
" Vim Script
Plug 'ahmedkhalf/project.nvim'

lua << EOF
  require("project_nvim").setup {
    -- your configuration comes here
    -- or leave it empty to use the default settings
    -- refer to the configuration section below
  }
EOF
```

### [packer](https://github.com/wbthomason/packer.nvim)

```lua
-- Lua
use {
  "ahmedkhalf/project.nvim",
  config = function()
    require("project_nvim").setup {
      -- your configuration comes here
      -- or leave it empty to use the default settings
      -- refer to the configuration section below
    }
  end
}
```

## ⚙️ Configuration

**project.nvim** comes with the following defaults:

```lua
{
  -- Manual mode doesn't automatically change your root directory, so you have
  -- the option to manually do so using `:ProjectRoot` command.
  manual_mode = false,

  -- Methods of detecting the root directory. **"lsp"** uses the native neovim
  -- lsp, while **"pattern"** uses vim-rooter like glob pattern matching. Here
  -- order matters: if one is not detected, the other is used as fallback. You
  -- can also delete or rearangne the detection methods.
  detection_methods = { "lsp", "pattern" },

  -- All the patterns used to detect root dir, when **"pattern"** is in
  -- detection_methods
  patterns = { ".git", "_darcs", ".hg", ".bzr", ".svn", "Makefile", "package.json" },

  -- Table of lsp clients to ignore by name
  -- eg: { "efm", ... }
  ignore_lsp = {},

  -- When set to false, you will get a message when project.nvim changes your
  -- directory.
  silent_chdir = true,
}
```

To enable telescope integration:
```lua
require('telescope').load_extension('projects')
```

## 🤝 Contributing

- All pull requests are welcome.
- If you encounter bugs please open an issue.
