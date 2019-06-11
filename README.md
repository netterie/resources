# This repo contains notes and examples for R resources
Folder titles meant to be self-explantory

## Tools mentioned at Cascadia-R 2019

### DataPackageR (Bryan Mayer, Fred Hutch)
Creates a package structure for creating formatted data from raw data. Versions formatted data. Requires you to update News.md every time you change formatting script(s). Pre-populates help file template for every formatted dataset. Optional to actually store raw data within this package.

Full paper
https://gatesopenresearch.org/articles/2-31

### rrtools (Ben Marwick)
Creates a package structure for your research "compendium" (fully reproducible analysis)

Overviews 
- https://annakrystalli.me/talks/r-in-repro-research.html#65
- http://inundata.org/talks/rstd19/#/0/10 (Karthik Rahm rstudio::conf 2019 talk)

Tutorial
- https://annakrystalli.me/rrtools-repro-research/create-compendium.html (made with workflowr)

### drakepkg ([Tiernan Martin](https://cascadiarconf.com/speakers/#tiernan_martin))
"The goal of drakepkg is to demonstrate how a drake workflow can be organized as an R package." I wonder if this might be a useful way to separate paper-writing from analysis code, which may be helpful for complex projects. Or, tips from the drake-driven structure of this package might be useful for including a drake plan in an _rrtools_ compendium package.

https://github.com/tiernanmartin/drakepkg
- Slides emphasize that you need to use drake::expose_imports() to bring the package into the drake environment

### workflowr
"Workflowr combines literate programming (knitr and rmarkdown) and version control (Git, via git2r) to generate a website containing time-stamped, versioned, and documented results." This seems useful for anything that can be posted publicly, unless you have a private GitLab server. 

The [example](https://stephenslab.github.io/wflow-divvy/) makes me think it would be great for tutorials.

### pkgdown
"pkgdown is designed to make it quick and easy to build a website for your package". At its simplest, its sounds like it it has 1) a home page generated from the package’s README.md, 2) a function reference generated from the documentation in the man/ directory, 3) results of any tests, and 4) changelog.

https://pkgdown.r-lib.org/

