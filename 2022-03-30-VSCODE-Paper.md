#! https://zhuanlan.zhihu.com/p/490547887

# 如何用 Vscode 简洁地写 Markdown 笔记

1. 限制编辑器(Editor) 数目
2. 切换预览(Toggle Preview) 快捷键
3. 按装Notes
4. 熟练用快捷键调用/关闭文件,放大缩小界面

## 1. 限制编辑器(Editor) 数目

想要达到的效果：点击新的文件查询信息时，自动关闭前面已经打开的文件。

背景：写笔记时，希望

- 一个编辑器界面专心写作

- 或者常用的双界面，编辑器界面以及预览界面。

- 偶尔选择多个其他文件打开参考，点击每个文件时，前面打开的文件会自动关闭。浏览完后，`CTRL+W`关掉，重新回到单界面，或者双界面工作。

- ![自动关闭](https://pic4.zhimg.com/80/v2-3a7c80af7e549d4c3272fd658386cf4e.gif)

解决方法 📝

- 左侧边栏选择⚙️, `Settings> Workbench >Editor Management`

    - `Limit: Enabled ☑️`
    - `Limit: Value: 2` 设置成2，或者3 (一个编辑，一个预览，另外一个供偶尔查其他文件用)

    ![Editor设置](https://pic4.zhimg.com/80/v2-fb6ed8d07287a30001981fdd0adb5019.png)

- 对preview界面选择 PIN

    ![PIN 模式](https://pic4.zhimg.com/80/v2-9df42bdcfa069f8179602645efb49bb8.png)


## 2. 切换预览(Toggle Preview) 快捷键

在单界面工作时候，有时候需要偶尔预览一下，`CTRL+K V`能自动打开预览界面。关掉预览的界面，却需要手工点击关闭。不是很顺畅。

与之鲜明对比，`CTRL+B` 切换左边栏，`CTRL+K Z`切换专注模式非常方便

📝解决思路：`CTRL+K V`后，快捷键 `CTRL+2`,`View:Focus Second Editor Group`，然后`CTRL+W`关闭，回到单界面工作

![Toggle Preview](https://pic4.zhimg.com/80/v2-3d7cee6f771493c08dbd078fbeec5ea4.gif)

## 3. Notes

安装Notes Extension,放在边栏。Notes里放两个文件

- 常用及特殊markdown配置，mermaid命令。供偶尔查找用

- 草稿文件。粘贴一些临时文字

![Notes](https://pic4.zhimg.com/80/v2-1adff2b072eca877f653327a5e009651.png)

## 4. 熟练用快捷键调用/关闭文件,放大缩小界面

- `CTRL+R` 打开目录

- `CTRL+P` 打开文件

- `CTRL+W` 关闭当前界面

- `CTRL+=`  放大

- `CTRL+-`  缩小

- `CTRL+home` 文章末尾

- `CTRL+end` 文章开头

- `CTRL+J`  进入Terminal

- `CTRL+Shift+M` Terminal Error输出

- `CTRL+K CTRL+S` 看快捷键

- `CTRL +,` 进入settings

- `CTRL + /`,切换comment

- `Alt+Shift+K`,切换block comment
