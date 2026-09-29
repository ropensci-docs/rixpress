# Render a Quarto Document as a Nix Derivation

Render a Quarto Document as a Nix Derivation

## Usage

``` r
rxp_qmd(
  name,
  qmd_file,
  additional_files = "",
  nix_env = "default.nix",
  args = "",
  env_var = NULL,
  noop_build = FALSE
)
```

## Arguments

- name:

  Symbol, derivation name.

- qmd_file:

  Character, path to .qmd file.

- additional_files:

  Character vector, additional files to include, for example a folder
  containing images to include in the Quarto document.

- nix_env:

  Character, path to the Nix environment file, default is "default.nix".

- args:

  A character of additional arguments to be passed directly to the
  `quarto` command.

- env_var:

  List, defaults to NULL. A named list of environment variables to set
  before running the Quarto render command, e.g., c(QUARTO_PROFILE =
  "production"). Each entry will be added as an export statement in the
  build phase.

- noop_build:

  Logical, defaults to FALSE. If TRUE, the derivation produces a no-op
  build (a stub output with no actual build steps). Any downstream
  derivations depending on a no-op build will themselves also become
  no-op builds.

## Value

An object of class derivation which inherits from lists.

## Details

To include built derivations in the document,
`rxp_read("derivation_name")` should be put in the .qmd file.

## See also

Other derivations:
[`rxp_jl()`](https://docs.ropensci.org/rixpress/reference/rxp_jl.md),
[`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md),
[`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md),
[`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md),
[`rxp_r()`](https://docs.ropensci.org/rixpress/reference/rxp_r.md),
[`rxp_r_file()`](https://docs.ropensci.org/rixpress/reference/rxp_r_file.md),
[`rxp_rmd()`](https://docs.ropensci.org/rixpress/reference/rxp_rmd.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Compile a .qmd file to a pdf using typst
  # `images` is a folder containing images to include in the Quarto doc
  rxp_qmd(
    name = report,
    qmd_file = "report.qmd",
    additional_files = "images",
    args = "--to typst"
  )

  # Skip building this derivation
  rxp_qmd(
    name = draft_report,
    qmd_file = "draft.qmd",
    noop_build = TRUE
  )
} # }
```
