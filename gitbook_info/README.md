
# Getting started with bookdown for Gitbooks

Again, please jump in

## Set up your template
- In RStudio, 
   - File --> New Project --> New Directory
   - Choose "Book project using bookdown"
   - Click "Build Book"

## Modify _bookdown.yml
- [EpiModelEDA example](https://github.com/statnet/EpiModelEDA/blob/master/_bookdown.yml)

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
You WILL spend more time debugging, because it's a more complex file structure

Book is useful when there is so much content that you 
- save time by knitting chapters separately
- navigate faster from the clean look of the bookdown TOC?

Other benefits:
- Can easily make a public website by saving the output to repo/docs and turning on the github.io website
- Aesthetics




