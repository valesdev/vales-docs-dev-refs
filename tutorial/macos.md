## 系统偏好设置

1. 【通用】→勾选【关闭文稿时要求保存更改】
1. 【电池】→【电源适配器】→勾选【当显示器关闭时，防止电脑自动进入睡眠】
1. 【键盘】→【修饰键】→【大写锁定⇪键】→选择【Control】

## “访达”偏好设置

1. 【高级】→勾选【显示所有文件扩展名】
1. 【高级】→【将以下位置的文件夹保持在顶部】→勾选【按名次排序的窗口中】
1. 【高级】→【将以下位置的文件夹保持在顶部】→勾选【桌面上】
1. 【高级】→【执行搜索时】→选择【搜索当前文件夹】

## 包管理器

[Homebrew 官方网站](https://brew.sh/)

初次安装：

```shell
$ brew doctor
```

常用包：

```shell
$ brew install coreutils findutils bash zsh curl wget gzip zip unzip p7zip git
```

常用 SDK：

```shell
$ brew install python ruby nodejs
```

环境 `PATH` 配置：

```shell
export PATH="/usr/local/opt/coreutils/libexec/gnubin:$PATH"
export PATH="/usr/local/opt/findutils/libexec/gnubin:$PATH"
export PATH="/usr/local/opt/python/libexec/bin:$PATH"
export PATH="/usr/local/opt/zip/bin:$PATH"
export PATH="/usr/local/opt/unzip/bin:$PATH"
export PATH="/usr/local/opt/ruby/bin:$PATH"
export PATH="/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"
```

## Shell

[Oh My Zsh 官方网站](https://ohmyz.sh/)

Oh My Zsh 禁用更新提示

```
DISABLE_AUTO_UPDATE="true"
```

Oh My Zsh 跳过目录安全检查

```
ZSH_DISABLE_COMPFIX="true"
```

## App

- [CheatSheet](https://www.mediaatelier.com/CheatSheet/)
- [CleanMyMac](https://macpaw.com/cleanmymac)
- [Alfred](https://www.alfredapp.com/)
- [Xee](https://theunarchiver.com/xee)
- [The Unarchiver](https://macpaw.com/the-unarchiver)
- [Moom](https://manytricks.com/moom/)
- [mpv](https://mpv.io/installation/)
- [Vox](https://vox.rocks/mac-music-player)
- [Skitch](https://evernote.com/intl/zh-cn/products/skitch)
- [Microsoft NTFS for Mac by Paragon Software](https://www.paragon-software.com/home/ntfs-mac/)

## 常用 Shell 别名定义

```shell
alias ll="ls --all --color=auto -l --human-readable"
```

## 常用 Shell 命令

将程序坞的图标大小设置为 36 像素

```shell
$ defaults write com.apple.dock tilesize -int 36
```

一键配置环境 HTTP 代理

```shell
$ export HTTP_PROXY=http://127.0.0.1:8118 && export HTTPS_PROXY=http://127.0.0.1:8118
```

一键解除配置环境 HTTP 代理

```shell
$ unset HTTP_PROXY && unset HTTPS_PROXY
```

一键更新 Homebrew 及其包

```shell
$ brew update --verbose && brew upgrade --verbose && brew cleanup --verbose --prune=all && rm --force --recursive --verbose '$(brew --cache)'
```

压缩打包（7z 格式、不压缩、连续）

```shell
$ 7z a -t7z -mx=0 -ms=on
```

压缩打包（7z 格式、最高等级压缩、连续）

```shell
$ 7z a -t7z -mx=9 -ms=on
```

压缩打包（7z 格式、不压缩）

```shell
$ 7z a -tzip -mx=0
```

压缩打包（7z 格式、最高等级压缩）

```shell
$ 7z a -tzip -mx=9
```
