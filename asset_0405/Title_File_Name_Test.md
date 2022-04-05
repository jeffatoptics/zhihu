---
chrome:
    format: "A4"
    headerTemplate: '<div style="width:100%; text-align:center; border-bottom: 1pt solid #eeeeee; margin: 2px 0px 10px; font-size: 8pt"> &copy;ABCD 2022 ABCD Internal Use <br> <br><span class=title></span></div>'
    footerTemplate: '<div style="width:50%; text-align:left; border-top: 1pt solid #eeeeee; margin:  10px 0px 10px; font-size: 8pt;">&nbsp; &nbsp; YYYY-MM-DD</div> <div style="width:50%; text-align:right; border-top: 1pt solid #eeeeee; margin:  10px 0px 10px; font-size: 8pt;"> <span class=pageNumber></span> of <span class=totalPages></span> &nbsp; &nbsp;</div>'
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


<div STYLE="page-break-after: always;"></div>

## page 3

- text 3

- text 3

