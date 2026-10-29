# List All Available Build Logs

Returns a data frame with information about all build logs in the
project's \_rixpress directory.

## Usage

``` r
rxp_list_logs(project_path = ".")
```

## Arguments

- project_path:

  Character, defaults to ".". Path to the root directory of the project.

## Value

A data frame with log filenames, modification times, and file sizes.

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md),
[`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md),
[`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md),
[`rxp_init()`](https://docs.ropensci.org/rixpress/reference/rxp_init.md),
[`rxp_inspect()`](https://docs.ropensci.org/rixpress/reference/rxp_inspect.md),
[`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md),
[`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md),
[`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # List all build logs in the current project
  logs <- rxp_list_logs()

  # List logs from a specific project directory
  logs <- rxp_list_logs("path/to/project")
} # }
```
