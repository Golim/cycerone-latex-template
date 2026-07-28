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

Compile from this directory in the `output` subdirectory:

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
