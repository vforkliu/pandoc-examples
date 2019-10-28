---
title: Pandoc 用户指南
author: LIU JUN
date: 2019.10.28
CJKmainfont: Heiti SC Light
mainfont: Helvetica
colorlinks: true
linkcolor: red
filecolor: Cyan
urlcolor: Navy
toccolor: Ivory3
geometry: top=2cm, bottom=1.5cm, left=2cm, right=2cm
---

# pandoc 安装
```bash
brew install pandoc
brew install pandoc-citeproc
brew install librsvg homebrew/cask/basictex
```
## 安装Tex
- 基本包地址：http://www.texts.io/support/0001/
- 全量包地址：https://tug.org/mactex/

## 使用tlmgr安装依赖
```bash
$sudo tlmgr install titling
$sudo tlmgr install lastpage
```

# pandoc 命令使用
`pandoc` [*options*] [*input-file*]...

- md转pdf 不含中文

`pandoc` sample.md -o sample.pdf

- md转pdf 含中文

`pandoc` sample.pdf --pdf-engine=xelatex -o sample.pdf -V mainfont="Heiti SC Light"


- md转pdf 含中文 使用模版
- 自动编号

--number-sections

- 链接添加颜色

-V colorlinks -V urlcolor=NavyBlue

- 导出模版

pandoc -D latex > default.tex

代码显示行号

pandoc --pdf-engine=xelatex sample.md -o sample.pdf   --number-sections -H listing-setup.tex --listings

系统已经安装的中文字体
```bash
fc-list :lang=zh 
```

代码块高亮
```bash
pandoc --pdf-engine=xelatex sample.md -o sample.pdf  --highlight-style breezedark
pandoc --pdf-engine=xelatex sample.md -o sample.pdf -N --highlight-style tango
pandoc --pdf-engine=xelatex sample.md -o sample.pdf --template=template.tex --highlight-style breezedark -N
```

列出支持的语言
```bash
pandoc --list-highlight-languages
```
列出支持的高亮模式
```bash
pandoc --list-highlight-styles
```

链接颜色
```bash
pandoc --pdf-engine=xelatex sample.md -o sample.pdf  \
    --highlight-style breezedark \
    -V colorlinks -V urlcolor=NavyBlue
```

修改边距
```bash
pandoc --pdf-engine=xelatex sample.md -o sample.pdf  \
    --highlight-style breezedark                     \
    -V colorlinks -V urlcolor=NavyBlue               \
    -V geometry:"top=2cm, bottom=1.5cm, left=2cm, right=2cm"
```

# 代码
```cpp
#include <iostream>
using namespace std;
int main(int argc,char* argv[]){
    cout << "Hello,World!" << endl;
    return 0;
}
```
# 图片

![test image](images/test.jpg){width=50%}
![test](images/test.jpg){width=50%}


# 列表

# 段落

# 引用

> 块引用。

# 数学公式

行内显示：$e=mc^2$

行间显示：$$\frac{df(x)}{dt}=lim_{x \to 0}{\frac{f(x+h)-f(x)}{h}}$$

# 表格

  Right     Left     Center     Default
-------     ------ ----------   -------
     12     12        12            12
    123     123       123          123
      1     1          1             1

Table:  Demonstration of simple table syntax.

# 参考文献
- [使用pandoc转换md为PDF并添加中文支持](https://www.jianshu.com/p/7f9a9ff053bb)
- [mac os 安装 pandoc markdown转docx,pdf](https://www.phodal.com/blog/mac-os-install-pandoc-markdown-convert-pdf-doc/)
- https://github.com/tzengyuxio/pages.git
- https://github.com/jgm/pandoc-templates.git
- https://github.com/martinkro/pandoc-tutorials.git
- [Generating Beautiful PDF from Markdown with Pandoc and Sublime Text](https://jdhao.github.io/2019/05/30/markdown2pdf_pandoc)
- [转化Markdown为PDF](http://shigaro.org/2019/01/02/pandoc-md-to-pdf/)
