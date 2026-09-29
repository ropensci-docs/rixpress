# Render an R Markdown Document as a Nix Derivation

Render an R Markdown Document as a Nix Derivation

## Usage

``` r
rxp_rmd(
  name,
  rmd_file,
  additional_files = "",
  nix_env = "default.nix",
  params = NULL,
  env_var = NULL,
  noop_build = FALSE
)
```

## Arguments

- name:

  Symbol, derivation name.

- rmd_file:

  Character, path to .Rmd file.

- additional_files:

  Character vector, additional files to include, for example a folder
  containing the pictures to include in the R Markdown document.

- nix_env:

  Character, path to the Nix environment file, default is "default.nix".

- params:

  List, parameters to pass to the R Markdown document. Default is NULL.

- env_var:

  List, defaults to NULL. A named list of environment variables to set
  before running the R Markdown render command, e.g., c(RSTUDIO_PANDOC =
  "/path/to/pandoc"). Each entry will be added as an export statement in
  the build phase.

- noop_build:

  Logical, defaults to FALSE. If TRUE, the derivation produces a no-op
  build (a stub output with no actual build steps). Any downstream
  derivations depending on a no-op build will themselves also become
  no-op builds.

## Value

An object of class derivation which inherits from lists.

## Details

To include objects built in the pipeline, `rxp_read("derivation_name")`
should be put in the .Rmd file.

## See also

Other derivations:
[`rxp_jl()`](https://docs.ropensci.org/rixpress/reference/rxp_jl.md),
[`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md),
[`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md),
[`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md),
[`rxp_qmd()`](https://docs.ropensci.org/rixpress/reference/rxp_qmd.md),
[`rxp_r()`](https://docs.ropensci.org/rixpress/reference/rxp_r.md),
[`rxp_r_file()`](https://docs.ropensci.org/rixpress/reference/rxp_r_file.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Compile a .Rmd file to a pdf
  # `images` is a folder containing images to include in the R Markdown doc
  rxp_rmd(
    name = report,
    rmd_file = "report.Rmd",
    additional_files = "images"
  )

  # Skip building this derivation
  rxp_rmd(
    name = draft_report,
    rmd_file = "draft.Rmd",
    noop_build = TRUE
  )
} # }
```
