**请确保你已经完成了 [scoop 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

**如果你遇到了问题请提一个 issues.**

## 安装 python 版本管理工具

python 的版本管理, 有两个解决方案, 可简单的分为轻量级和重量级, **请自行考虑选择其中一种**

### 轻量级(43MB): 使用 scoop 管理你的 python 版本

scoop 下载了 python 2.x 与 python 3.x 两个版本, 除此之外没有下载其他东西.

1. 按快捷键 `Win + X + I` 打开 powershell 终端窗口, 执行以下命令, 以添加 versions bucket 到 scoop:
    ```powershell
    scoop bucket add versions # add the 'versions' bucket if you haven't already
    ```
2. 执行以下命令, 以下载安装 python 2.x 与 python 3.x 到 scoop 全局目录:
    ```powershell
    sudo scoop install python27 python -g
    ```
    如果下载卡住了, 请敲击回车多次...
3. 下载安装完成后, 执行以下命令, 查看 python 版本:
    ```powershell
    python --version
    ```
4. 切换到 python 3.x:
    ```powershell
    sudo scoop reset python
    ```

5. 切换到 python 2.x:
    ```powershell
    sudo scoop reset python27
    ```

### 重量级(1GB +): 使用 [anaconda](https://www.anaconda.com/) 管理你的 python 版本

anaconda 之所以这么大, 是因为它集成了 python 的运行环境, 并集成了 100+ 的第三方库.

你可以在这里查看 [anaconda 的介绍信息](https://www.anaconda.com/why-anaconda/)
了解更多: [Anaconda介绍、安装及使用教程](https://zhuanlan.zhihu.com/p/32925500)

anaconda 分 anaconda2 与 anaconda3 两个版本.
如果你主用 python 2.x 就装 anaconda2, 主用 python 3.x 就装 anaconda3.

这里以 anaconda2 为例

1. 执行以下命令, 以添加 versions bucket 到 scoop:
    ```powershell
    scoop bucket add versions # add the 'versions' bucket if you haven't already
    ```
2. 执行以下命令, 以下载安装 anaconda:
    ```powershell
    scoop install anaconda2 # 或者 scoop install anaconda3
    ```
3. 执行以下命令, 以设置 anaconda 在清华服务器的 conda 仓库镜像:
    ```powershell
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    conda config --set show_channel_urls yes
    ```
4. 执行以下命令, 以更新 conda:
    ```powershell
    conda update conda
    ```
    如果提示: Proceed ([y]/n)?
    请键入 `y` 回车继续.

5. 执行以下命令, 以创建 python2.x 或者 python3.x 环境选项:
    ```powershell
    sudo conda create --name python37 python=3.7 # 或者 sudo conda create --name python27 python=2.7
    ```
    如果下载卡住了, 请敲击回车多次...
6. 激活 python3.x 环境
    ```powershell
    conda activate python37
    ```

7. 退出 python3.x 环境
    ```powershell
    conda deactivate
    ```

## 安装编辑器

python 的编辑器, 我只推荐以下 2 个. **请自行考虑选择其中一种**

### [PyCharm](https://www.jetbrains.com/pycharm/)

这是一款专为 python 开发的 IDE, 分为 社区版(免费) 与 Pro版(收费).

1. 按快捷键 `Win + X + I` 打开 powershell 终端窗口, 执行以下命令,以下载安装PyCharm:
    ```powershell
    scoop install pycharm
    ```
2. 要想验证安装,安装完成后, 在终端窗口键入 `pycharm` 以打开 pycharm 编辑器.

### [vscode(visual studio code)](https://github.com/microsoft/vscode)

vscode 是一款微软创建的基于 Electron 架构的开源应用, 拥有繁荣的社区生态.

1. 在 powershell 终端窗口中执行以下命令,以下载安装 vscode 便携版.

    ```powershell
    scoop bucket add extras
    scoop install vscode-portable
    ```

2. 要想验证安装,安装完成后, 在终端窗口键入 `code` 以打开 vscode 编辑器.
3. 为鼠标右键添加 vscode 的上下文菜单, 执行以下命令:
    ```powershell
    start "C:\Support\Scoop\apps\vscode-portable\current\vscode-install-context.reg" # 请确保 C:\Support\Scoop 是你安装 scoop 时设置的局部安装目录, 如有不同, 请修改为你自己的路径.
    ```

#### 配置集成终端

**请确保你已经完成了[git 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E9%85%8D%E7%BD%AE-git)**

1. 打开 vscode 编辑器
2. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `preferences: Open Settings(JSON)` 回车执行.
3. 在打开的 settings.json 文件中加入以下字段:
```json
    "terminal.integrated.shell.windows": "C:\\Scoop\\apps\\git\\current\\bin\\bash.exe", // 请确保路径为你自己的 git 安装路径
    "terminal.integrated.shellArgs.windows": [
        "--login",
        "-i"
    ],
    "terminal.external.windowsExec": "C:\\Scoop\\apps\\git\\current\\bin\\bash.exe", // 请确保路径为你自己的 git 安装路径
    "terminal.integrated.cursorStyle": "underline", // 终端光标样式
    "terminal.integrated.cursorBlinking": true,
    "terminal.integrated.fontFamily": "'Fira Code', 'Sarasa Mono T CL', 'Cascadia Code', 'Hack'", // 终端字体
    "terminal.integrated.fontSize": 18, // 字体大小
    "workbench.colorCustomizations": { // 你可以自己修改终端主题颜色
        // tomorrow light theme
        "terminal.foreground": "#4d4d4c",
        // "terminal.background": "#ffffff",
        "terminal.ansiBrightBlack": "#000000",
        "terminal.ansiBlack": "#000000",
        "terminal.ansiBrightRed": "#c82829",
        "terminal.ansiRed": "#c82829",
        "terminal.ansiBrightGreen": "#718c00",
        "terminal.ansiGreen": "#718c00",
        "terminal.ansiBrightPurple": "#8959a8",
        "terminal.ansiPurple": "#8959a8",
        "terminal.ansiBrightYellow": "#eab700",
        "terminal.ansiYellow": "#eab700",
        "terminal.ansiBrightBlue": "#4271ae",
        "terminal.ansiBlue": "#4271ae",
        "terminal.ansiBrightMagenta": "#b084eb",
        "terminal.ansiMagenta": "#72519c",
        "terminal.ansiBrightCyan": "#3e999f",
        "terminal.ansiCyan": "#3e999f",
        "terminal.ansiBrightWhite": "#4EC5F1",
        "terminal.ansiWhite": "#ffffff"
    },
      // 英文会使用 Fira Code 中文会使用 Sarasa Mono T CL
    "editor.fontFamily": "'Fira Code', 'Sarasa Mono T CL', 'Cascadia Code', 'Hack'",
```
5. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Terminal: Create New Integrated Terminal` 回车执行以打开集成终端.
6. 现在你应该看到底部的终端面板弹出.

#### 扩展

- [适用于 VS Code 的中文（简体）语言包](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-zh-hans)
- [Settings Sync, 同步你的 vscode 扩展与设置](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)
- [python, 必装](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Project Manager, 项目管理, 功能有点多自己看介绍吧](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)


你可以在这里搜索你需要的扩展: [Visual Studio系列产品的扩展](https://marketplace.visualstudio.com/VSCode)

#### 主题

我推荐几个很多人在用的主题...

- [Atom One Dark Theme](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-theme-onedark)

    ![Atom One Dark Theme](https://raw.githubusercontent.com/akamud/vscode-theme-onedark/master/screenshots/preview.png)

- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)

    ![Material Icon Theme](https://raw.githubusercontent.com/PKief/vscode-material-icon-theme/master/images/fileIcons.png)

- [Horizon Theme](https://marketplace.visualstudio.com/items?itemName=jolaleye.horizon-theme-vscode)

    ![Material Icon Theme](https://raw.githubusercontent.com/jolaleye/horizon-theme-vscode/master/preview.png)

- [Noctis](https://marketplace.visualstudio.com/items?itemName=liviuschera.noctis)

    ![Noctis Lux](https://github.com/liviuschera/noctis/raw/master/images/noctisLux.png)

用着这么养眼的主题,写代码简直就是一种享受...

想自己找找主题? [主题](https://marketplace.visualstudio.com/search?term=theme&target=VSCode&category=All%20categories&sortBy=Relevance)

### Hello World

1. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Terminal: Create New Integrated Terminal` 回车执行以打开集成终端.
2. 在集成终端窗口, 键入 `cd ~` 回车, 然后键入 `cd desktop` 回车.
3. 继续键入 `mkdir hello-world` 回车以在桌面创建 `hello-world` 文件夹, 然后键入 `cd hello-world` 回车.
4. 继续键入 `touch index.py` 回车以在 `hello-world` 文件夹中创建 `index.py` 文件.
5. 继续键入 `code .` 回车以使用 vscode 编辑器打开 `hello-world` 文件夹.
6. 复制 `print('Hello World!')` 到 `index.py` 文件中, 然后按快捷键 `Ctrl + S` 保存文件.
7. 鼠标选中集成终端, 键入 `python index.py` 回车以执行 `index.py` 脚本文件.
8. 你应该看到 `Hello World!` 在终端窗口中被打印出.
9. 在 vscode 中 调试 python 请看这篇文档: https://code.visualstudio.com/docs/python/debugging
