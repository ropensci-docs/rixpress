# Read Output of a Derivation

Reads the output of derivations in the current session, returns a path
if reading directly is not possible.

## Usage

``` r
rxp_read(derivation_name, which_log = NULL, project_path = ".")
```

## Arguments

- derivation_name:

  Character, the name of the derivation.

- which_log:

  Character, defaults to NULL. If NULL the most recent build log is
  used. If a string is provided, it's used as a regular expression to
  match against available log files.

- project_path:

  Character, defaults to ".". Path to the root directory of the project.

## Value

The derivation's output.

## Details

When `derivation_name` points to a single R object, it gets read in the
current session using
[`readRDS()`](https://rdrr.io/r/base/readRDS.html). If it's a Python
object and `{reticulate}` is available,
[`reticulate::py_load_object()`](https://rstudio.github.io/reticulate/reference/py_save_object.html)
is used. In case the derivation is pointing to several outputs (which
can happen when building a Quarto document for example) or neither
[`readRDS()`](https://rdrr.io/r/base/readRDS.html) nor
[`reticulate::py_load_object()`](https://rstudio.github.io/reticulate/reference/py_save_object.html)
successfully read the object, the path to the object is returned
instead.

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md),
[`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md),
[`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md),
[`rxp_init()`](https://docs.ropensci.org/rixpress/reference/rxp_init.md),
[`rxp_inspect()`](https://docs.ropensci.org/rixpress/reference/rxp_inspect.md),
[`rxp_list_logs()`](https://docs.ropensci.org/rixpress/reference/rxp_list_logs.md),
[`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md),
[`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  mtcars <- rxp_read("mtcars")

  # Read from a specific build log
  mtcars <- rxp_read("mtcars", which_log = "2025-05-10")
} # }
```
