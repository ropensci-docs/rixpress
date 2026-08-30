# Inspect the Build Result of a Pipeline

Returns a data frame with four columns: - derivation: the name of the
derivation - build_success: whether the build was successful or not -
path: the path of this derivation in the Nix store - output: the output,
if this derivation was built successfully. Empty outputs mean that this
derivation was not built successfully. Several outputs for a single
derivation are possible. In the `derivation` column you will find an
object called `all-derivations`. This object is generated automatically
for internal purposes, and you can safely ignore it.

## Usage

``` r
rxp_inspect(project_path = ".", which_log = NULL)
```

## Arguments

- project_path:

  Character, defaults to ".". Path to the root directory of the project.

- which_log:

  Character, defaults to NULL. If NULL the most recent build log is
  used. If a string is provided, it's used as a regular expression to
  match against available log files.

## Value

A data frame with derivation names, if their build was successful, their
paths in the /nix/store, and their build outputs.

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md),
[`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md),
[`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md),
[`rxp_init()`](https://docs.ropensci.org/rixpress/reference/rxp_init.md),
[`rxp_list_logs()`](https://docs.ropensci.org/rixpress/reference/rxp_list_logs.md),
[`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md),
[`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md),
[`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Inspect the most recent build
  build_results <- rxp_inspect()

  # Inspect a specific build log
  build_results <- rxp_inspect(which_log = "20250510")

  # Check which derivations failed
  failed <- subset(build_results, !build_success)
} # }
```
