
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Idea

The idea behind *So You Want To Use Rcpp?* would be to create a guide to
Rcpp that takes an incredibly practical and R package centric approach.

The motivation for its existance is to create a guide that teaches an
experienced R developer *just enough* about C++ and Rcpp to be
dangerous, while also pointing out a number of pitfalls and issues they
are likely to run into along the way.

For instance, going from an R package with a single file `src/` repo to
having multiple files that reference each other introduces an incredibly
large amount of new infrastructure that a user won’t know they need
until they spend hours researching stack overflow and trying to wade
through C++ help guides for information relevant to their question which
is specialized to the R package context. It would be better to provide
advice on these common patterns up front, so new users can be nudged in
the right direction from the beginning.

It would assume that the user has little to no experience with C++ but
intermediate experience with R, and teach everything from:

  - What are the file types in C++?
  - Where do header files generally go in R packages?
  - How do I write a C++ function in one file and call it from another
    in an R package?
  - What are the basic R data structures in C++?
  - What methods are available for debugging C++ code?
  - C++ data types
  - SEXP type variants
  - Custom as\<\>() and wrap()
  - Talk about how as\<\>() and wrap() help with automatic argument
    conversion
  - Using custom types in an R package, and how
    `inst/include/packagename_types.h` is needed so they can be found in
    `RcppExports.cpp`
  - When would I use C++11 and C++14?
  - How would I tell R I need to use C++11? (SystemRequirements /
    Makevars)
  - What does a Makevars file do?
  - How do I build an R package with C++ files using devtools?
  - How to prototype an algorithm in R (with for loops\!), to more
    easily convert it to C++

This guide would have a heavy focus on practical user examples. It would
likely opt for a mix of full C++ file examples that can be sourced with
`Rcpp::sourceCpp()`, and multiple mini R packages with C++ source files
that can easily be cloned and installed.

It would be an open bookdown repo so the community can have a complete
and free guide for getting started.

# Outline

  - Introduction
      - Practical introduction, for R developers everywhere.
      - Focusing on the “What I Wish I Knew” points
  - Motivation
      - Why use Rcpp?
      - A speed example over base R
      - Doing things that can’t be done in base R example
      - Some existing powerful packages (dplyr, purrr, RcppArmadillo)
  - An R focused intro to C++
      - (All examples are sourcable to run in R)
      - Rcpp functions
          - Write an R function first
          - Then compare to C++ implementation
          - Rcpp::sourceCpp()
          - RMarkdown code block
      - Rcpp data types
          - Talk about SEXP types
          - Talk about NumericVector, NumericMatrix and friends
          - Abstract over underlying stuff like StoragePolicy class, etc
      - C++ includes
          - vector
          - algorithm
      - Namespaces
          - Could compare to packages
          - using namespace Rcpp
          - Compare with Rcpp::
  - Creating an algorithm in C++
      - Start the algorithm in R
      - Maybe have a fast version and a loop version
      - Talk about how C++ loops are fast
      - Rewrite in C++, hopefully it looks similar to R
      - Potentially a good place for \[\[Rcpp::depends\]\]
      - And \[\[Rcpp::plugins\]\]
  - R package Whole Game
      - Full R package with C++ walkthrough (Inspired by r-pkgs reboot
        Whole Game)
      - R package with embedded library walkthrough?
  - Creating an R package with Rcpp
      - A recap of creating an R package
      - The `src/` directory
          - Adding a C++ function to a package
          - RcppExports
          - Rcpp::compileAttributes()
      - A development workflow
          - devtools::load\_all()
          - Run it again, no recompilation\!
          - devtools::clean\_dll()
      - Expanding to multiple files
          - Adding a second C++ function to a package (in the same file)
          - Having one function call the other
          - Moving that function to a new file for clarity
          - Headers
          - Calling a function from another file
          - devtools::load\_all() when only 1 file changes (not a full
            recompile)
      - The `inst/` directory
          - Organizing headers in the inst/ directory
          - Custom types
          - RcppExports (revisited)
          - Exposing your library to other packages
          - `inst/include/tools/`
      - Makevars
          - PKG\_CXXFLAGS
          - Makevars.win
          - What else?
      - configure
          - Ugh
      - Library infrastructure
          - Helper headers
          - Error handling cpp functions
      - CRAN ready packages with C++
  - Bundling third party libraries
      - Header only library
      - Library with cpp files to compile
  - Misc
      - Dynamic typing
          - Templates
          - SEXP types (revisited)
          - TYPEOF and switch() statements
      - Custom namespaces
      - Reference material (links to as many vignettes / presentations
        as I can find)
