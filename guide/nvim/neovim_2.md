# 我的NeoVim配置

## 准备工作

- 首先安装字体, nerd fonts网站，<https://www.nerdfonts.com/>， 安装JetBrainsMono字体

- 安装NeoVim
  - 可以直接apt仓库安装，但是版本可能比较低
  - 直接到github网站安装预编译的二进制可执行文件，然后配置环境变量；
    
    ``` yaml
      # 编辑~/.bashrc文件，在末尾添加路径即可
      export PATH=<你的要加入的路径>:$PATH

      # 如果有多个路径，只需要使用冒号分隔：
      export PATH=<你要加入的路径1>:<你要加入的路径2>:......:$PATH
    ```

## NeoVim配置文件

- 基本配置命令和说明
  - 创建配置文件和路径
    
    ``` yaml
      # 创建配置文件夹
      mkdir -p .config/nvim
      
      cd .config/nvim

      # 创建lua配置文件
      touch init.lua

      # nvim支持模块化的加载配置文件，可以将不同功能模块写到不同的文件中便于管理
      mkdir lua 
      cd lua 
      mkdir core 
      cd core 
      touch options.lua

    ```
  
  - 编写配置文件，使用lua语言编写
    - init.lua 文件编写，直接引用写好的配置模块文件

      ``` lua
        -- 直接引用，不需要加文件夹名称
        require("core.options")

      ```

    - options.lua文件编写

      ``` lua
        local opt = vim.opt
        
        -- 配置行号 
        opt.relativenumber = true
        opt.number = true

        -- 配置缩进
        opt.


      ```