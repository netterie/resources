
# Patrick Ball, 11/1/2018

## Resources

- Book: The Pragmatic Programmer
- Any intro to bash tutorial - just keep using those tools until they're second nature


## Major takeaways

- Separate tasks: input, code, output
- Write a single script that rules them all, if you don't do a makefile (training wheels for makefile)
- Storing params in Excel vs .yaml - it's more about convenience. Not needing to open Excel is an advantage.


## When to use these strategies

### When there's more than 2 people, use more than 2 times...etc

- Input files
- Updates to your inputs
- Analysts
- Results / types of results
- Different kinds of analyses or languages - he says leave IDE behind! Hmmmm.

### When you need to read it again 6 mos later!

### When it's complicated enough that you could be too dumb to debug your own code

### Reproducibility means being able to rerun and get same results, but it also means "reproducible writing" - embed the audit trail in the writing, so that it's easy to go back and see where things came from

## Design patterns

### Make documentation executable

Code evolves faster than documentation, so better to use "code" (relative paths, makefiles, knitr/Rmd)... we always forget to update comments. No one updates comments unless others are forcing you! Documentation can be anti-helpful --slow you down because it's outdated. So instead, write the code that actually shows what to do...

### Separate...

- Protytyping from production
- Data from logic (conflict_begins =, not x = )
- Reading from writing - if you have a good file structure, seeing "input/xfile" tells you you're reading input

### One-button build

Standardize how each task is executed, wrap complexity in standardization. This sounds like using makefiles for everything - every task can be executed using "make". Or drake - recursively execute if anything has been updated since the last time. 

### No "magic" (make changes by hand)

Interactive fiddling leaves no trace. Every change must be in code. Use hand/, args, explicit outputs... ?

Put it at the highest level that it needs to be, but no higher

### Chunk it

Every chunk is obvious what it does. Size the task so you can understand what's going on...so you can maintain a high-level view until you want to drill down. This enables debugging.

## Design tactics

- Everything is a pipeline 
- Manage project flow with relative paths
- Use unix not Windows -- once you have a terminal, you can use any computer/server/cloud/etc. Then you're not tied to a certain computer.
    - My comment is that for R, you really need to recreate the environment with MRAN or packrat
    - He says, it's not that big of a deal...they used to require certain versions...they're fine if things break? 
    - He does say it's problematic for CRAN libraries - OH he's not trying to rerun a project 4-5 years later. That's containerizig with docker. 
- Learn bash, ssh and screen (disconnect and reconnect without losing the terminal)
- Design analysis to run from scripts that accept input and output filenames as arguments (e.g., argparse in R and python). Never setwd(). 
- You can put defaults to the parser argparse commands to allow it to run in RStudio

## Documentation

- If it's long, it's wrong. Break it up and give things self-evident names (not x and i)
- Exception: things that don't change much like input data, exported data, and common libraries can benefit from documentation
- A good project is self-documenting with standard structures and metadata 
- Version control: git is good for code...data should have a different kind of version control
- Don't document the content of a project in version control...in git commit, don't write what (use git diff), but write WHY. WHY is the metadata that you can't get from git diff. Another thing is the status of the project - where you are in the process of getting to the goal: "I finished this task, I'm concerned about this, and I still need to write a test..."
    - Write an alias that gives you the last 20 git commit messages in a format that you like. Search stackoverflow. Then look at it constantly. This will remind you what's going on in a project

## The task is a quantum of workflow

### Break work into a series of tasks that link in one direction, separating reading from writing

### Structure

1. Makefile at the task level
2. src/ for code that opreates on files in input/ (written by you)
3. input/ for files coming from outside the task (read-only)
4. output/ for results of computations (written only by the machine - NOT by hand)
5. hand/ for results you do edit by hand

### Start with import/

This example is a whole folder where all it does is there's a makefile that reads in an Excel file and writes out a csv. The utility is that you can run tree at a higher level and the bug is easy to find, because import is SEPARTE from clean, export, share, and note (the other tasks - note is for notebooks)

So, import/output is the .csv file. 

Can generate a flowchart with an automatic audit that shows the dependencies, e.g. import -> filter -> clean -> standardize -> export. graphvis in python is super easy to use for this.

### Tasks separate reading from writing

They copy code from task to task or project to project...
Use assigning names to values in .yaml files. Often .yaml files are output, because the the values were computed from a prior computation.
- input/stratify.yaml looks like this:

num_year: 26
x: 50

- hand/constants.yaml (recoding work)

month_fix = c('jan'=01, 'feb'=02)

Use library(yaml) and 
library("argparse")

## Workflow ideas

- One-button build via makefiles and rel paths or symlinks
- WITHIN a project, keep yoru code "dry" - don't repeat yourself
- Extract cool stuff from old projects and let the library evolve for the new project. This allows you to rerun the old project without stifling the new one.

### Makefiles

Begin the makefile with the script that you change the most?

$< refers to the first dependency - in his exmple, src/make_magic_numbers.R

### Separate prototype from production

- You can re-run a notebook changing stuff out of order. Fine for prototyping, but bad for production - for production, you need a makefile.
- Prune code. When you make a decision, commit the new code and delete the old stuff - don't leave it as a comment. Use version control for deprecated code, and use git diff to get the old stuff back
- You're not done until the code is in version contorl and it runs on someone else's machine

### Save lots of intermediate files

- And if you're going to access it months later, it should be a text file. BUT, commas are a bad delimiter. They use the | symbol, since language doesn't use the | like it uses commas


## Editor aside

- He's pretty convinced that emacs or vim are the way to go
- Get comfy with an editor and really live there

## Auditability via tests

### Types

Never just fix a bug. First write a test that fails on the bug. Then fix the bug and watch the test pass. Keep that test (assert, unit test, or acceptance test) in the code forever. One of the powers of makefiles appears, to me, to be that you can write a test for compiling a package or knitting a whole script or other stuff that you might otherwise be hard-pressed to replicate exactly

#### Asserts (in R, stopifnot)

Everywhere you think you know what should have happened. It's like when you do a print statement and it finally comes out right - that should get turned into an assert. They also help you describe to yourself (self-executing documentation) what should happen.

#### Unit tests

For specific functions and run on simplified data. Lots of frameworks/ways to do this in R...

#### Acceptance tests

These tend to be big structures. Use when you have a lot of stuff. 




