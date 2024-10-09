---
layout: default
---

## Overview

Whether deciding to enter the academic, public, or private sector, every researcher needs a curriculum vitae (Latin for "course of life") or CV for short. This document will be needed for job applications, for conferences, and for keeping track of publications and notable accomplishments.

In the academic world, LaTeX is the standard formatting language and for good reason: LaTeX makes formatting easy for maintenance and quick updates. It's for this reason that I've created a CV entirely in LaTeX. To further tailor this for academics, the CV has integration with Biblatex as well to easily update publications.

## Prerequisites

To work with the source code and tailor this CV for your own needs, you will need the following installed:

* Latest version of MikTeX or TeXLive.
* The following LaTeX packages: [newtxttext](https://ctan.org/pkg/newtx), [fontenc](https://ctan.org/pkg/fontenc), [geometry](https://ctan.org/pkg/geometry), [ragged2e](https://ctan.org/pkg/ragged2e), [fancyhdr](https://ctan.org/pkg/fancyhdr), [xcolor](https://ctan.org/pkg/xcolor), [url](https://ctan.org/pkg/url), [hyperref](https://ctan.org/pkg/hyperref), [booktabs](https://ctan.org/pkg/booktabs), [fmtcount](https://ctan.org/pkg/fmtcount), [refcount](https://ctan.org/pkg/refcount), [datetime](https://ctan.org/pkg/datetime), [titlesec](https://ctan.org/pkg/titlesec), [lastpage](https://ctan.org/pkg/lastpage), [paralist](https://ctan.org/pkg/paralist), [enumitem](https://ctan.org/pkg/enumitem), [array](https://ctan.org/pkg/array), and [biblatex](https://ctan.org/pkg/biblatex).

## Details

### Preamble

Before the actual CV document is rendered, your preamble (in the .tex file) should look similar to the following (don't mind the comments):

```latex
\documentclass[a4paper, 10pt]{article}

%% Loading .sty file
\usepackage{tran_paul_le_cv}

%% Adding space before section headings
\titlespacing{\section}{0pt}{2ex}{1ex}

%% Entering in name and information
\name{Paul L. Tran}
\info{Office: & \href{https://liberalarts.utexas.edu/economics/ph-d-program/}{Department of Economics},\\
  & College of Liberal Arts,\\
  & University of Texas at Austin,\\
  & 2225 Speedway,\\
  & BRB 2.128, C3100,\\
  & Austin, Texas 78712\\
  \textbf{Citizenship}: & \textbf{United States of America}\\
  Cell: & +1 (512) 704-3025\\
  Email: & \href{mailto:pltran@utexas.edu}{pltran@utexas.edu}\\
  Website: & \href{https://paulletran.com/}{https://paulletran.com/}
}

%% Setting up bibliography
\addbibresource{tran_paul_le_cv_wps.bib}
\addbibresource{tran_paul_le_cv_wips.bib}
\DeclareSourcemap{
  \maps[datatype = bibtex, overwrite]{
    \map{
      \step[fieldset = month, null]
    }
  }
}
\ExecuteBibliographyOptions{useprefix = true}

%% Add selected items from .bib files to be shown
\addtocategory{wps}{
  tran_opecnn,
}
\addtocategory{wips}{
  tran_moretimepls,
}
```

* Your name should be placed in the `\name` command.
* Relevant contact information should be placed into the `\info` command. The argument is a single string, but you can have it be a very long string with multiple line breaks.
* The final section of your preamble should be for bibiliographies. You should declare each .bib file in their individual `\addbibresource` commands. The `\addtocategory` command allows you to specify what BibTeX entry types you want to both count in your total publications and display in the CV itself. You can find out more about all the [standard entry types here](https://www.bibtex.com/e/entry-types/).
  * It should be mentioned that custom entry types can be created, but that won't be covered here due to the relative rarity for such need
  * You can easily create customise the naming of entry types in the accompanying .sty file. The following is an example:
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
  ~\begin{tabular}{llll}
    2020 - & \textbf{PhD} & Economics & University of Texas at Austin\\
    2023 & \textbf{MS en Passant} & Economics & University of Texas at Austin\\
    2017 & \textbf{BA} & Mathematics, Mathematical Economics & Pomona College
  \end{tabular}
  \vspace*{0.25em}

  \section{Dissertation}
  \begin{compactitem}\parskip = 0cm
    \item Committee: Olivier Coibion (Co-Supervisor), Christoph Boehm (Co-Supervisor), Saroj Bhattarai, and Amy Handlan (Brown University)
  \end{compactitem}
  \vspace*{0.25em}

  \section{Research}
  \begin{compactitem}\parskip = 0cm
    \item My current interests involve applications of text analysis and natural language processing in macroeconomics, particularly in central bank communication and expectations formation.
    %% Uncomment the following line when you actually get submissions accepted and published in journals
    % \item I have authored or co-authored \numberstringnum{\getrefnumber{sumpapers}} publications on economic topics. A list of these appear below.
  \end{compactitem}
  \vspace*{0.25em}

  %% Adding working papers, works in progress, and publications .bib files
  %% You can include \printbib outside of the publications environment. They just won't be counted towards sumpapers
  \begin{publications}
    \printbib{wps}
  \end{publications}
  \vspace*{-0.75em}
  \printbib{wips}
  \vspace*{-0.75em}

  \section{Honours and awards}
  ~\begin{tabular}{lll}
    2020 - & \textbf{Graduate Teaching Fellowship} & University of Texas at Austin\\
    2017 & \textbf{Distinction in Economics Senior Exercise} & Pomona College\\
    2014 - 2015 & \textbf{Pomona College Scholar} & Pomona College
  \end{tabular}
  \vspace*{0.25em}

  \section{Teaching history}\label{sec:teaching_history}
  \begin{compactitem}\parskip = 0cm
    \item Since Fall 2020, student evaluations have given an average rating for my teaching of 4.25 out of 5.
    \item I earned an \href{https://ctl.utexas.edu/teaching-preparation-series}{Advanced Teaching Preparation Certificate} in 2023 from the University of Texas at Austin.
  \end{compactitem}
  \vspace*{0.70em}
  ~\begin{tabular}{p{2.3cm} p{2.4cm} p{2.8cm} p{6.6cm}}
    University of \newline Texas at Austin & Fall 2024 & Assistant Instructor & \textbf{ECO304L: Introduction to \newline Macroeconomics}\\
    & Spring 2024 & Teaching Assistant \newline (Prof. Mueller) & \textbf{ECO395L: Macro and the Labor Market \newline (MA course)}\\
    & & Teaching Assistant \newline (Prof. Oettinger) & \textbf{ECO395K: Labor Economics (MA course)}\\
    & Fall 2021 - 2023 & Teaching Assistant \newline (Profs. Acchiardo, \newline Geerling, Mateer) & \textbf{ECO304K: Introduction to Microeconomics \newline (Synchronous Massive Online Course for \newline fall)}\\
    & Summer 2022 & Teaching Assistant \newline (Prof. Schneider) & \textbf{ECO325K: Health Economics}\\
    & Fall 2020, \newline Spring 2021 & Teaching Assistant \newline (Profs. Sadler, \newline Acchiardo) & \textbf{ECO304L: Introduction to \newline Macroeconomics}
  \end{tabular}
  \vspace*{0.25em}

  \section{Employment history}
  \begin{compactitem}\parskip = 0cm
    \item Please see the {\hypersetup{linkcolor = black}\hyperref[sec:teaching_history]{``Teaching history''}} section for more details about my teaching experience.
  \end{compactitem}
  \vspace*{0.70em}
  ~\begin{tabular}{lll}
    2024 - & \textbf{Assistant Instructor} & University of Texas at Austin\\
    2020 - 2024 & \textbf{Teaching Assistant} & University of Texas at Austin\\
    2018 - 2020 & \textbf{Senior Research Assistant} & Board of Governors of the Federal Reserve System\\
    2017 - 2018 & \textbf{Research Assistant} & Board of Governors of the Federal Reserve System
  \end{tabular}
  \vspace*{0.25em}
      
  \section{Grants}
  ~\begin{tabular}{llll}
    2024 & \textbf{PhD Summer Research Fellowship} & University of Texas at Austin, & \$5,000\\
    2023 & \textbf{PhD Summer Research Fellowship} & University of Texas at Austin, & \$3,000\\
    2016 & \textbf{Harry G. Steele Scholarship} & Pomona College & \$4,000\\
    2013 & \textbf{Flextronics Texas Scholarship} & Pomona College & \$1,000
  \end{tabular}
  \vspace*{0.25em}
    
  \section{Miscellaneous information}
  \begin{compactitem}\parskip = 0cm
    \item \textbf{Programming:} Matlab, Python, Bash, SAS, \href{https://en.wikipedia.org/wiki/FAME_(database)}{FAME}, (P)SQL, R, Stata, EViews, \LaTeX
    \item \textbf{Front-end Development:} Vanilla HTML, CSS, JS, Jekyll
    \item \textbf{Applications:} Visual Studio Code, Emacs, Git, Sublime Text, RStudio, Tableau, Microsoft Office
    \item \textbf{Operating Systems:} Unix, Linux, Windows
    \item \textbf{Languages:} Vietnamese (native), English (native)
  \end{compactitem}
\end{document}
```

* `\maketitle` after `\begin{document}` inserts the header box into the LaTeX document. Afterwards, the rest of the .tex file outputs a typical LaTeX document with `\section` commands.
* To insert publications into the document, use the `\begin{publications}` command.
  * Each `\printbib` command will insert a subsection that contains all publications in that category, in chronological and descending order, and sorted by name within each year.
    * Sorting specifics can be modified within the Biblatex package options in the .sty file.
  * The total number of publications listed inside the `publications` environment is calculated and converted into an integer using the `fmtcount` package. The page numbers for the publications section are also stored. These allow you to output them in the LaTeX document if you wish.
  * You're allowed to have `\printbib` commands outside the `publications` enviroment, but the associated .bib items will not be counted towards the total number of publications.
    * Note that this only works for outside `\printbib` commands that __follow__ the `publications` environment. For outside `\printbib` commands that you want displayed before the `publications` environment (e.g., working papers), you will need to manually subtract the number of .bib items from `sumpapers` in the .sty file:

    ```latex
      %% Counters for keeping track of papers
      %% Sumpapers will naturally count everything contained inside of the publications environment (because you ideally want only publications counted). For conveninecen, the following lines of code modify the count of sumpapers of the publications environment if you want to count other materials, such as manuscripts submitted for publication (because you have no publications yet :') )
      %% If you're counting the number of publications, subtract the number of .bib items THAT COME BEFORE the publications environemtn (x) from sumpapers (0 - x = -x)
      %% If you're counting the number of publications, keep sumpapers argument to equal zero since these papers go under the ``Working Papers'' category, which is first
      %% This does not need to be done for .bib items after the publications environment
      \newcounter{papers}\setcounter{papers}{0}
      \newcounter{sumpapers}\setcounter{sumpapers}{0}
      \def\lastref#1{\addtocounter{#1}{\value{papers}}\setcounter{papers}{0}}

      %% Add all papers in the bib file.
      \nocite{*}
    ```

## Download

Feel free to take a look at the [.tex file here](https://raw.githubusercontent.com/PaulTran47/latex-cv-with-biblatex/master/tran_paul_le_cv.tex), the [.sty file here](https://raw.githubusercontent.com/PaulTran47/latex-cv-with-biblatex/master/tran_paul_le_cv.sty), my [personal CV](https://drive.google.com/file/d/1P3rTeJtPRlIMhha3hauKHkdX2BGse3ht/view) as an example, and the [GitHub repo](https://github.com/PaulTran47/latex-cv-with-biblatex) for the source code (also found by the buttons at the top of this website).

## Closing note

If you want to find out more about me and my research, please visit my [personal website](https://paulletran.com). You can also find my research on [my SSRN profile](https://papers.ssrn.com/sol3/cf_dev/AbsByAuth.cfm?per_id=7065188), [my GitHub profile](https://github.com/PaulTran47), and my ORCID (0009-0000-8559-7915).
