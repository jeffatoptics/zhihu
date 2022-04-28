#! https://zhuanlan.zhihu.com/p/506523935

# 用 jekyll minima 做一个 Github pages 日记模板

基于github的 theme [jekyll/minima](https://jekyll.github.io/minima/) ,做了一个日记模板
 [jeffatoptics/jeff-minima](https://jeffatoptics.github.io/jeff-minima/) , 模板也可以从Gitee上 [gitee jeffatoptics/jeff-minima](https://gitee.com/jeffatoptics/jeff-minima) 下来

## 目的

- 把 github pages 做一个基于个人日记网站，记录生活和工作日常以及读书笔记）

- 平时按日期时间自动在index发布链接，也可以自动按分类排序（工作，生活，读书等）自动排序

- 简单化，界面简单固定下来。本地只用Vscode,然后直接push发表。

- 支持手机大小的界面!可以缩小浏览

## 用法

- 用markdown写日记，在 `_posts` 目录里按`2022-04-27-主题名字.md` 起名写日记。

- 尽量用markdown 语法，而不是jekyll语法，特别是文件的引用上

## 改动以及效果

1. 删了一堆minima没必要的文件（应该是给本地预览用的）,改了两三个缺省参数，调正了大小

2. 按 [Jeklly 网站](https://jekyllrb.com/docs/posts/) 给出的三四行代码，直接copy做了一个category的page

模板效果如下:

![jeff-minima](https://pic4.zhimg.com/80/v2-b07de587e42e790c762525049052f332.gif)