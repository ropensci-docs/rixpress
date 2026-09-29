# Load Output of a Derivation

Loads the output of derivations in the parent frame of the current
session, returns a path if reading directly is not possible.

## Usage

``` r
rxp_load(derivation_name, which_log = NULL, project_path = ".")
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

Nothing, this function has the side effect of loading objects into the
parent frame.

## Details

When `derivation_name` points to a single R object, it gets loaded in
the current session using `assign(..., envir = parent.frame())`, which
corresponds to the global environment in a regular interactive session.
If you're trying to load a Python object and `{reticulate}` is
available,
[`reticulate::py_load_object()`](https://rstudio.github.io/reticulate/reference/py_save_object.html)
is used and then the object gets loaded into the global environment. In
case the derivation is pointing to several outputs (which can happen
when building a Quarto document for example) or loading fails, the path
to the object is returned instead.

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md),
[`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md),
[`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md),
[`rxp_init()`](https://docs.ropensci.org/rixpress/reference/rxp_init.md),
[`rxp_inspect()`](https://docs.ropensci.org/rixpress/reference/rxp_inspect.md),
[`rxp_list_logs()`](https://docs.ropensci.org/rixpress/reference/rxp_list_logs.md),
[`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md),
[`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Load an R object
  rxp_load("mtcars")

  # Load a Python object
  rxp_load("my_python_model")

  # Load from a specific build log
  rxp_load("mtcars", which_log = "2025-05-10")
} # }
```
