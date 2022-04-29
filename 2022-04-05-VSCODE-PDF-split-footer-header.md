#! https://zhuanlan.zhihu.com/p/493494190

# Markdown Preview Enhanced (MPE) 输出PDF文档分页及页眉页脚

- [背景](#背景)
- [解决方法](#解决方法)
    - [分页](#分页)
    - [页眉页脚](#页眉页脚)
    - [一个例子](#一个例子)
        - [代码](#代码)
- [稍微复杂一点的页眉页脚](#稍微复杂一点的页眉页脚)
- [更复杂的页眉页脚](#更复杂的页眉页脚)
- [模板地址 (支持LOGO标识)](#模板地址-支持logo标识)
- [参考](#参考)


## 背景

MPE最为方便的两个文档输出工具是:

- html (offline): 内置
- Chrome(Puppeterr): PDF （按装Chrome浏览器)即可

![MPE输出pdf文档](https://pic4.zhimg.com/80/v2-0c118f498b12c6e9ace0f8f6d74798d3.png)

**输出pdf的缺省配置无法分页，没有页眉页脚。**

- 一个方法，用chrome或者edge打开html,可以勾选页眉页脚输出，但格式无法指定，并且打印一个文件路径名字在页脚，导致输出文档无法做正式交流用。Chrome不提供配置选项。
    ![chrome直接存成pdf文件](https://pic4.zhimg.com/80/v2-e5a516e56fe48bdcdb6d5747725a861d.png)


## 解决方法

### 分页

在markdown文件中分页，用html符号解决: `<div STYLE="page-break-after: always;"></div>`

不影响html显示，输出为pdf时候会分页

### 页眉页脚

- 定义chrome或者puppeteer配置参数 `headerTemplate`, `footerTemplate`,以及 `margin`，`displayHeaderFooter`

> ⚠️ 在`displayHeaderFooter`为true的情况下，如果`headerTemplate`, `footerTemplate`不做设置，或者设置不当，仍然不会显示页眉页脚。

具体例子参见[例子](#33-一个例子)章节。

### 一个例子

- 两页文档，分页。
- 页头居中，显示文档Title
- 页眉右边对起，显示当前页数和总页数

![页眉页脚](https://pic4.zhimg.com/80/v2-101aa995b89a92e9c80230abc6272dff.png)

#### 代码
```txt
---
title: This is Title
chrome:
    format: "A4"
    headerTemplate: '<div style="width:100%; text-align:center; border-bottom: 1pt solid #eeeeee; margin: 20px 10px 10px; font-size: 10pt"> 
    <span class=title></span></div>'
    footerTemplate: '<div style="width:100%; text-align:right; border-top: 1pt solid #eeeeee; margin:  10px 10px 20px; font-size: 8pt;"> 
    <span class=pageNumber></span> of <span class=totalPages></span></div>'
    displayHeaderFooter: true
    margin:
        top: '80px'
        bottom: '80px'
        left: '60px'
        right: '60px'
---

# Simple Demo of PDF 分页 页眉 页脚

## page 1

- text 1 
- text 1 
- text 1[^1]

[^1]: this is demo text 

`markdown分页` :

<div STYLE="page-break-after: always;"></div>

## page 2

- text 2
- text 2
- text 2

```
⚡⚡ 下列为必须设置 ⚡⚡:

- `displayHeaderFooter: true`

- `footerTemplate`/`headerTemplate` 的 `<div>` 中  `margin` 以及`font size`必须设置。`<div>`定义风格，其他通过<span>来增加属性参数及文本

- 可以定义多个`<div>` 注意 `width`配置

- `<span class=pageNumber>` 里输出文档属性参数 pageNumber, title, date, totalPages等。其他文字需用户手工定义输入

## 稍微复杂一点的页眉页脚

- 页眉分两部分
- 页脚分三部分

![多段页眉页脚](https://pic4.zhimg.com/80/v2-bca159c97a79d63c6afecc320e5c3715.png)

用下面的`footerTemplate`/`headerTemplate`取代上文
```
headerTemplate: '<div style="position: relative; width:100%; text-align:center; border-bottom: 1pt solid #eeeeee; margin: 30px 0px 10px; font-size: 10pt"></span>

<div style="position: absolute; width:100%; text-align: center; bottom: 5px;"><span class=title></div>

<div style="position: absolute; text-align: right; bottom: 5px;right: 20px;">version: 1.0</div>
</div>'
footerTemplate: '<div style="position: relative; width: 100%; text-align: left; border-top: 1pt solid #eeeeee; margin:  10px 0px 30px; font-size: 8pt;">
<div style="position: absolute; text-align: left; top: 5px;left: 60px;">YYYY-MM-DD</div>
<div style="position: absolute; width: 100%; text-align: center; top: 5px;">&copy;2022 ABCD</div>
<div style="position: absolute; text-align: right;top: 5px;right: 20px;"> <span class=pageNumber></span> of <span class=totalPages></span></div></div>'
```

## 更复杂的页眉页脚

输出HTML文档，通过word编辑
缺点是手工编辑，无法固定模式化。
![Word编辑HTML增加页眉](https://pic4.zhimg.com/80/v2-e9cb899f97fd79178585c86b91e1758f.png)

## 模板地址 (支持LOGO标识)

[模板地址](https://gitee.com/jeffatoptics/mpe-pdf-template)

在页眉增加 LOGO 标识

![vsc logo 页眉](https://pic4.zhimg.com/80/v2-a9bbb3303b717b24f2426e0211852827.png)

![输出pdf](https://pic4.zhimg.com/80/v2-4fc0b73b4d9e06d1c911cbd12bb4ba48.gif)

## 参考

1. [Github:Header and Footer with Puppeteer PDF? · Issue #142](https://github.com/shd101wyy/vscode-markdown-preview-enhanced/issues/142)

1. [puppeteer pdf 配置参数](https://github.com/GoogleChrome/puppeteer/blob/v1.8.0/docs/api.md#pagepdfoptions)   

1. [Github: Headers/Footers on PDF! · Issue #1028](https://github.com/shd101wyy/markdown-preview-enhanced/issues/1028)

1. [Github:mpe-puppeteer-header-footer-example](https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2Ftmori3y2%2Fmpe-puppeteer-header-footer-example)