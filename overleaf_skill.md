## overleaf
- [国内](cn.overleaf.com)
- [需要翻墙](www.overleaf.com)
- [在线latex公式编辑网址](latex.91maths.com)
- [在线表格转换网址](www.tablesgenerator.com)
- [练习作业参看答案](cn.overleaf.com/read/kttyzzzrsyjp)

## 模板下载
- [IEEE模板](http://www.ieee.org/publications_standards/publications/authors/author_templates.html)
- [通用模板](https://cn.overleaf.com/latex/templates)
- 百度、csdn自行寻找

## 一般不建立空白项目，上传官网模板zip。
- `\section{}` 表示罗马大标题Ⅰ、Ⅱ、Ⅲ。
- `\subsection{}` 表示二级标题，即ABCD
- 公式书写用 `\begin{equation}`  `\end{equation}` 包裹起来。
- 表格书写用 `\begin{table}`  `\end{table}` 包裹起来。
- 图片书写用 `\begin{figure}`  `\end{figure}` 包裹起来。
- `\begin{decument}`表示文件开始，上面部分为前言区，可以加入宏包
- 想要显示中文，需要在文档开头加入`\usepackage{xeCJK}`，并在menu菜单中的setting的compiler改为XeLaTex
- **换行符、换页符**：
  - 空一行表示换行
  - 段尾添加`\par`表示换行
  - 段尾`\\` 、`\newline` 、`\hfill \break` ，但是这三种方法的分段无法在段首自动缩进
  - `\newpage`表示换页
- **段落对齐**：
  - 居中：`\begin{center}` `\end{center}`包裹
  - 左对齐：`\begin{flushleft}` `\end{flushleft}`
  - 右对齐：`\begin{flushright}` `\end{flushright}`
- **字体设置**：
  - `\textbf{context}`加粗
  - `\underline{context}`下划线
  - `\textit{context}`斜体
  - `\textbf{textit{context}}`斜体加粗
  - 改变大小：
    - `{\tiny context}`
    - `{\scriptsize context}`
    - `{\footnotesize context}`
    - `{\small context}`
    - `{\normalsize context}`
    - `{\large context}`
    - `{\Large context}`
    - `{\LARGE context}`
    - `{\huge context}`
    - `{\Huge context}`

## 参考文献
在最后加上
```
\bibliographystyle{IEEEtran}      # IEEEtran指文章所用格式，bst文件
\bibliography{Mybib}              # Mybib指参考文献放在的文件中，bib文件
```
两行代码

谷歌学术进行引用时可以选择BibTex格式，粘贴至bib文件即可。

## 引用
- 文献引用时使用 `\cite{tame2023quantum} # tame2023quantum好像是默认名称`
- 图片引用时，先给图片用  `\label{fig}` 起个名字， 再使用 `\ref{fig}` 即可。`\pageref{fig}` 可以引用图像所在页码。
- 公式引用同图片，先起名字 `\label{equ-01}` ，再 `\ref{equ-01}` 即可。
- 图片加标题，在`\begin{figure}` 下面写 `\caption{example of a parametric plot}`。`\caption{example of a parametric plot}` 位于`\includegraphics{}`上方，则标题在图片上。反之在图片下。
- 一个figure想要对应两张图像时，需要导入`\usepackage{subcaption}` ，![image](https://github.com/user-attachments/assets/7e357c32-8f35-4ca9-ba36-5c626e1e8a57)
- 


## 固定位置图片
1. 新建一个images文件夹存放图像
2. `\usepackage{graphicx}`导入包
3. `\graphicspath{{./images/}}`指定图片保存路径
4. `\includegraphics{图片名（不带后缀）}`即可插入
5. `\includegraphics[scale=1.5,angle=45]{图片名（不带后缀）}`可以缩放和旋转（逆时针旋转角度）
6. `\includegraphics[width=3cm,height=4cm,right]{图片名（不带后缀）}`可以指定图像大小和位置。**使用此方法对齐需要在最开始导入`\usepackage[export]{adjustbox}`**

## 浮动位置图片
```
\begin{figure}[h]
\includegraphics[width=3cm,height=5cm]{universe}
\end{figure}
```
即可自动

## 文字包围图片
在要插入的图片上下插入`\begin{wrapfigure}{r}{0.25\textwidth}    # r表示右对齐，0.25表示图片包围盒的宽度（textwidth表示文本长度），即文本的四分之一长度。` `\end{wrapfigure}`
