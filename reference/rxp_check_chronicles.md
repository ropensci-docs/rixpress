# Check Pipeline Outputs for Chronicle Status

Scans all derivation outputs for chronicle objects and reports their
status: success (Just, no warnings), warning (Just with warnings), or
nothing (failed computation). Only active when chronicler is installed.

## Usage

``` r
rxp_check_chronicles(project_path = ".", which_log = NULL)
```

## Arguments

- project_path:

  Character, defaults to ".". Path to the root directory of the project.

- which_log:

  Character, defaults to NULL. If NULL the most recent build log is
  used. If a string is provided, it's used as a regular expression to
  match against available log files.

## Value

A data frame with columns: derivation, chronicle_state, num_operations,
num_failed, failed_functions, messages. Returns NULL invisibly if
chronicler is not installed or no chronicle objects are found.

## Details

This function is useful when using the `{chronicler}` package in your
rixpress pipeline. Because chronicler catches errors and warnings,
returning `Nothing` values instead of failing, Nix builds will always
succeed. This function helps identify derivations that contain failed
computations.

The function displays one of three symbols for each chronicle:

- `checkmark` Success: Just value, no warnings or errors

- `warning sign` Warning: Just value, but warnings were captured

- `X mark` Nothing: Failed computation, errors captured

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md),
[`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md),
[`rxp_init()`](https://docs.ropensci.org/rixpress/reference/rxp_init.md),
[`rxp_inspect()`](https://docs.ropensci.org/rixpress/reference/rxp_inspect.md),
[`rxp_list_logs()`](https://docs.ropensci.org/rixpress/reference/rxp_list_logs.md),
[`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md),
[`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md),
[`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # After building a pipeline with chronicler functions
  rxp_check_chronicles()

  # Check a specific build log
  rxp_check_chronicles(which_log = "20250131")
} # }
```
