**请确保你已经完成了 [scoop 的安装](https://github.com/FloatingShuYin/development-environment-manual#%E5%AE%89%E8%A3%85-windows-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7-scoop)**

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
    activate python37 # 或者在 bash 中 source activate python37
    ```

7. 退出 python3.x 环境
    ```powershell
    deactivate # 或者在 bash 中 source deactivate
    ```

## 安装编辑器: [vscode(visual studio code)](https://github.com/microsoft/vscode)

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
    start "D:\Applications\Scoop\apps\vscode-portable\current\vscode-install-context.reg" # 请确保 D:\Applications\Scoop 是你安装 scoop 时设置的局部安装目录, 如有不同, 请修改为你自己的路径.
    ```
#### 扩展

- [适用于 VS Code 的中文（简体）语言包](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-zh-hans)
- [python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

你可以在这里搜索你需要的扩展: [Visual Studio系列产品的扩展](https://marketplace.visualstudio.com/VSCode)
