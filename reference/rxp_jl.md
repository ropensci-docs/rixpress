# Create a Nix Expression Running a Julia Function

Create a Nix Expression Running a Julia Function

## Usage

``` r
rxp_jl(
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

  Character, Julia code to generate the expression. Ideally it should be
  a call to a pure function. Multi-line expressions are not supported.

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

  Character, defaults to NULL. The name of the Julia function used to
  serialize the object. It must accept two arguments: the object to
  serialize (first), and the target file path (second). If NULL, the
  default behaviour uses the built‐in `Serialization.serialize` API.
  Define any custom serializer in `functions.jl`. See
  [`vignette("encoding-decoding")`](https://docs.ropensci.org/rixpress/articles/encoding-decoding.md)
  for more details.

- decoder:

  Character or named vector/list, defaults to NULL. Can be:

  - A single string for the Julia function to unserialize all upstream
    objects

  - A named vector/list where names are upstream dependency names and
    values are their specific unserialize functions If NULL, the default
    is `Serialization.deserialize`. See
    [`vignette("encoding-decoding")`](https://docs.ropensci.org/rixpress/articles/encoding-decoding.md)
    for more details.

- env_var:

  Character vector, defaults to NULL. A named vector of environment
  variables to set before running the Julia script, e.g.,
  `c("JULIA_DEPOT_PATH" = "/path/to/depot")`. Each entry will be added
  as an `export` statement in the build phase.

- noop_build:

  Logical, defaults to FALSE. If TRUE, the derivation produces a no-op
  build (a stub output with no actual build steps). Any downstream
  derivations depending on a no-op build will themselves also become
  no-op builds.

## Value

An object of class derivation which inherits from lists.

## Details

At a basic level, `rxp_jl(filtered_data, "filter(df, :col .> 10)")` is
equivalent to `filtered_data = filter(df, :col .> 10)` in Julia.
`rxp_jl()` generates the required Nix boilerplate to output a so‐called
"derivation" in Nix jargon. A Nix derivation is a recipe that defines
how to create an output (in this case `filtered_data`) including its
dependencies, build steps, and output paths.

## See also

Other derivations:
[`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md),
[`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md),
[`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md),
[`rxp_qmd()`](https://docs.ropensci.org/rixpress/reference/rxp_qmd.md),
[`rxp_r()`](https://docs.ropensci.org/rixpress/reference/rxp_r.md),
[`rxp_r_file()`](https://docs.ropensci.org/rixpress/reference/rxp_r_file.md),
[`rxp_rmd()`](https://docs.ropensci.org/rixpress/reference/rxp_rmd.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Basic usage, no custom serializer
rxp_jl(
  name = filtered_df,
  expr = "filter(df, :col .> 10)"
)

# Skip building this derivation
rxp_jl(
  name = model_result,
  expr = "train_model(data)",
  noop_build = TRUE
)

# Custom serialization: assume `save_my_obj(obj, path)` is defined in functions.jl
rxp_jl(
  name = model_output,
  expr = "train_model(data)",
  encoder = "save_my_obj",
  user_functions = "functions.jl"
)
} # }
```
