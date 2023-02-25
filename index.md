---
layout: default
---

## Overview

Whether deciding to enter the academic, public, or private sector, every researcher needs a curriculum vitae (Latin for "course of life") or CV for short. This document will be needed for job applications, for conferences, and for keeping track of publications and notable accomplishments.

In the academic world, LaTeX is the standard formatting language and for good reason: LaTeX makes formatting easy for maintenance and quick updates. It's for this reason that I've created a CV entirely in LaTeX. To further tailor this for academics, the CV has integration with Biblatex as well to easily update publications.

## Prerequisites

To work with the source code and tailor this CV for your own needs, you will need the following installed:

* Latest version of MikTeX or TeXLive.
* The following LaTeX packages (more information can be found on [CTAN](https://ctan.org/): Biblatex, booktabs, fontawesome, fontenc, carlito, fmtcount, refcount.

## Details

### Preamble

Before the actual CV document is rendered, your preamble (in the .tex file) should look similar to the following (don't mind the comments):

```latex
\documentclass[a4paper, 10pt]{article}

%% Used packages
\usepackage{tran_paul_le_cv, booktabs, fontawesome}
\usepackage[T1]{fontenc}
\usepackage{hyperref}
\usepackage[sfdefault, lf, t]{carlito}
\usepackage{inconsolata}
\usepackage{fmtcount}
\usepackage{refcount}

%% Changing heading colour to blue
\def\headcolor{\color[rgb]{0, 0, 0.5}}

%% Adding space before section headings
\titlespacing{\section}{0pt}{2ex}{1ex}

%% Entering in name and information
\name{Paul Le Tran}
\info{Office: & \href{https://liberalarts.utexas.edu/economics/ph-d-program/}{Department of Economics},\\
  & College of Liberal Arts,\\
  & The University of Texas at Austin,\\
  & 2225 Speedway,\\
  & BRB 2.128, C3100,\\
  & Austin, Texas 78712.\\
  \textbf{Citizenship}: & \textbf{United States of America}.\\
  Cell: & +1 (512) 704-3025\\
  Email: & \href{mailto:pltran@utexas.edu}{pltran@utexas.edu}\\
  Website: & \href{https://paulletran.com/}{https://paulletran.com/}\\
  GitHub: & \href{https://github.com/PaulTran47}{https://www.github.com/paultran47/}
}

%% Setting up bibliography
\bibliography{tran_paul_le_cv_wips, tran_paul_le_cv_pubs}

%% Add selected items from .bib files to be shown
\addtocategory{wips}{
  pt_evercore,
  act_trna,
}
\addtocategory{fin}{
  tran_opecnn,
  ct_econthesis,
  tran_mathsthesis,
}
```

* Your name should be placed in the `\name` command.
* Relevant contact information should be placed into the `\info` command. The argument is a single string, but you can have it be a very long string with multiple line breaks.
* The final section of your preamble should be for bibiliographies. You should declare any .bib files in the `\bibliography` command. The `\addtocategory` command allows you to specify what BibTeX entry types you want to both count in your total publications and display in the CV itself. You can find out more about all the [standard entry types here](https://www.bibtex.com/e/entry-types/).
  * It should be mentioned that custom entry types can be created, but that won't be covered here due to the relative rarity for such need
  * You can easily create customise the naming of entry types in the .sty file. The following is an example:
  ```
  \makebibcategory{papers}{Publications}
  ```

### Document

After the preamble, your .tex file should look like this:

```latex
\begin{document}
  \maketitle
  \thispagestyle{firststyle}
  \section{Education}
  ~\begin{tabular}{ll}
    2020--Present; & \textbf{PhD, Economics}, The University of Texas at Austin (UT Austin).\\
    2023; & \textbf{MS en Passant, Economics}, UT Austin.\\
    2017; & \textbf{BA, Mathematics}, Pomona College.\\
    2017; & \textbf{BA, Mathematical Economics}, Pomona College.\\
  \end{tabular}
  \vspace*{0.25em}

  \section{Research}
  \begin{compactitem}\parskip = 0cm
    \item My current interests involve applications of text analysis in macroeconomics, machine learning, business cycles, and nonparametric econometrics. My research interests primarily focus on investigating how text analysis through machine learning can be used in macroeconomics to provide cleaner causal inference.
    \item I have authored or co-authored \numberstringnum{\getrefnumber{sumpapers}} publications on economic topics. A list of these appear below.
  \end{compactitem}
  \vspace*{0.25em}

  %% Adding works in progress and publication .bib files
  %% You can inclide \printbib outside of the publications environment. They just won't be counted towards sumpapers
  \printbib{wips}
  \vspace*{-0.75em}
  \begin{publications}
    \printbib{fin}
  \end{publications}
  \vspace*{-0.75em}

  \section{Honours and awards}
  ~\begin{tabular}{lll}
    2020--Present; & \textbf{Graduate Teaching Fellowship}, & UT Austin.\\
    2017; & \textbf{Distinction in Economics Senior Exercise}, & Pomona College.\\
    2014--2015; & \textbf{Pomona College Scholar}, & Pomona College.
  \end{tabular}
  \vspace*{0.25em}
```

* `\maketitle` after `\begin{document}` inserts the header box into the LaTeX document. Afterwards, the rest of the .tex file outputs a typical LaTeX document with `\section` commands.
* To insert publications into the document, use the `\begin{publications}` command.
  * Each `\printbib` command will insert a subsection that contains all publications in that category, in chronological and descending order, and sorted by name within each year.
    * Sorting specifics can be modified within the Biblatex package options in the .sty file.
  * The total number of publications listed inside the `publicaitons` environment is calculated and converted into an integer using the `fmtcount` package. The page numbers for the publications section are also stored. These allow you to output them in the LaTeX document if you wish.
  * You're allowed to have `\printbib` commands outside the `publications` enviroment, but the associated .bib items will not be counted towards the total number of publications.
    * Note that this only works for outside `\printbib` commands that __follow__ the `publications` environment. For outside `\printbib` commands that you want displayed before the `publications` environment (e.g., working papers), you will need to manually subtract the number of .bib items from `sumpapers` in the .sty file:

    ```latex
    %% Counters for keeping track of papers
    %% Subtract the number of .bib items before publications environment (x) from sumpapers (0 - x = -x)
    %% This does not need to be done for .bib items after the publications environment
    \newcounter{papers}\setcounter{papers}{0}
    \newcounter{sumpapers}\setcounter{sumpapers}{-2}
    \def\lastref#1{\addtocounter{#1}{\value{papers}}\setcounter{papers}{0}}
    ```

## Download

Feel free to take a look at the [.tex file here](https://raw.githubusercontent.com/PaulTran47/latex-cv-with-biblatex/master/tran_paul_le_cv.tex), the [.sty file here](https://raw.githubusercontent.com/PaulTran47/latex-cv-with-biblatex/master/tran_paul_le_cv.sty), my [personal CV](https://drive.google.com/file/d/1P3rTeJtPRlIMhha3hauKHkdX2BGse3ht/view) as an example, and the [GitHub repo](https://github.com/PaulTran47/latex-cv-with-biblatex) for the source code (also found by the buttons found on this website).

## Closing note

If you want to find out more about me, check out my [personal website](https://paulletran.com)!