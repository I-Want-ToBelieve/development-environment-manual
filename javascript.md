**请确保你已经完成了 [scoop 的安装](https://github.com/FloatingShuYin/development-environment-manual)**

## 安装 node 版本管理工具 nvm(node version management)

1. 在 powershell 终端窗口中执行以下命令, 以下载安装 nvm

    ```powershell
    sudo scoop install nvm -g
    ```
2. 执行以下命令, 以下载 node 最新长期支持版本 10.16.0.

    ```powershell
    nvm install 10.16.0
    ```
    如果下载卡住了, 请选中终端窗口敲击回车多次...
3. 下载完成后, 执行一下命令, 以使用 10.16.0 版本的 node.

    ```powershell
    sudo nvm use 10.16.0
    ```
    期间会弹出一次 UAC 获取权限的窗口, 请点击`是`给予管理员权限.

4. 执行以下命令, 以验证 node 是否成功安装.

    ```powershell
    node -v
    npm -v
    ```

    如果打印出:

    ```
    v10.16.0
    6.9.0
    ```

    则表示安装成功.如有问题请提一个 issuse.

## 安装编辑器: vscode(visual studio code)



1. 在 powershell 终端窗口中执行以下命令,以下载安装 vscode 便携版.

    ```powershell
    scoop bucket add extras
    scoop install vscode-portable
    ```

2. 要想验证安装,安装完成后, 键入 code 以打开 vscode 编辑器.

## 安装 vscode 插件





