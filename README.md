# development-environment-manual

整理一些编程语言的开发环境搭建教程

**你需要使用 windows 7 及以上系统, 此教程以 windows 10 为例.**
**如果你遇到了问题请提一个 issues.**

## 目录

- [VHDL](VHDL.md)
- [assembly](assembly.md)
- [c++](c%2B%2B.md)
- [c](c.md)
- [golang](golang.md)
- [groovy](groovy.md)
- [java](java.md)
- [javascript](javascript.md)
- [lisp](lisp.md)
- [matlab](matlab.md)
- [python](python.md)

## 安装 windows 包管理工具: [scoop](https://github.com/lukesampson/scoop)

1. 按快捷键 `Win + X + A` 打开 powershell 终端窗口
2. 复制这行命令到 powershell 终端窗口以修改执行策略: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
3. 复制以下代码配置安装目录,执行安装:

    ```powershell
    $env:SCOOP='D:\Applications\Scoop' # 局部安装目录, 你可以自行修改为合适的路径.
    [Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')

    $env:SCOOP_GLOBAL='C:\Scoop' # 全局安装目录, 你可以自行修改为合适的路径.
    [Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')

    iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
    ```

4. scoop下载安装完成后, 下载基础的软件包,请在 powershell 终端窗口执行以下命令:

    ```powershell
    scoop install sudo # 提权脚本
    sudo scoop install 7zip # 解压缩
    scoop install aria2 # 多线程下载
    ```

## 安装 google 的 chrome 浏览器

1. 在 powershell 终端窗口中执行以下命令, 以安装 chrome 浏览器
    ```
    scoop bucket add extras
    scoop install chrome
    ```
### chrome 扩展

- [Tampermonkey](https://www.gugeapps.net/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
- [扩展管理](https://www.gugeapps.net/webstore/detail/extension-manager/gjldcdngmdknpinoemndlidpcabkggco)
- [书签侧边栏](https://www.gugeapps.net/webstore/detail/bookmark-sidebar/jdbnofccmhefkmjbkkdkfiicjkgofkdh)
- [topy 书签管理与分享](https://www.gugeapps.net/webstore/detail/toby-for-chrome/hddnkoipeenegfoeaoibdmnaalmgkpip)

如果想安装扩展, 又不会科学上网的同学, 请使用 chrome 浏览器打开 [chrome 扩展镜像站](https://www.gugeapps.net/).

### Tampermonkey 脚本推荐

- [GitHub 汉化插件](chrome-extension://dhdgffkkebhmkfjojejmpbldmpobfkfo/ask.html?aid=8f6e62a0-d0a0-4954-8c47-f436baf330f7).建议英语不好的同学还是要学下英语哈

你可以在这里自行搜索 [Tampermonkey 脚本](https://greasyfork.org/zh-CN)

## 配置 git

**你需要先去 [github](https://github.com/join?source=header-home) 或者 [gitlab](https://gitlab.com/users/sign_in#register-pane) 官网注册账号**

1. 在 powershell 终端窗口中执行以下命令, 以安装 git 和  openssh 到全局目录:

    ```sudo scoop install git openssh -g```

2. 成功安装后, 在 powershell 终端窗口中执行以下命令, 以配置 git:

    ```powershell
    git config --global user.email example@gmail.com # 请将 example@gmail.com 替换为你注册 git 时使用的邮箱
    git config --global user.name  your username # 请将 your username 替换为你注册 git 时使用的用户名
    ```

3. 在 powershell 终端窗口中执行以下命令, 以配置 git ssh.

    ```powershell
    ssh-keygen -t rsa -C example@gmail.com # 请将 example@gmail.com 替换为你注册 git 时使用的邮箱
    ```
    你需要设置两次密码, 也可不设置直接按三次回车跳过

4. 在 powershell 终端窗口中执行以下命令, 打印出 git ssh 密钥, 并选中复制.

    ```powershell
    cat $env:userprofile\.ssh\id_rsa.pub
    ```

5. 打开 [github](https://github.com/settings/keys) 或者 [gitlab](https://gitlab.com/profile/keys) 将你的 ssh key 添加进去.

6. 按 快捷键 `Win + Q` 键入 `git bash`, 回车打开 bash 终端窗口, 键入 `ssh -T git@github.com` 或者 `ssh -T git@gitlab.com`

    如果打印出

    > Hi your user name! You've successfully authenticated, but GitHub does not provide shell access.

    或者

    > Welcome to GitLab, @your user name!

    则表示配置成功!

## 编程字体推荐

你可以在这里[在线查看字体效果](https://app.programmingfonts.org/)
你可以在这里[查看是否可以通过 scoop 下载你喜欢的字体](https://github.com/matthewjberger/scoop-nerd-fonts/tree/master/bucket)

添加字体的 bucket:

```powershell
scoop bucket add nerd-fonts
```

这里我推荐下载 FiraCode 字体,你也可以选择你喜欢的字体:

```powershell
sudo scoop install FiraCode-NF -g
```

## 贡献者

## License

[![License: CC BY-NC-ND 3.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%203.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/3.0/)
