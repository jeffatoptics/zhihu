#! https://zhuanlan.zhihu.com/p/493494190
# Markdown Preview Enhanced (MPE) 输出PDF文档分页及页眉页脚

## 参考

1. [Github:Header and Footer with Puppeteer PDF? · Issue #142](https://github.com/shd101wyy/vscode-markdown-preview-enhanced/issues/142)

1. [puppeteer pdf 配置参数](https://github.com/GoogleChrome/puppeteer/blob/v1.8.0/docs/api.md#pagepdfoptions)   

1. [Github: Headers/Footers on PDF! · Issue #1028](https://github.com/shd101wyy/markdown-preview-enhanced/issues/1028)

## 背景

MPE最为方便的两个文档输出工具是:

- html (offline): 内置
- Chrome(Puppeterr): PDF （按装Chrome浏览器)即可

![Image](https://pic4.zhimg.com/80/v2-0c118f498b12c6e9ace0f8f6d74798d3.png)

**输出pdf的缺省配置无法分页，没有页眉页脚。**

- 一个方法，用chrome或者edge打开html,可以勾选页眉页脚输出，但格式无法指定，并且打印一个文件路径名字在页脚，导致输出文档无法做正式交流用。Chrome不提供配置选项。
    ![Image](https://pic4.zhimg.com/80/v2-e5a516e56fe48bdcdb6d5747725a861d.png)


## 分页

在markdown文件中分页，用html符号解决: `<div STYLE="page-break-after: always;"></div>`

不影响html显示，输出为pdf时候会分页

## 页眉页脚

- 定义chrome或者puppeteer配置参数 `headerTemplate`, `footerTemplate`,以及 `margin`，`displayHeaderFooter`

> ⚠️ 在`displayHeaderFooter`为true的情况下，如果`headerTemplate`, `footerTemplate`不做设置，或者设置不当，仍然不会显示页眉页脚。

具体例子参见如下。

## 一个例子

- 两页文档，分页。 
- 页头居中，显示文档Title
- 页眉右边对起，显示当前页数和总页数


#### 代码
```txt
---
chrome:
    format: "A4"
    headerTemplate: '<div style="width:100%; text-align:center; border-bottom: 1pt solid #eeeeee; margin: 2px 10px 10px; font-size: 8pt"> This Is Title </span></div>'
    footerTemplate: '<div style="width:100%; text-align:right; border-top: 1pt solid #eeeeee; margin:  10px 10px 10px; font-size: 8pt;"> <span class=pageNumber></span> of <span class=totalPages></span></div>'
    displayHeaderFooter: true
    margin:
        top: '25mm'
        bottom: '25mm'
        left: '25mm'
        right: '25mm'
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



#### 效果

![Image](https://pic4.zhimg.com/80/v2-08d6bb7a663f2d5cb753eaeee9a2db52.png)


### 稍微复杂一点的页眉页脚

- 页眉分行
- 页脚 分两部分，左对齐写时间，右对齐写页数

用下面的`footerTemplate`/`headerTemplate`取代上文
```
    headerTemplate: '<div style="width:100%; text-align:center; border-bottom: 1pt solid #eeeeee; margin: 2px 0px 10px; font-size: 8pt"> &copy;ABCD 2022 ABCD Internal Use <br> <br><span class=title></span></div>'

    footerTemplate: '<div style="width:50%; text-align:left; border-top: 1pt solid #eeeeee; margin:  10px 0px 10px; font-size: 8pt;">&nbsp; &nbsp; YYYY-MM-DD</div> <div style="width:50%; text-align:right; border-top: 1pt solid #eeeeee; margin:  10px 0px 10px; font-size: 8pt;"> <span class=pageNumber></span> of <span class=totalPages></span> &nbsp; &nbsp;</div>'
```
效果如图
![Image](https://pic4.zhimg.com/80/v2-adc67537210de96e81806d24ba8ecb33.png)

### 更复杂的页眉页脚

- 用word打开html,然后手工排版，添加页眉页脚，然后存成pdf.这个方法用于解决复杂页眉页脚配置，但是手工调整，无法固定模式化。

![Image](https://pic4.zhimg.com/80/v2-e9cb899f97fd79178585c86b91e1758f.png)