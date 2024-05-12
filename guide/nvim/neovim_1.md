# NeoVim配置，来自知乎

- 首先安装字体, nerd fonts网站，<https://www.nerdfonts.com/>， 安装JetBrainsMono字体

- ubuntu24.04直接使用仓库安装neovim

  ``` yaml
    sudo apt install neovim
  ```

- 安装插件管理器

  ``` yaml
    git clone https://github.com/wbthomason/packer.nvim ~/.local/share/nvim/site/pack/packer/start/packer.nvim
  ```

- 创建 Neovim 配置目录，并且配置init.lua文件

  ``` yaml
    mkdir -p ~/.config/nvim
    vim ~/.config/nvim/init.lua
  ```

  ``` lua
    -- 使用 Packer.nvim 安装插件
    require('packer').startup(function()
        -- Packer 自身
        use 'wbthomason/packer.nvim'

        -- LSP 相关插件
        use 'neovim/nvim-lspconfig' -- nvim-lspconfig 插件
        use 'hrsh7th/nvim-compe' -- 补全插件

        -- 代码外观增强
        use 'kyazdani42/nvim-web-devicons'
        use 'glepnir/galaxyline.nvim'
    end)

    -- LSP 配置
    local lspconfig = require('lspconfig')

    -- C++ LSP 配置
    lspconfig.clangd.setup{}

    -- Python LSP 配置
    require'lspconfig'.pyright.setup {
        cmd = { "/home/zs/.virtualenvs/myenv/bin/pyright-langserver", "--stdio" }
    }

    -- nvim-compe 设置
    require'compe'.setup {
        enabled = true;            -- 启用补全
        autocomplete = true;       -- 自动完成
        min_length = 1;            -- 触发补全的最小字符数
        preselect = 'enable';      -- 自动选择第一个补全项
        throttle_time = 80;        -- 补全延迟时间（毫秒）
        source_timeout = 200;      -- 补全来源超时时间（毫秒）
        incomplete_delay = 400;    -- 补全延迟时间（毫秒）
        max_abbr_width = 100;      -- 补全项最大缩写宽度
        max_kind_width = 100;      -- 补全项最大类型宽度
        max_menu_width = 100;      -- 补全项最大菜单宽度
        documentation = true;      -- 显示补全项文档
    }

    -- 基础配置
    vim.cmd('syntax enable')         -- 启用语法高亮
    vim.cmd('filetype plugin indent on')  -- 启用文件类型检测和缩进

    -- 快捷键映射
    vim.api.nvim_set_keymap('n', '<F5>', '<Cmd>!g++ % -o %< && ./%< <CR>', { noremap = true, silent = true })  -- 编译 C++ 文件
    vim.api.nvim_set_keymap('n', '<F6>', '<Cmd>!python3 % <CR>', { noremap = true, silent = true })           -- 运行 Python 文件

    -- 外观设置
    vim.o.mouse = 'a'               -- 启用鼠标支持
    vim.o.termguicolors = true      -- 启用 24 位真彩色
    vim.o.background = 'dark'       -- 指定背景为暗色
    vim.cmd('colorscheme gruvbox')  -- 设置颜色主题

    vim.o.number = true             -- 显示行号

  ```

- 安装编程语言相关工具

  ``` yaml
    sudo apt install g++
    
    # 安装所需的语言服务器和其他工具，对于 C++，你需要安装 clangd：
    sudo apt install clang
    
    # 对于 Python，你需要安装 pyright
    sudo apt install python3-venv
    sudo apt install python3-pip
    
    python3 -m venv ~/.virtualenvs/myenv
    
    source ~/.virtualenvs/myenv/bin/activate  
    pip install pyright

  ```

- 安装 Gruvbox 颜色主题

  ``` yaml
    git clone https://github.com/morhetz/gruvbox.git ~/.config/nvim/pack/default/opt/gruvbox
  
  ```

- 启动 Neovim 和安装插件

  ``` yaml
    # 打开 Neovim：
    nvim 
    # 在 Neovim 中执行以下命令安装插件
    :PackerInstall
  ```
