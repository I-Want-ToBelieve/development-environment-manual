**请确保你已经完成了 [scoop 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

**如果你遇到了问题请提一个 issues.**

## 安装 Rust

1. 按快捷键 `Win + X + A`, 以管理员权限打开 powershell 终端

2. 由于众所周知的原因, 先执行以下命令, 以设置清华镜像加速下载
    (**如果后续出现 429 错误, 请临时删除这两个环境变量: `del env:RUSTUP_DIST_SERVER;del env:RUSTUP_UPDATE_ROOT`**):
    ```powershell
    $env:RUSTUP_DIST_SERVER='https://mirrors.ustc.edu.cn/rust-static'
    [Environment]::SetEnvironmentVariable('RUSTUP_DIST_SERVER', $env:RUSTUP_DIST_SERVER, 'User')
    $env:RUSTUP_UPDATE_ROOT='https://mirrors.ustc.edu.cn/rust-static/rustup'
    [Environment]::SetEnvironmentVariable('RUSTUP_UPDATE_ROOT', $env:RUSTUP_UPDATE_ROOT, 'User')
    ```

3. 执行以下命令, 以下载安装 Rust 及其版本管理工具: rustup, 包管理工具(准确的说是项目构建工具): cargo, 文档工具: rustdoc
   **下载的东西有点多, 耐心等待, 偶尔需要敲一敲回车以轻微挪动方向盘, 因为你正在使用 Motor Vehicle Auto Driving System :)**

    ```powershell
    sudo scoop install rustup -g
    ```

4. 按快捷键 `ALT + F4` 关闭当前终端, 并按快捷键 `Win + X + A`, 以管理员权限打开一个 **新的** powershell 终端, 执行以下命令, 以验证安装:


    ```powershell
    rustc --version; cargo --version; rustdoc --version
    ```

5. 执行以下命令, 以下载 toolchain: stable-x86_64-pc-windows-gnu


    ```powershell
    rustup toolchain install stable-x86_64-pc-windows-gnu
    ```

6. 执行以下命令以打开 `settings.toml` 配置文件


    ```powershell
    notepad $env:scoop_global\apps\rustup\current\.rustup\settings.toml
    ```

7. 将 `settings.toml` 配置文件中的 `default_host_triple = "x86_64-pc-windows-msvc"` 修改为 `default_host_triple = "x86_64-pc-windows-gnu"`, 按快捷键 `Ctrl + S` 保存修改

8. 执行以下命令, 以下载 rust 源码: rust-src

    ```powershell
    rustup component add rust-src
    ```

9. 执行以下命令, 以下载 nightly 版本的 toolchain:

    ```
    rustup toolchain add nightly
    rustup update nightly
    ```

