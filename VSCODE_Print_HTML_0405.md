#! https://zhuanlan.zhihu.com/p/493313101

# Markdown Preview Enhanced (MPE) 输出不同主题 (theme) 的HTML和PDF

>问题: MPE 支持不同主题的预览风格(preview theme).但是按缺省配置,转成HTML和PDF时总是输出github-light.css风格

解决方法: `CTRL+,` 然后选择及改动MPE里缺省参数,Markdown-preview-enhanced: Print Background为enabled.

> Markdown-preview-enhanced: Print Background:
> ☑️Whether to print background for file export or not. If set to `false`, then `github-light` preview theme will be used. You can also set `print_background` in front-matter for individual files.

右键点击html或者pdf输出时候,输出文件与选择的预览风格一致

下图选择 Vue 风格的输出,并转为相同风格的PDF文档

1. `preview` 框里点右键 选择 `vue.css`

    ![Image](https://pic4.zhimg.com/80/v2-bc8fdaacf577ce2dafcf81418b438cd1.png)

1. 点右键 选择转 html或者pdf格式

    ![Image](https://pic4.zhimg.com/80/v2-c48f320cd3753c8f5412bf631322e382.png)

1. 打开转化的pdf文档

    ![Image](https://pic4.zhimg.com/80/v2-a2d7f952bb3e43337f7cd5d828a16e33.png)