# development-environment-manual

整理一些编程语言的开发环境搭建教程

**你需要使用 windows 7 及以上系统, 此教程以 windows 10 为例**

## 目录

- [VHDL](https://github.com/FloatingShuYin/development-environment-manual/blob/master/VHDL.md)
- [assembly](https://github.com/FloatingShuYin/development-environment-manual/blob/master/assembly.md)
- [c++](https://github.com/FloatingShuYin/development-environment-manual/blob/master/c%2B%2B.md)
- [c](https://github.com/FloatingShuYin/development-environment-manual/blob/master/c.md)
- [golang](https://github.com/FloatingShuYin/development-environment-manual/blob/master/golang.md)
- [groovy](https://github.com/FloatingShuYin/development-environment-manual/blob/master/groovy.md)
- [java](https://github.com/FloatingShuYin/development-environment-manual/blob/master/java.md)
- [javascript](https://github.com/FloatingShuYin/development-environment-manual/blob/master/javascript.md)
- [lisp](https://github.com/FloatingShuYin/development-environment-manual/blob/master/lisp.md)
- [matlab](https://github.com/FloatingShuYin/development-environment-manual/blob/master/matlab.md)
- [python](https://github.com/FloatingShuYin/development-environment-manual/blob/master/python.md)

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

## 配置 git

**你需要先去 github 或者 gitlab 官网注册账号**

## License

[![License: CC BY-NC-ND 3.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%203.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/3.0/)
