# Neovim Basic setup
- [**Kickstart**](https://github.com/nvim-lua/kickstart.nvim): Taking help from this git repo for the setup

## Adding Lazy package manager.
----
1. create a file `~/.config/nvim/init.lua`
2. now we will open the init.lua from the kickstart repo and paste the lazy nvim code.
```lua
-- [[ Install `lazy.nvim` plugin manager ]]
--    See `:help lazy.nvim.txt` or https://github.com/folke/lazy.nvim for more info
local lazypath = vim.fn.stdpath 'data' .. '/lazy/lazy.nvim'
if not (vim.uv or vim.loop).fs_stat(lazypath) then
  local lazyrepo = 'https://github.com/folke/lazy.nvim.git'
  local out = vim.fn.system { 'git', 'clone', '--filter=blob:none', '--branch=stable', lazyrepo, lazypath }
  if vim.v.shell_error ~= 0 then
    error('Error cloning lazy.nvim:\n' .. out)
  end
end ---@diagnostic disable-next-line: undefined-field
vim.opt.rtp:prepend(lazypath)

-- [[ Configure and install plugins ]]
--
--  To check the current status of your plugins, run
--    :Lazy
--
--  You can press `?` in this menu for help. Use `:q` to close the window
--
--  To update plugins you can run
--    :Lazy update
--
-- NOTE: Here is where you install your plugins.
require('lazy').setup({
  -- here we will add the plugins.
})
```
3. Save the file and exit
4. open the file with nvim and check if it show any error.

## Adding Neovim tree file structure.
---
1. Open the `~/.config/nvim/init.lua`.
2. [Nvim-neo-Tree](https://github.com/nvim-neo-tree/neo-tree.nvim). open this repo.
3. copy the Minimal example for lazy code block.
```lua
require('lazy').setup({
-- only copy the code inside the require('lazy').setup
{
    "nvim-neo-tree/neo-tree.nvim",
    branch = "v3.x",
    dependencies = {
      "nvim-lua/plenary.nvim",
      "nvim-tree/nvim-web-devicons", -- not strictly required, but recommended
      "MunifTanjim/nui.nvim",
      -- "3rd/image.nvim", -- Optional image support in preview window: See `# Preview Mode` for more information
    }
}
})
```
4. save and exit the file.
5. open the file in nvim and check of errors.

## Adding Nord color theme.
1. Open the `.config/nvim/init.lua`
2. add below code inside the `require('lazy').setup({`
```lua
require('lazy').setup({
--nvim-neo-tree code
},--noe-tree's code last line

-- nord color theme
{
'shaunsingh/nord.nvim',
lazy=false,
priority = 1000,
config = function()
	-- Example config in lua
	vim.g.nord_contrast = true
	vim.g.nord_borders = false
	vim.g.nord_uniform_diff_background = true
	vim.g.nord_bold = false

	-- load the colorscheme
	require('nord').set()
end
}
)
```
