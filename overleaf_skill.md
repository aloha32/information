## overleaf
- [国内](cn.overleaf.com)
- [需要翻墙](www.overleaf.com)
- [在线latex公式编辑网址](latex.91maths.com)
- [在线表格转换网址](www.tablesgenerator.com)
- [练习作业参看答案](cn.overleaf.com/read/kttyzzzrsyjp)

## 一般不建立空白项目，上传官网模板zip。
- 空一行表示换行
- \section{} 表示罗马大标题Ⅰ、Ⅱ、Ⅲ。
- \subsection{} 表示二级标题，即ABCD
- 公式书写用 \begin{equation}  \end{equation} 包裹起来。
- 表格书写用 \begin{table}  \end{table} 包裹起来。
- 图片书写用 \begin{figure}  \end{figure} 包裹起来。

## 参考文献
在最后加上

\bibliographystyle{IEEEtran}      # IEEEtran指文章所用格式，bst文件
\bibliography{Mybib}              # Mybib指参考文献放在的文件中，bib文件

两行代码

谷歌学术进行引用时可以选择BibTex格式，粘贴至bib文件即可。

## 引用
- 文献引用时使用 \cite{tame2023quantum} # tame2023quantum好像是默认名称
- 图片引用时，先给图片用  \label{fig} 起个名字， 再使用 \ref{fig} 即可。
- 公式引用同图片，先起名字 \label{equ-01} ，再 \ref{equ-01} 即可。
