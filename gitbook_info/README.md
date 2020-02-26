
# Getting started with bookdown for Gitbooks

Again, please jump in

## Set up your template
- In RStudio, 
   - File --> New Project --> New Directory
   - Choose "Book project using bookdown"
   - Click "Build Book" (top right, near the Git tab) 
   
## Modify _output.yml
- Change "A Minimal Book Example" to title of your choice (will appear at the top of the left-hand TOC)
- Delete the pdf and/or epub output sections, if you don't care to compile a pdf and are getting pandoc/tex/epub errors when you try to build

## Modify _bookdown.yml
- [EpiModelEDA example](https://github.com/statnet/EpiModelEDA/blob/master/_bookdown.yml)
    - If you specify the chapters explicitly, then you don't need to number them
    - Makes it easier to rearrange chapter order
    - Also makes it easier to temporarily exclude chapters when compiling the book - this may come in handy, see below

## Rely on the bookdown website
[https://bookdown.org/yihui/bookdown/](https://bookdown.org/yihui/bookdown/)

# Some tips

## Debug faster by using easy-to-find code chunk titles
- E.g. ```{r chaptername-whatthischunkdoes, echo=FALSE}```


## Debug faster by knitting modified chapters one-at-a-time
Options:
- Comment out the other chapters in ```_bookdown.yml```, and then build
- Have the chapter code be completely standalone (doesn't rely on prior chapters), and then knit just that chapter
- Use ```bookdown::preview_chapter``` (can't remember why I don't like this)

## Do not make a book when an Rmd file with floating TOC is sufficient
You WILL spend more time debugging, because it's a more complex file structure. It's also more annoying to share, unless you're making it a public website.

Book is useful when there is so much content that you 
- save time by knitting chapters separately
- navigate faster from the clean look of the bookdown TOC?

Other benefits:
- Can easily make a public website by saving the output to repo/docs and turning on the github.io website
- Aesthetics

# More on GitBooks versus other formats

## Single .Rmd file 

**BEST FOR** most reproducible work

**RELIES ON** knitr, rmarkdown

**PROS**
- [As stated above](https://github.com/netterie/resources/tree/master/gitbook_info#do-not-make-a-book-when-an-rmd-file-with-floating-toc-is-sufficient), it's the cleanest, simplest option 
- Tons of flexibility: [floating TOC](https://bookdown.org/yihui/rmarkdown/html-document.html#table-of-contents), [code folding](https://bookdown.org/yihui/rmarkdown/html-document.html#code-folding), [flexdashboard](https://rmarkdown.rstudio.com/flexdashboard/), [tabs](https://bookdown.org/yihui/rmarkdown/html-document.html#tabbed-sections)
- Output to HTML or pdf

**CONS**
- Doesn't accommodate a large amount of computation well, unless perhaps you cache major sections? 

## GitBook

**BEST FOR** When you want to typeset a large amount of information to multiple formats (html, pdf and/or epub)

**RELIES ON** knitr, rmarkdown, bookdown

**PROS**
- Collects multiple Rmd files into one "book"
- Output to html, pdf and/or epub

**CONS**
- Does not support all features available to single Rmd files, like code-folding?
- Can be buggy 

**GETTING STARTED** [See above](https://github.com/netterie/resources/tree/master/gitbook_info#getting-started-with-bookdown-for-gitbooks)

**EXAMPLES** The books at http://bookdown.org, for example [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/)

## Website via Rmarkdown

**BEST FOR** Web-based access to a large amount of information

**RELIES ON** knitr, rmarkdown

**PROS** 
- Can combine several layers of navigation: top navbar with drop-down sub-sections plus normal Rmd navation (floating TOC, tabs)
- Many aesthetics are highly customizable 

**CONS**
- HTML only

**GETTING STARTED** There are surely many tutorials out there. Here is [one way to get started](https://github.com/netterie/resources/tree/master/websites#websites-with-rmarkdown). Or, try [workflowr](https://jdblischak.github.io/workflowrBeta/index.html#why-use-workflowr) which seems to be good for simpler analyses that have accompanying text and figures.

**EXAMPLES** [Public site for SHAMP](https://statnet.github.io/SHAMP-public), if you want an internal example. 

## Website via GitHub Pages and Jekyll

**BEST FOR** Simple edit-via-web site, specific to a single user?

**RELIES ON** A GitHub user's "GitHub Pages" feature

**PROS**
- I like how you get a preview of the .md content when you view the page from the repo, e.g. https://github.com/netterie/netterie.github.io/blob/master/second_page.md

**GETTING STARTED** [Here's the tutorial](https://guides.github.com/features/pages/#setup) for setting up your page; [Here's the guide](https://help.github.com/en/github/working-with-github-pages/adding-a-theme-to-your-github-pages-site-using-jekyll) to customizing.

**EXAMPLES**

https://netterie.github.io

https://hivbackcalc.github.io

## Wikis

**BEST FOR** Simple edit-via-web site, specific to one repository?

**RELIES ON** A GitHub repo's "Wiki" feature

**EXAMPLES**
 [Here's](https://www.quora.com/What-are-some-examples-of-very-well-made-GitHub-wiki-pages-for-open-source-projects) a list of good ones.
