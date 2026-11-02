# Fudan PPT Template 使用说明书

这是一个基于 LaTeX Beamer 的演示文稿模板，修改自 SINTEF Presentation 主题，适用于学术报告或展示。

## 目录结构
- `beamersapienza.tex`: 主示例文件，建议直接在此文件基础上进行修改。
- `beamerthemesintef.sty`: 主题样式逻辑定义。
- `sintefcolor.sty`: 颜色方案定义。
- `assets/`: 存放演示文稿背景图及 Logo。

---

## 1. 快速开始与编译
### 环境要求
- 安装 TeX Live, MiKTeX 或 MacTeX。
- **推荐编译方式**: 使用 `xelatex`。
  ```bash
  xelatex beamersapienza.tex
  ```
  *(注意：若包含目录或引用，通常需要编译两次)*

### 标题页设置
在导言区配置信息，并在 `\begin{document}` 后使用 `\maketitle`：
```latex
\title{报告标题}
\subtitle{报告副标题}
\author{作者姓名}
\date{\today}
\titlebackground*{assets/background} % 设置标题页背景，星号版本将背景图片切分在右侧
\maketitle
```

---

## 2. 布局与排版控制
### 页面结构
使用 Beamer 标准环境创建幻灯片：
```latex
\begin{frame}{幻灯片标题}
  \framesubtitle{幻灯片副标题}
  内容区域...
\end{frame}
```

### 列表逐项显示 (Sequential Reveal)
使用 `[<+->]` 可以轻松实现列表逐行出现：
```latex
\begin{itemize}[<+->]
  \item 第一点
  \item 第二点
\end{itemize}
```

### 分栏布局 (Columns)
使用 `columns` 环境并配合 `column` 划分宽度：
```latex
\begin{columns}
  \begin{column}{0.3\textwidth}
    左侧内容 (占30%宽度)
  \end{column}
  \begin{column}{0.7\textwidth}
    右侧内容 (占70%宽度)
  \end{column}
\end{columns}
```

---

## 3. 颜色与样式控制
### 整体配色
在导言区设置：
- `\themecolor{white}`: 白色主题（默认）。
- `\themecolor{main}`: 主色主题。

### 页脚颜色
在特定的 `\begin{frame}` 之前使用，用于区分不同章节：
```latex
\footlinecolor{sintefyellow} % 之后的所有页面页脚将变为黄色
\begin{frame}{...} ... \end{frame}
\footlinecolor{} % 恢复默认
```
*可用颜色*: `maincolor`, `sintefyellow`, `sintefgreen`, `sintefdarkgreen`。

### 区块 (Blocks)
- **标准区块**: `\begin{block}{标题} 内容 \end{block}`
- **彩色区块**: 使用 `colorblock` 自定义背景色：
  ```latex
  \begin{colorblock}[文字颜色]{背景颜色}{标题}
    内容...
  \end{colorblock}
  ```

---

## 4. 特殊命令说明
- **颜色测试**: 使用 `\testcolor{颜色名}` 可以快速查看模板中预定义的颜色及其名称。
- **链接**: 使用 `\hrefcol{链接地址}{显示文字}` 可以创建带颜色的超链接。

## 5. 自定义配色
如果需要修改主色调或添加自定义颜色，请编辑 `sintefcolor.sty` 文件。该文件中定义了所有的色彩变量。

---
*如有特殊需求，请直接参考 `beamersapienza.tex` 中的实现代码。*
