# Create a Nix Expression Running an R Function

Create a Nix Expression Running an R Function

## Usage

``` r
rxp_r(
  name,
  expr,
  additional_files = "",
  user_functions = "",
  nix_env = "default.nix",
  encoder = NULL,
  decoder = NULL,
  env_var = NULL,
  noop_build = FALSE
)
```

## Arguments

- name:

  Symbol, name of the derivation.

- expr:

  R code to generate the expression. Ideally it should be a call to a
  pure function, or a piped expression. Multi-line expressions are not
  supported.

- additional_files:

  Character vector, additional files to include during the build
  process. For example, if a function expects a certain file to be
  available, this is where you should include it.

- user_functions:

  Character vector, user-defined functions to include. This should be a
  script (or scripts) containing user-defined functions to include
  during the build process for this derivation. It is recommended to use
  one script per function, and only include the required script(s) in
  the derivation.

- nix_env:

  Character, path to the Nix environment file, default is "default.nix".

- encoder:

  Function or character defaults to NULL. A function used to encode
  (serialize) objects for transfer between derivations. It must accept
  two arguments: the object to encode (first), and the target file path
  (second). If your function has a different signature, wrap it to match
  this interface. By default,
  [`saveRDS()`](https://rdrr.io/r/base/readRDS.html) is used, but this
  may yield unexpected results, especially for complex objects like
  machine learning models. For instance, for `{keras}` models, use
  `keras::save_model_hdf5()` to capture the full model (architecture,
  weights, training config, optimiser state, etc.). See
  [`vignette("encoding-decoding")`](https://docs.ropensci.org/rixpress/articles/encoding-decoding.md)
  for more details.

- decoder:

  Function, character, or named vector/list, defaults to NULL. Can be:

  - A single function/string to decode (unserialize) all upstream
    objects (e.g., `readRDS`)

  - A named vector/list where names are upstream dependency names and
    values are their specific decoding functions (e.g.,
    `c(mtcars_tail = "qs::qread", mtcars_head = "read.csv")`) By
    default, [`readRDS()`](https://rdrr.io/r/base/readRDS.html) is used.
    See
    [`vignette("encoding-decoding")`](https://docs.ropensci.org/rixpress/articles/encoding-decoding.md)
    for more details.

- env_var:

  Character vector, defaults to NULL. A named vector of environment
  variables to set before running the R script, e.g.,
  `c("CMDSTAN" = "${defaultPkgs.cmdstan}/opt/cmdstan)"`. Each entry will
  be added as an export statement in the build phase.

- noop_build:

  Logical, defaults to FALSE. If TRUE, the derivation produces a no-op
  build (a stub output with no actual build steps). Any downstream
  derivations depending on a no-op build will themselves also become
  no-op builds.

## Value

An object of class derivation which inherits from lists.

## Details

At a basic level, `rxp_r(mtcars_am, filter(mtcars, am == 1))` is
equivalent to `mtcars_am <- filter(mtcars, am == 1)`. `rxp_r()`
generates the required Nix boilerplate to output a so-called
"derivation" in Nix jargon. A Nix derivation is a recipe that defines
how to create an output (in this case `mtcars_am`) including its
dependencies, build steps, and output paths.

## See also

Other derivations:
[`rxp_jl()`](https://docs.ropensci.org/rixpress/reference/rxp_jl.md),
[`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md),
[`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md),
[`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md),
[`rxp_qmd()`](https://docs.ropensci.org/rixpress/reference/rxp_qmd.md),
[`rxp_r_file()`](https://docs.ropensci.org/rixpress/reference/rxp_r_file.md),
[`rxp_rmd()`](https://docs.ropensci.org/rixpress/reference/rxp_rmd.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Basic usage
  rxp_r(name = filtered_mtcars, expr = filter(mtcars, am == 1))

  # Skip building this derivation
  rxp_r(
    name = turtles,
    expr = occurrence(species, geometry = atlantic),
    noop_build = TRUE
  )

  # Serialize object using qs
  rxp_r(
   name = filtered_mtcars,
   expr = filter(mtcars, am == 1),
   encoder = qs::qsave
  )
  # Unerialize using qs::qread in the next derivation
  rxp_r(
   name = mtcars_mpg,
   expr = select(filtered_mtcars, mpg),
   decoder = qs::qread
  )
} # }
```
