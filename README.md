# LaTeX CV with Biblatex

[MIT Licensed](https://github.com/PaulTran47/CV/blob/master/LICENCE.md).

<details>
  <summary>Table of contents</summary>
  <ul>
    <li>
      <a href="#overview">Overview</a>
      <ul>
        <li><a href="#reporting-vulnerabilities">Reporting vulnerabilities</a></li>
        <li><a href="#notable-features">Notable features</a></li>
      </ul>
    </li>
    <li><a href="#prerequisites">Prerequisites</a></li>
  </ul>
</details>

---

## Overview

This repository hosts all assets and source code that create my curriculum vitae (CV).

I love LaTeX and use it so much, I figured using the language for the creation
and maintenance of my CV is a natural move.

<p align="right">
  (<a href="#latex-cv-with-biblatex">back to top.</a>)
</p>

---

### Reporting vulnerabilities

If you discover a vulnerability/error/mistake in the production code of my
website, please [refer to the instructions found in SECURITY.md](https://github.com/PaulTran47/latex-cv-with-biblatex/blob/gh-pages/SECURITY.md)
for instructions on reporting these issues. I will then address the problem as
soon as possible.

<p align="right">
  (<a href="#latex-cv-with-biblatex">back to top.</a>)
</p>

---

### Notable features

* Built entirely with LaTeX for ease-of-maintenance and quick updates.
* Built for academics. This means [Biblatex](https://ctan.org/pkg/biblatex?lang=en)
is naturally incorporated, and all shown bibliographies are in chronological and
descending order, and sorted by name within each year.
* Total number of publications are counted for quick display if desired.

<p align="right">
  (<a href="#latex-cv-with-biblatex">back to top.</a>)
</p>

---

## Prerequisites

* Latest version of MikTeX or TeXLive
* The following LaTeX packages:
  * [newtxttext](https://ctan.org/pkg/newtx)
  * [fontenc](https://ctan.org/pkg/fontenc) (with option T1)
  * [geometry](https://ctan.org/pkg/geometry) (with option margin = 1in)
  * [ragged2e](https://ctan.org/pkg/ragged2e)
  * [fancyhdr](https://ctan.org/pkg/fancyhdr)
  * [xcolor](https://ctan.org/pkg/xcolor) (with option dvipsnames)
  * [url](https://ctan.org/pkg/url)
  * [hyperref](https://ctan.org/pkg/hyperref) (with colorlinks = true)
  * [booktabs](https://ctan.org/pkg/booktabs)
  * [fmtcount](https://ctan.org/pkg/fmtcount)
  * [refcount](https://ctan.org/pkg/refcount)
  * [datetime](https://ctan.org/pkg/datetime)
  * [titlesec](https://ctan.org/pkg/titlesec)
  * [lastpage](https://ctan.org/pkg/lastpage)
  * [paralist](https://ctan.org/pkg/paralist)
  * [enumitem](https://ctan.org/pkg/enumitem)
  * [array](https://ctan.org/pkg/array)
  * [biblatex](https://ctan.org/pkg/biblatex) (with backend of [Biber](https://ctan.org/pkg/biber)
  and options sorting = ydnt, citestyle = authoryear, bibstyle = authoryear-comp,
  defernumbers = true, maxnames = 20, giveninits = false, bibencoding = utf8,
  terseinits = true, uniquename = init, dashed = false, doi = true,
  isbn = false, natbib = true, backend = biber, date = year)

<p align="right">
  (<a href="#latex-cv-with-biblatex">back to top.</a>)
</p>

---