10. 执行以下命令, 以下载 [rls](https://github.com/rust-lang/rls/blob/e5c6f7262eb1cd5840276228600dc45e8063ef7a/README.md) 所依赖的组件:

    ```powershell
    rustup component add rls --toolchain nightly
    rustup component add rust-analysis --toolchain nightly
    rustup component add rust-src --toolchain nightly
    ```

11. 执行以下命令, 以下载 [racer](https://github.com/racer-rust/racer#configuration)
    (**前方高能: 要编译的东西有点多, 一核有难, 七核围观, 就当是 CPU 压力测试. XD**)
    ```powershell
    cargo +nightly install racer
    ```

12. 执行以下命令, 以设置 [racer](https://github.com/racer-rust/racer#configuration) 环境变量:

    ```powershell
    $env:RUST_SRC_PATH=$env:scoop_global + '\apps\rustup\current\.rustup\toolchains\nightly-x86_64-pc-windows-gnu\lib\rustlib\src\rust\src'
    [Environment]::SetEnvironmentVariable('RUST_SRC_PATH', $env:RUST_SRC_PATH, 'Machine')
    ```

13. 执行以下命令, 以验证安装:

    ```powershell
    racer complete std::io::B
    ```
14. **[在以管理员权限运行的 CMD 终端中, 执行以下命令, 创建符号链接(Symbolic link), 以正确引导源码映射(source Map):](https://github.com/rust-lang/rls/issues/472)**

    ```cmd
    mklink /d c:\rustc\a53f9df32fbb0b5f4382caaad8f1a46f36ea887c\src c:\Scoop\persist\rustup\.rustup\toolchains\nightly-x86_64-pc-windows-gnu\lib\rustlib\src\rust\src
    ```

## 安装 C/C++ 编译器: mingw-w64

1. 执行以下命令, 以下载安装 mingw-w64:

    ```powershell
    sudo scoop install gcc -g
    ```
2. 执行 `gcc -v`, 以验证安装.

## 安装编辑器: [vscode(visual studio code)](https://github.com/microsoft/vscode)

1. 在 powershell 终端窗口中执行以下命令,以下载安装 vscode 便携版.

    ```powershell
    scoop bucket add extras
    scoop install vscode-portable
    ```

2. 要想验证安装,安装完成后, 在终端窗口键入 `code` 然后回车, 以打开 vscode 编辑器.

3. 为鼠标右键添加 vscode 的上下文菜单, 执行以下命令:
    ```powershell
    start "C:\Support\Scoop\apps\vscode-portable\current\vscode-install-context.reg" # 请确保 C:\Support\Scoop 是你安装 scoop 时设置的局部安装目录, 如有不同, 请修改为你自己的路径.
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

### 扩展

- [适用于 VS Code 的中文（简体）语言包](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-zh-hans)
- [Settings Sync, 同步你的 vscode 扩展与设置](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)
- [Rust (rls), 必装](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust)
- [Native Debug](https://marketplace.visualstudio.com/items?itemName=webfreak.debug)
- [Rust language integration for VSCode](https://marketplace.visualstudio.com/items?itemName=kalitaalexey.vscode-rust)
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

### Hello World

**请确保 vscode扩展: [Rust (rls), 必装](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust) 已被安装**

1. 打开 vscode 编辑器, 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `preferences: Open Settings(JSON)` 回车执行.
2. 在打开的 settings.json 文件中加入以下字段, 然后按快捷键 `Ctrl + S` 保存更改:

    ```json
    "debug.allowBreakpointsEverywhere": true,
    "rust-client.channel": "stable",
    "rust.clippy_preference": "on",
    ```
3. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Terminal: Create New Integrated Terminal` 回车执行以打开集成终端.
4. 在集成终端窗口, 键入 `cd ~` 回车, 然后键入 `cd desktop` 回车.
5. 继续键入 `mkdir hello-world` 回车以在桌面创建 `hello-world` 文件夹, 然后键入 `cd hello-world` 回车.
6. 继续键入 `cargo init` 回车以在 `hello-world` 文件夹中初始化一个基本 rust 项目.
7. 继续键入 `code src/main.rs` 回车以使用 vscode 编辑器打开 `src` 目录下的 `main.rs` 文件.
8. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Tasks: Configure Default Build Task` 回车, 选择 `Rust: cargo build` 以打开 `tasks.json`文件.
9. 复制以下代码, 覆盖 `tasks.json` 文件中的内容, 然后按快捷键 `Ctrl + S` 保存文件:
    ```json
    {
        // 有关 tasks.json 格式的文档，请参见
        // https://go.microsoft.com/fwlink/?LinkId=733558
        "version": "2.0.0",
        "tasks": [
            {
                "label": "cargo build",
                "type": "cargo",
                "subcommand": "build",
                "problemMatcher": [
                    "$rustc"
                ],
                "group": {
                    "kind": "build",
                    "isDefault": true
                }
            }
        ]
    }
    ```
10. 按快捷键 `Ctrl + Shift + P` 打开命令面板, 在顶部弹出的命令面板中键入 `Debug: open launch.json` 选择 `GDB` 回车以打开 `launch.json`文件.
11. 复制以下代码, 覆盖 `launch.json` 文件中的内容, 然后按快捷键 `Ctrl + S` 保存文件:
    ```json
    {
        // 使用 IntelliSense 了解相关属性。
        // 悬停以查看现有属性的描述。
        // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
        "version": "0.2.0",
        "configurations": [
            {
            "name": "Debug",
            "type": "gdb",
            "request": "launch",
            "preLaunchTask": "cargo build",
            "target": "${workspaceRoot}\\target\\debug\\${workspaceRootFolderName}.exe",
            "cwd": "${workspaceRoot}",
            "valuesFormatting": "parseText",
            }
        ]
    }
    ```
12. 选中 `main.rs` 文件, 然后按快捷键 `F5` 进入调试模式.(或者在集成终端窗口中键入 `cargo run` 回车以编译执行)
13. 此时你应该看到控制台打印出: `Hello, world!`
14. 想了解在 vscode 中关于调试的更多的信息, 请看这篇文档: https://code.visualstudio.com/docs/editor/debugging



