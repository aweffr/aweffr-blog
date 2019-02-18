---
title: git config --global 的记录被写到了哪里?
tags:
  - git
date: 2019-02-18 10:19:02
---


## 摘要
想知道配置项被写入了哪个路径/文件, 就打`git config --list --show-origin`.

<!--more-->

## 正文

首先, 从git v1开始 git config --list 命令就可以打印出所有目前生效的配置项.

```bash
$ git config --list
core.symlinks=false
core.autocrlf=true
core.fscache=true
color.diff=auto
color.status=auto
...
```

*git config 命令的man page见 {% link git文档 https://github.com/git/git/blob/70bd879ab66aeee809306908e3551d50cdf06802/Documentation/git-config.txt true %}*

其次, git-2.8 (2016, 三月) 发布之后, 就可以带上`--show-origin`参数, 在每行配置项上同步打印出该配置项来源的配置文件路径:
`Augment the output of all queried config options with the origin type (file, standard input, blob, command line) and the actual origin (config file path, ref, or blob id if applicable).`

```bash
$ git config --list --show-origin
file:"C:\\ProgramData/Git/config"       core.symlinks=false
file:"C:\\ProgramData/Git/config"       core.autocrlf=true
file:"C:\\ProgramData/Git/config"       core.fscache=true
file:"C:\\ProgramData/Git/config"       color.diff=auto
file:"C:\\ProgramData/Git/config"       color.status=auto
file:"C:\\ProgramData/Git/config"       color.branch=auto
file:"C:\\ProgramData/Git/config"       color.interactive=true
file:"C:\\ProgramData/Git/config"       help.format=html
file:"C:\\ProgramData/Git/config"       rebase.autosquash=true
file:C:/Program Files/Git/mingw64/etc/gitconfig http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
```

想知道user.name 或者 http.proxy配置到哪里了, 就可以加个管道 grep:

```bash
$ git config --list --show-origin | grep user.name
file:C:/Users/aweffr/.gitconfig user.name=aweffr
```
