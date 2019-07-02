**请确保你已经完成了 [scoop 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

**如果你遇到了问题请提一个 issues.**

## 安装 windows 第三方包管理工具: [choco](https://github.com/chocolatey/choco)

1. 按快捷键 `Win + X + A` 打开 powershell 终端窗口
2. 请在 powershell 终端窗口执行以下命令, 以设置 choco 安装目录:

    ```powershell
    $env:ChocolateyInstall='D:\Applications\Choco' # choco 安装目录, 你可以自行修改为合适的路径.
    [Environment]::SetEnvironmentVariable('ChocolateyInstall', $env:ChocolateyInstall, 'Machine')
    ```
3. 关闭当前终端窗口, 再次按快捷键 `Win + X + A` 打开 powershell 终端窗口, 执行以下命令, 以安装 choco:
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    ```
4. 执行 `choco -v` 以验证安装.

## 安装 C/C++ 编译器: mingw-w64

1. 执行以下命令, 以下载安装 mingw-w64:

    ```powershell
    choco install mingw -y
    ```
2. 执行 `choco list --local-only`, 以验证安装.

## 安装编辑器: [vscode(visual studio code)](https://github.com/microsoft/vscode)

1. 在 powershell 终端窗口中执行以下命令,以下载安装 vscode 便携版.

    ```powershell
    scoop bucket add extras
    scoop install vscode-portable
    ```

2. 要想验证安装,安装完成后, 在终端窗口键入 `code` 然后回车, 以打开 vscode 编辑器.
3. 为鼠标右键添加 vscode 的上下文菜单, 执行以下命令:
    ```powershell
    start "D:\Applications\Scoop\apps\vscode-portable\current\vscode-install-context.reg" # 请确保 D:\Applications\Scoop 是你安装 scoop 时设置的局部安装目录, 如有不同, 请修改为你自己的路径.
    ```

### 配置集成终端

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
    "terminal.integrated.fontFamily": "Fira Code", // 终端字体
    "terminal.integrated.fontSize": 18, // 字体大小
    "workbench.colorCustomizations": { // 你可以自己修改终端主题颜色
        // panda theme
        "terminal.foreground": "#ff75b5",
        "terminal.ansiBrightBlack": "#292a2b",
        "terminal.ansiBlack": "#676b79",
        "terminal.ansiBrightRed": "#ff75b5",
        "terminal.ansiRed": "#ff2c6d",
        "terminal.ansiBrightGreen": "#19f9d8",
        "terminal.ansiGreen": "#ff75b5",
        "terminal.ansiBrightYellow": "#ffcc95",
        "terminal.ansiYellow": "#ffb86c",
        "terminal.ansiBrightBlue": "#6fc1ff",
        "terminal.ansiBlue": "#45a9f9",
        "terminal.ansiBrightMagenta": "#b084eb",
        "terminal.ansiMagenta": "#72519c",
        "terminal.ansiBrightCyan": "#000000",
        "terminal.ansiCyan": "#6fc1ff",
        "terminal.ansiBrightWhite": "#e6e6e6",
        "terminal.ansiWhite": "#ffffff"
    },
```
5. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Terminal: Create New Integrated Terminal` 回车执行以打开集成终端.
6. 现在你应该看到底部的终端面板弹出.

### 扩展

- [适用于 VS Code 的中文（简体）语言包](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-zh-hans)
- [Settings Sync, 同步你的 vscode 扩展与设置](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)
- [C/C++, 必装](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- [Project Manager, 项目管理, 功能有点多自己看介绍吧](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)

你可以在这里搜索你需要的扩展: [Visual Studio系列产品的扩展](https://marketplace.visualstudio.com/VSCode)

### 主题

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

## Hello World

请参考:
- [在 Windows 下使用 Visual Studio Code 搭建 C 语言开发环境](https://hovenjay.github.io/2018/06/01/VSCodeC/#4-%E5%88%9B%E5%BB%BA%E5%92%8C%E8%AE%BE%E7%BD%AE-C-%E8%AF%AD%E8%A8%80%E5%BC%80%E5%8F%91%E5%B7%A5%E4%BD%9C%E5%8C%BA)
- [c++](c%2B%2B.md#hello-world)
