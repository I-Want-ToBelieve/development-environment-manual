**请确保你已经完成了 [scoop 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

**如果你遇到了问题请提一个 issues.**

## 安装 golang

1. 按快捷键 `Win + X + I` 打开 powershell 终端窗口, 执行以下命令,以下载安装 golang:

    ```powershell
    sudo scoop install go -g
    ```

    下载安装完成后, 如果你在大陆的话, 很不幸你还需要一些额外的操作:

2. **(不在大陆可跳过)请确保你已经完成了[git 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E9%85%8D%E7%BD%AE-git)** 执行以下命令, 以下载安装 golang 依赖项:
    ```powershell
    mkdir -p $env:USERPROFILE\go\src\github.com\
    mkdir -p $env:USERPROFILE\go\src\golang.org\x
    cd $env:USERPROFILE\go\src\golang.org\x
    git clone git@github.com:golang/tools.git
    git clone git@github.com:golang/lint.git lint
    copy $env:USERPROFILE\go\src\golang.org\x\lint -Destination $env:USERPROFILE\go\src\github.com\golang\lint -Recurse
    cd $env:USERPROFILE\go\src\github.com\
    git clone git@github.com:mdempsky/gocode.git mdempsky/gocode
    git clone git@github.com:uudashr/gopkgs.git uudashr/gopkgs
    git clone git@github.com:ramya-rao-a/go-outline.git ramya-rao-a/go-outline
    git clone git@github.com:acroca/go-symbols.git acroca/go-symbols
    git clone git@github.com:derekparker/delve.git derekparker/delve
    git clone git@github.com:stamblerre/gocode.git stamblerre/gocode
    git clone git@github.com:rogpeppe/godef.git rogpeppe/godef
    git clone git@github.com:ianthehat/godef.git ianthehat/godef
    git clone git@github.com:sqs/goreturns.git sqs/goreturns
    git clone git@github.com:cweill/gotests.git cweill/gotests
    git clone git@github.com:fatih/gomodifytags.git fatih/gomodifytags
    git clone git@github.com:josharian/impl.git josharian/impl
    git clone git@github.com:davidrjenni/reftools.git davidrjenni/reftools
    git clone git@github.com:haya14busa/goplay.git haya14busa/goplay
    git clone git@github.com:karrick/godirwalk.git karrick/godirwalk
    git clone git@github.com:pkg/errors.git pkg/errors
    git clone git@github.com:go-delve/delve.git go-delve/delve
    git clone git@github.com:skratchdot/open-golang.git skratchdot/open-golang
    go install github.com/mdempsky/gocode
    go install github.com/uudashr/gopkgs/cmd/gopkgs
    go install github.com/ramya-rao-a/go-outline
    go install github.com/acroca/go-symbols
    go install golang.org/x/tools/cmd/guru
    go install golang.org/x/tools/cmd/gorename
    go install github.com/derekparker/delve/cmd/dlv
    go install github.com/stamblerre/gocode
    go install github.com/rogpeppe/godef
    go install github.com/ianthehat/godef
    go install github.com/sqs/goreturns
    go install golang.org/x/lint/golint
    go install github.com/cweill/gotests/...
    go install github.com/fatih/gomodifytags
    go install github.com/josharian/impl
    go install github.com/davidrjenni/reftools/cmd/fillstruct
    go install github.com/haya14busa/goplay/cmd/goplay
    ```

3. 执行以下命令,以验证安装:

    ```powershell
    go version
    ```

## 安装编辑器

Goland 与 vscode 二选一

### [Goland](https://www.jetbrains.com/go/)

1. 执行以下命令, 以添加 jetbrains bucket:

    ```powershell
    scoop bucket add jetbrains
    ```
2. 执行以下命令, 以下载安装 Goland
    ```powershell
    scoop install GoLand
    ```

### [vscode(visual studio code)](https://github.com/microsoft/vscode)

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
    "terminal.integrated.fontFamily": "Fira Code", // 终端字体
    "terminal.integrated.fontSize": 18, // 字体大小
    "workbench.colorCustomizations": { // 你可以自己修改终端主题颜色
        // panda theme
        "terminal.foreground": "#fffefe",
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

#### 扩展

- [适用于 VS Code 的中文（简体）语言包](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-zh-hans)
- [Settings Sync, 同步你的 vscode 扩展与设置](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)
- [Go 必装](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Go)
- [Guides, 为你的代码缩进添加各种缩进指南线](https://marketplace.visualstudio.com/items?itemName=spywhere.guides)
- [Project Manager, 项目管理, 功能有点多自己看介绍吧](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)
- [Rainbow Brackets, 对你代码中的括号添加颜色](https://marketplace.visualstudio.com/items?itemName=2gua.rainbow-brackets)

你可以在这里搜索你需要的扩展: [Visual Studio系列产品的扩展](https://marketplace.visualstudio.com/VSCode)

##### 配置 Go 扩展

1. 打开 vscode 编辑器
2. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `preferences: Open Settings(JSON)` 回车执行.
3. 在打开的 settings.json 文件中加入以下字段:
    ```json
      "go.autocompleteUnimportedPackages": true,
      "go.gocodePackageLookupMode": "go",
      "go.gotoSymbol.includeImports": true,
      "go.useCodeSnippetsOnFunctionSuggest": true,
      "go.inferGopath": true,
      "go.useCodeSnippetsOnFunctionSuggestWithoutType": true,
    ```

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

## Hello World

**请确保你已经安装了 [Go 必装](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Go) 扩展 **

**安装扩展后请确保你已经重启了 vscode**

1. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Terminal: Create New Integrated Terminal` 回车执行以打开集成终端.
2. 在集成终端窗口, 键入 `cd ~` 回车, 然后键入 `cd desktop` 回车.
3. 继续键入 `mkdir hello-world` 回车以在桌面创建 `hello-world` 文件夹, 然后键入 `cd hello-world` 回车.
4. 继续键入 `touch index.go` 回车以在 `hello-world` 文件夹中创建 `index.go` 文件.
5. 继续键入 `code .` 回车以使用 vscode 编辑器打开 `hello-world` 文件夹.
6. 复制以下代码到 `index.go` 文件中, 然后按快捷键 `Ctrl + S` 保存文件:

    ```go
    package main

    import (
      "fmt"
    )

    func main() {
      fmt.Println("hello go!")
    }
    ```
8. 选中 `index.go` 文件, 然后按快捷键 `F5` 进入调试模式.
10. 此时你应该看到 `hello go!` 在终端窗口中被打印出.
