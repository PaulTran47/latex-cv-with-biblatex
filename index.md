---
layout: default
---

## Overview

Whether deciding to enter the academic, public, or private sector, every researcher needs a curriculum vitae (Latin for "course of life") or CV for short. This document will be needed for job applications, for conferences, and for keeping track of publications and notable accomplishments.

In the academic world, LaTeX is the standard formatting language and for good reason: LaTeX makes formatting easy for maintenance and quick updates. It's for this reason that I've created a CV entirely in LaTeX. To further tailor this for academics, the CV has integration with Biblatex as well to easily update publications.

## Prerequisites

To work with the source code and tailor this CV for your own needs, you will need the following installed:

* Latest version of MikTeX or TeXLive.
* The following LaTeX packages: [Biblatex](https://ctan.org/pkg/biblatex), [newtxttext](https://ctan.org/pkg/newtx), [fontenc](https://ctan.org/pkg/fontenc), [booktabs](https://ctan.org/pkg/booktabs), [fmtcount](https://ctan.org/pkg/fmtcount), [refcount](https://ctan.org/pkg/refcount), [xcolor](https://ctan.org/pkg/xcolor), [hyperref](https://ctan.org/pkg/hyperref), [paralist](https://ctan.org/pkg/paralist), [ragged2e](https://ctan.org/pkg/ragged2e), [datetime](https://ctan.org/pkg/datetime), [url](https://ctan.org/pkg/url), [fancyhdr](https://ctan.org/pkg/fancyhdr), [lastpage](https://ctan.org/pkg/lastpage), [enumitem](https://ctan.org/pkg/enumitem), [geometry](https://ctan.org/pkg/geometry), [titlesec](https://ctan.org/pkg/titlesec), and [array](https://ctan.org/pkg/array).

## Details

### Preamble

Before the actual CV document is rendered, your preamble (in the .tex file) should look similar to the following (don't mind the comments):

```latex
\documentclass[a4paper, 10pt]{article}

%% Used packages
\usepackage{tran_paul_le_cv}
\usepackage{newtxtext}
\usepackage[T1]{fontenc}
\usepackage{booktabs}
\usepackage{fmtcount}
\usepackage{refcount}
\usepackage[dvipsnames]{xcolor}
\usepackage[colorlinks = true]{hyperref}
\AtBeginDocument{
  \hypersetup{
    allcolors = Blue,
  }
}

%% Adding space before section headings
\titlespacing{\section}{0pt}{2ex}{1ex}

%% Entering in name and information
\name{Paul L. Tran}
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
  ~\begin{tabular}{ll}
    2020 - Present; & \textbf{PhD, Economics}, The University of Texas at Austin (UT Austin).\\
    & Committee: Olivier Coibion (Co-Supervisor), Christoph Boehm (Co-Supervisor),\\
    & Saroj Bhattarai, and Amy Handlan (Brown University).\\
    2023; & \textbf{MS en Passant, Economics}, UT Austin.\\
    2017; & \textbf{BA, Mathematics}, Pomona College.\\
    2017; & \textbf{BA, Mathematical Economics}, Pomona College.\\
  \end{tabular}
  \vspace*{0.25em}

  \section{Research}
  \begin{compactitem}\parskip = 0cm
    \item My current interests involve applications of text analysis and natural language processing in macroeconomics, particularly in central bank communication and expectations formation.
    \item I have submitted \numberstringnum{\getrefnumber{sumpapers}} manuscript on economic topics for publication. A list of these appear below.
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
    2020 - Present; & \textbf{Graduate Teaching Fellowship}, & UT Austin.\\
    2017; & \textbf{Distinction in Economics Senior Exercise}, & Pomona College.\\
    2014 - 2015; & \textbf{Pomona College Scholar}, & Pomona College.
  \end{tabular}
  \vspace*{0.25em}

  \section{Teaching history}\label{sec:teaching_history}
  \begin{compactitem}\parskip = 0cm
    \item I have taught master's and undergraduate economics students as an assistant instructor (AI) and teaching assistant (TA) across 10 semesters at UT Austin.
    \item I earned an \href{https://ctl.utexas.edu/teaching-preparation-series}{Advanced Teaching Preparation Certificate} in 2023 from UT Austin.
  \end{compactitem}
  \vspace*{0.70em}
  ~\begin{tabular}{p{3.5cm} p{12cm}}
    Fall 2024; & \textbf{ECO304L: Introduction to Macroeconomics}, AI.\\
    Spring 2024; & \textbf{ECO395L: Macro and the Labor Market (MA course)}, TA, Prof. Mueller.\\
    & \textbf{ECO395K: Labor Economics (MA course)}, TA, Prof. Oettinger.\\
    Fall 2021 - Fall 2023; & \textbf{ECO304K: Introduction to Microeconomics (Synchronous Massive Online Course for fall semesters)}, TA, Profs. Acchiardo, Geerling, and Mateer.\\
    Summer 2022; & \textbf{ECO325K: Health Economics}, TA, Prof. Schneider.\\
    Fall 2020, Spring 2021; & \textbf{ECO304L: Introduction to Macroeconomics}, TA, Profs. Sadler and Acchiardo.\\
  \end{tabular}
  \vspace*{-0.5em}

  \section{Employment history}
  ~\begin{tabular}{ll}
    2024 - Present; & \textbf{Assistant Instructor}, UT Austin.
  \end{tabular}
  \begin{compactitem}\parskip = 0cm
    \item Please see the {\hypersetup{linkcolor = black}\hyperref[sec:teaching_history]{``Teaching history''}} section for more details.
  \end{compactitem}
  \vspace*{1.25em}
  
  ~\begin{tabular}{ll}
    2020 - 2024; & \textbf{Teaching Assistant}, UT Austin.
  \end{tabular}
  \begin{compactitem}\parskip = 0cm
    \item Please see the {\hypersetup{linkcolor = black}\hyperref[sec:teaching_history]{``Teaching history''}} section for more details.
  \end{compactitem}

  ~\begin{tabular}{ll}
    2018 - 2020; & \textbf{Senior Research Assistant}, Board of Governors of the Federal Reserve System (FRB).
  \end{tabular}
  \begin{compactitem}\parskip = 0cm
    \item {[Bash, FAME, SAS]} Assisted group of economists tasked with assembling staff's forecasts for U.S. business fixed investment (BFI) ahead of each Federal Open Market Committee (FOMC) meeting.
    \item {[FAME]} Compiled a memo consisting of BFI and business sentiment survey metrics across private sectors and Federal Reserve regional banks, used by Chairman Powell in his June 2019 press conference.
    \item {[Bash, FAME, (P)SQL, SAS]} Calculated relationship between industry-level capital expenditure growth rates from Compustat with metrics of trade exposure and uncertainty with China and other countries. Metrics were published in an internal cross-division FRB memo.
    \item {[FAME]} Implemented tighter incorporation of business sentiment, profit expectations, trade exposure, and uncertainty metrics into models that forecast BFI.
    \item {[Stata]} Calculated trade exposures of industries (categorised by the U.S. Census Bureau's Manufacturers' Shipments, Inventories, and Orders release) of final and input goods to China, Europe, and other regions for the purposes of understanding the effects of COVID-19 on supply chains.
    \item {[Bash, Python, (P)SQL]} Created framework that can construct daily, flexible news intensity indices for an arbitrary number of news topics. The framework is capable of performing the dictionary search, outlined in Baker, Bloom, and Davis (2016), across eight million news records in the Thomson Reuters News Archive database and constructing an index in only a few hours.
    \begin{compactitem}
      \item {(Acknowledgement)} The framework was used to measure non-market expectations of tax extensions through text analysis in the following paper: Chang, Andrew C. (2023). ``\href{https://drive.google.com/file/d/1ipHYM7oGXl9A5VQJqe9VwLM4ZMVJYsC9/view}{\textit{Nothing is Certain Except Death and Taxes: The Lack of Policy Uncertainty from Expiring `Temporary' Taxes}}''.
    \end{compactitem}
    \item {[Stata]} Collected and compiled the Drug Enforcement Agency's Automation of Reports and Consolidated Orders Systems database to measure opioid distribution to retail pharmacies as a proxy for opioid usage. Merged with cause-of-death data from the Center for Disease Control and Prevention's National Vitality Statistics Systems database to produce death measurements related to opioid usage.
    \begin{compactitem}
      \item {(Acknowledgement)} The database was merged with the Current Population Survey to estimate the causal effects of heroin use on labour market outcomes by proxying for heroin use with prior exposure to oxycodone in the following paper: Cho, David, Daniel I. Garcia, Joshua Montes, and Alison Weingarden (2021). ``\href{https://doi.org/10.17016/FEDS.2021.025}{\textit{Labor Market Effects of the Oxycodone-Heroin Epidemic}}''.
    \end{compactitem}
  \end{compactitem}
  \vspace*{1.25em}
      
  ~\begin{tabular}{ll}
    2017 - 2018; & \textbf{Research Assistant}, FRB.
  \end{tabular}
  \begin{compactitem}\parskip = 0cm
    \item {[FAME, R]} Excelled in high-pressure role supporting a group of economists charged with assembling the staff's GDP forecast ahead of each FOMC meeting.
    \item {[FAME, R]} Developed programmes used by FRB staff that expanded the FRB's forecasting apparatus to directly account for measurement error's role in published statistics when determining the true, underlying cyclical position of the economy.
    \item {[FAME]} Created new exhibits highlighting the estimates of the cyclical position of the economy through variables such as GDP, potential output, output gap, \& measurement error in the \href{https://www.federalreserve.gov/monetarypolicy/fomc_historical.htm#tealbooks}{\textit{Tealbook A: ``Economic and Financial Conditions: Current Situation and Outlook''}} and the \href{https://www.federalreserve.gov/monetarypolicy/fomc_historical.htm#greenbooks}{\textit{Greenbooks: ``Current Economic and Financial Conditions''}}.
  \end{compactitem}
  \vspace*{0.25em}
      
  \section{Grants}
  ~\begin{tabular}{llll}
    2020 - 2024; & \textbf{Full PhD Teaching Assistantship Tuition Waiver}, & UT Austin, & \$75,702.\\
    2023 - 2024; & \textbf{PhD Summer Fellowship}, & UT Austin, & \$8,000.\\
    2016; & \textbf{Harry G. Steele Scholarship}, & Pomona College, & \$4,000.\\
    2013; & \textbf{Flextronics Texas Scholarship}, & Pomona College, & \$1,000.
  \end{tabular}
  \vspace*{0.25em}
    
  \section{Miscellaneous information}
  \begin{compactitem}\parskip = 0cm
    \item \textbf{Programming:} Matlab, Python, Bash, SAS, \href{https://en.wikipedia.org/wiki/FAME_(database)}{FAME}, (P)SQL, R, Stata, EViews, \LaTeX.
    \item \textbf{Web Development:} Vanilla HTML, CSS, JS; Jekyll.
    \item \textbf{Applications:} Visual Studio Code, Emacs, Git, Sublime Text, RStudio, Tableau, Microsoft Office.
    \item \textbf{Operating Systems:} Unix, Linux, Windows.
    \item \textbf{Languages:} Vietnamese (native), English (native).
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

Feel free to take a look at the [.tex file here](https://raw.githubusercontent.com/PaulTran47/latex-cv-with-biblatex/master/tran_paul_le_cv.tex), the [.sty file here](https://raw.githubusercontent.com/PaulTran47/latex-cv-with-biblatex/master/tran_paul_le_cv.sty), my [personal CV](https://drive.google.com/file/d/1P3rTeJtPRlIMhha3hauKHkdX2BGse3ht/view) as an example, and the [GitHub repo](https://github.com/PaulTran47/latex-cv-with-biblatex) for the source code (also found by the buttons found on this website).

## Closing note

If you want to find out more about me and my research, please check out my [personal website](https://paulletran.com)!