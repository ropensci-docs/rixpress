# Creates a Nix Expression That Reads In a File (or Folder of Data) Using R

Creates a Nix Expression That Reads In a File (or Folder of Data) Using
R

## Usage

``` r
rxp_r_file(...)
```

## Arguments

- ...:

  Arguments passed on to
  [`rxp_file`](https://docs.ropensci.org/rixpress/reference/rxp_file.md)

  `name`

  :   Symbol, the name of the derivation.

  `path`

  :   Character, the file path to include (e.g., "data/mtcars.shp") or a
      folder path (e.g., "data"). See details.

  `read_function`

  :   Function, an R function to read the data, taking one argument (the
      path). This can be a user-defined function that is made available
      using `user_functions`. See details.

  `user_functions`

  :   Character vector, user-defined functions to include. This should
      be a script (or scripts) containing user-defined functions to
      include during the build process for this derivation. It is
      recommended to use one script per function, and only include the
      required script(s) in the derivation.

  `nix_env`

  :   Character, path to the Nix environment file, default is
      "default.nix".

  `env_var`

  :   List, defaults to NULL. A named list of environment variables to
      set before running the R script, e.g., c(VAR = "hello"). Each
      entry will be added as an export statement in the build phase.

  `encoder`

  :   Function/character, defaults to NULL. A language-specific
      serializer to write the loaded object to disk.

      - R: function/symbol/character (e.g., `qs::qsave`) taking
        `(object, path)`. Defaults to `saveRDS`.

      - Python: character name of a function taking `(object, path)`.
        Defaults to using `pickle.dump`.

      - Julia: character name of a function taking `(object, path)`.
        Defaults to using `Serialization.serialize`.

## Value

An object of class `rxp_derivation`.

## Details

The basic usage is to provide a path to a file, and the function to read
it. For example:
`rxp_r_file(mtcars, path = "data/mtcars.csv", read_function = read.csv)`.
It is also possible instead to point to a folder that contains many
files that should all be read at once, for example:
`rxp_r_file(many_csvs, path = "data", read_function = \(x)(readr::read_csv(list.files(x, full.names = TRUE, pattern = ".csv$"))))`.
See the
[`vignette("importing-data")`](https://docs.ropensci.org/rixpress/articles/importing-data.md)
vignette for more detailed examples.

## See also

Other derivations:
[`rxp_jl()`](https://docs.ropensci.org/rixpress/reference/rxp_jl.md),
[`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md),
[`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md),
[`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md),
[`rxp_qmd()`](https://docs.ropensci.org/rixpress/reference/rxp_qmd.md),
[`rxp_r()`](https://docs.ropensci.org/rixpress/reference/rxp_r.md),
[`rxp_rmd()`](https://docs.ropensci.org/rixpress/reference/rxp_rmd.md)
