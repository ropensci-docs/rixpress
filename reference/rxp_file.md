# Generic Nix Expression Builder for R, Python, and Julia Data Readers

You should not call it directly, but instead use one of
[`rxp_r_file()`](https://docs.ropensci.org/rixpress/reference/rxp_r_file.md),
[`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md)
or
[`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md).

## Usage

``` r
rxp_file(
  lang,
  name,
  path,
  read_function,
  user_functions = "",
  nix_env = "default.nix",
  env_var = NULL,
  encoder = NULL
)
```

## Arguments

- lang:

  `"R"`, `"Py"` or `"Jl"`.

- name:

  Symbol, the name of the derivation.

- path:

  Character, the file path to include (e.g., "data/mtcars.shp") or a
  folder path (e.g., "data"). See details.

- read_function:

  Function, an R function to read the data, taking one argument (the
  path). This can be a user-defined function that is made available
  using `user_functions`. See details.

- user_functions:

  Character vector, user-defined functions to include. This should be a
  script (or scripts) containing user-defined functions to include
  during the build process for this derivation. It is recommended to use
  one script per function, and only include the required script(s) in
  the derivation.

- nix_env:

  Character, path to the Nix environment file, default is "default.nix".

- env_var:

  List, defaults to NULL. A named list of environment variables to set
  before running the R script, e.g., c(VAR = "hello"). Each entry will
  be added as an export statement in the build phase.

- encoder:

  Function/character, defaults to NULL. A language-specific serializer
  to write the loaded object to disk.

  - R: function/symbol/character (e.g., `qs::qsave`) taking
    `(object, path)`. Defaults to `saveRDS`.

  - Python: character name of a function taking `(object, path)`.
    Defaults to using `pickle.dump`.

  - Julia: character name of a function taking `(object, path)`.
    Defaults to using `Serialization.serialize`.

## Value

An object of class `rxp_derivation`.

## Details

Creates a Nix derivation that reads a file or folder of data using R,
Python, or Julia. Handles user-defined functions, environment variables,
and Nix environment specification.
