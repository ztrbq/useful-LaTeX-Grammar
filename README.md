

# Useful LaTeX Grammar

## Decription

This file is supposed to give some useful LaTeX grammar templates, which can be directly copied to the essay or paper writing.

## Packages

``` latex
\usepackage{cite} %引用
\usepackage[UTF8, heading = false, scheme = plain]{ctex} %中文设置
\usepackage[english]{babel} %英语字符格式
\usepackage{authblk} %封面作者格式
\usepackage{indentfirst} %行缩进
\usepackage{amsmath} %数学
\usepackage{graphicx} %绘图
\usepackage[colorlinks=true, allcolors=blue]{hyperref} %超链接颜色等设定
\usepackage{tikz} %tikz绘图
\usepackage{multicol} %多行表格
\usepackage{pgfplots} %tikz绘图所用属性设置
\usepackage{subfigure} %子图
\usepackage{caption} %图、表格的标题
\usepackage{amssymb} %特殊数学符号
```

## Basic

### __文章信息__

```latex
\documentclass{article} %article模版
\title{} %文章标题
\author{} %作者姓名
\affil{} %机构
```

### __正文内容__

```latex
\begin{document}
\maketitle

\begin{abstract}
%%%%%%%%%%%%%%%%%%%%%%
%在这里写入你的abstract%
%%%%%%%%%%%%%%%%%%%%%%
\end{abstract}

\tableofcontents %目录
\newpage

\section{}
\subsection{}
%%%%%%%%%%%%%%%%%%%%%%
%%%在这里写入你的正文%%%%
%%%%%%%%%%%%%%%%%%%%%%

\bibliographystyle{IEEEtran}
\bibliography{refs}

\end{document}
```

### __数学公式__ 

```latex
\begin{gather}
%%%%%%%%%%%%%%%%%%%%%%
%%%输入你的数学公式集%%%%
%%%%%%%%%%%%%%%%%%%%%%
\end{gather}
```

## Image & Graphic

### __插入图片__

```latex
\begin{figure}[!htbp]
      \centering
      \includegraphics[width=0.9\textwidth]{}
      \caption{}
\end{figure}
```

### __插入图片（subfigure）__

```latex
\begin{figure}[!htbp]
      \centering
      \subfigure[实际应用测试图像]{
            \centering
            \includegraphics[width=0.2\textwidth]{image/testInput.png}
      }
      \subfigure[实际应用模型输出]{
            \centering
            \includegraphics[width=0.55\textwidth]{image/testOutput.png}
      }
      \caption{实际应用测试}
\end{figure}
```

### __插入图片（minipage）__

- 两张图片

```latex
\begin{figure}[!htbp]
      \centering
      \begin{minipage}[t]{0.48\textwidth}
            \centering
            \includegraphics[width=0.6\textwidth] {image/scaledDotProduct.png}
            \caption{scaled dot-product attetion示意}
      \end{minipage}
      \begin{minipage}[t]{0.48\textwidth}
            \centering
            \includegraphics[width=0.6\textwidth]{image/multiheadAttention.png}
            \caption{multi-head attention示意}
      \end{minipage}
\end{figure}
```

- 四张图片

```latex
\begin{figure}[!htbp]
    \centering
    \begin{minipage}[!htbp]{0.5\textwidth}
          \centering
          \includegraphics[width=1\textwidth]{image/CNN Architechture Example.jpeg}
          \caption{卷积神经网络架构示例}
    \end{minipage}
    \begin{minipage}[!htbp]{0.45\textwidth}
          \centering
          \includegraphics[width=0.85\textwidth]{image/Convolution Example.png}
          \caption{卷积操作示例}
    \end{minipage}
    \begin{minipage}[!htbp]{0.45\textwidth}
          \centering
          \includegraphics[width=0.85\textwidth]{image/Pooling Example.png}
          \caption{池化操作示例}
    \end{minipage}
\end{figure}
```

### __tikz绘图__

```latex
\begin{figure}[h]
      \centering
      \subfigure[sigmoid]
      {
                  \begin{tikzpicture}[global scale=0.5]
                        %[global scale = 0.5]为整体缩放
                        \begin{axis}[        
                            axis lines=middle,
                            samples=200,         %切分格大小
                            grid,                
                            thick,
                            domain=-8:8,        %函数范围
                            legend pos=outer north east,
                            smooth,
                        ]
                        \addplot+[no marks]{{1/(1+(e^(-1*(\x))))}};    
                        %画函数[]中为属性设置，{}中为函数
                        \end{axis}
                    \end{tikzpicture}
      }
      \subfigure[tanh]
      {
                  \begin{tikzpicture}[global scale=0.5]
                        %[global scale = 0.5]为整体缩放
                        \begin{axis}[        
                            axis lines=middle,
                            samples=200,         %切分格大小
                            grid,                
                            thick,
                            domain=-8:8,        %函数范围
                            legend pos=outer north east,
                            smooth,
                        ]
                        \addplot+[no marks]{{2/(1+(e^(-2*(\x))))-1}};    
                        %画函数[]中为属性设置，{}中为函数
                        \end{axis}
                    \end{tikzpicture}
      }
      \quad
      \subfigure[ReLU]{
                  \begin{tikzpicture}[global scale = 0.5]
                        \begin{axis}[
                       axis lines=middle,
                       samples=200,
                       grid,
                       thick,
                       domain=-8:8,
                       legend pos=outer north east,
                       smooth,
                       ]
                       \addplot+[no marks]{max(\x,0)};
                       \end{axis}
                   \end{tikzpicture}
      }
      \subfigure[softmax]{
            \begin{tikzpicture}[global scale = 0.5]
                  \begin{axis}[
                  axis lines=middle,
                  samples=200,
                  grid,
                  thick,
                  domain=-8:8,
                  legend pos=outer north east,
                  smooth,
                  ]
                  \addplot+[no marks]{((e^(0.1*(\x)))-(e^(-1*(\x))))/((e^(0.1*(\x)))+(e^(-1*(\x))))};
                  \end{axis}
              \end{tikzpicture}
      }
      \caption{不同的激活函数图像}
\end{figure}
```

## Table

```latex
\begin{table}[!htbp]
	\renewcommand\arraystretch{1.2}
	\centering 
	\caption{实际应用性能对比}
	\begin{tabular}{p{45pt}l|ccccc|r} 
		&&向日葵&玫瑰&康乃馨&水仙花&睡莲&平均\\
		原版模型&&0.735&0.625&0.561&0.834&0.839&0.729\\    
		改进模型&&0.823&0.451&0.61&0.855&0.833&0.714\\
	\end{tabular}
\end{table}
```

