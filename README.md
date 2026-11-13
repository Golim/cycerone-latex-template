# Cycerone Beamer Theme

A working example of how to use the Cycerone Beamer theme is in `cycerone-demo.tex`. The theme is in `beamerthemeCycerone.sty` and the main configuration options are near the top of that file. The title badge, event, and closing-slide contacts can be configured after `\input{theme.tex}`.

Use the local theme in a Beamer document:

```tex
\documentclass[10pt,t,aspectratio=169]{beamer}
\input{theme.tex}

\title{Lecture title}
\subtitle{Optional subtitle}
\author{Your Name}
\date{\today}
```

Compile from this directory into the `output` subdirectory:

```sh
latexmk -pdf -output-directory=output your-slides.tex
```

The main configuration options live near the top of `beamerthemeCycerone.sty`. Configure the title badge, event, and closing-slide contacts after `\input{theme.tex}`:

```tex
\cysettitlegraphic{figures/unitn-logo.png}
\cysetevent{University of Trento}
\cysetcontactname{Your Name}
\cysetcontactemail{author@unitn.it}
\cysetcontactwebsite{https://author-website.example.com}
\cysetlinkedin{https://www.linkedin.com/company/cycerone-project/}
\cysetyoutube{https://www.youtube.com/@CYCERONE-j1m}
```

For slide content, use `\vspace{2mm}` or `\vspace{0.3cm}` between short ideas. The frame-title, footer, contact block, title-page badge, margins, and logo coordinates have nearby comments in the `.sty` file; change those values when you need to tune the overall layout. Use `block` for a dark callout and `alertblock` for a pale-red warning.

## Highlighted code

`theme.tex` loads the shared `code.tex` setup, which defines language-specific environments using `minted` and Pygments. If you use `theme.tex`, the code setup is loaded automatically. If you load only `beamerthemeCycerone` with `\usetheme{Cycerone}`, add `\input{code.tex}` in the preamble. Then put code in the matching environment. For example:

```tex
\begin{frame}[fragile]{Python example}
\begin{pythoncode}
def hello_world():
    print("Hello, world!")
\end{pythoncode}
\end{frame}
```

Other provided environments are `jscode`, `htmlcode`, `httpcode`, `httpreq`, `bashcode`, `sqlcode`, and `phpcode`. For a different language, use `minted` directly, such as `\begin{minted}{ruby} ... \end{minted}`. Beamer frames containing code need the `[fragile]` option.

Install the `minted` package using your TeX distribution. With TeX Live 2024 or newer, the minted executable is allowed under restricted shell escape, so the normal `latexmk` command above works. Older TeX Live versions and MiKTeX may require shell escape enabled for the document; only enable it for source you trust. The [minted documentation](https://tug.ctan.org/macros/latex/contrib/minted/minted.pdf) covers installation and version-specific setup.

## Diagrams

`diagrams.tex` defines shared TikZ styles that use the theme colours and typography, so diagrams across the course have a consistent visual language. Load it after the theme, and enable the TikZ libraries for arrowheads and relative node placement:

```tex
\usetheme{Cycerone}
\usetikzlibrary{arrows.meta,positioning}
\input{diagrams.tex}
```

Use the styles in a `tikzpicture`. For example:

```tex
\begin{tikzpicture}[node distance=7mm and 12mm]
  \node[cy process] (input) {Input};
  \node[cy process,right=of input] (process) {Process};
  \node[cy mint box,right=of process] (output) {Output};
  \draw[cy arrow] (input) -- (process);
  \draw[cy arrow] (process) -- (output);
\end{tikzpicture}
```

Available styles include `cy box`, `cy dark box`, `cy mint box`, `cy process`, `cy layer`, `cy arrow`, `cy dashed`, `cy label`, and `cy title`. The file also provides helper commands such as `\cyKernelBar`, `\cyStackBox`, and `\cyMiniTag`. See the diagram slide in `cycerone-demo.tex` for a complete example.
