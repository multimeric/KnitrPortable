# Portable Vignettes

* Both vignettes will work using the knit button
* However, if you try to render `not_portable` to markdown (by running the cell containing `rmarkdown::render()`), it will fail
* This is because it tries to build the images paths relative to the `vignettes` directory, but this is not where it will ultimately live
* The reason why `portable` works, is because we force the knitr `output.dir` to be the same as the root dir
* Below is a diff of the two vignettes:

```diff
11,16d10
< root_dir <- knitr::opts_knit$get("root.dir")
< if (!is.null(root_dir)){
<     knitr::opts_knit$set(
<         output.dir = root_dir
<     )
< }
23c17
<     "portable.Rmd",
---
>     "not_portable.Rmd",
```
