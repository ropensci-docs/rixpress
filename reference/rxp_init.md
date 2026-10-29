# Initialize Rixpress Project

Generates `gen-env.R` and `gen-pipeline.R` scripts in the specified
project directory, after asking the user for confirmation. If the user
declines, no changes are made.

## Usage

``` r
rxp_init(project_path = ".", skip_prompt = FALSE)
```

## Arguments

- project_path:

  Character string specifying the project's path.

- skip_prompt:

  Logical. If TRUE, skips all confirmation prompts and proceeds with
  initialization, useful on continuous integration. Defaults to FALSE.

## Value

Logical. Returns TRUE if initialization was successful, FALSE if the
operation was cancelled by the user.

## Details

Creates (overwriting if they already exist):

- `gen-env.R`: Script to define an execution environment with `{rix}`.

- `gen-pipeline.R`: Defines a data pipeline with `{rixpress}`.

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md),
[`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md),
[`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md),
[`rxp_inspect()`](https://docs.ropensci.org/rixpress/reference/rxp_inspect.md),
[`rxp_list_logs()`](https://docs.ropensci.org/rixpress/reference/rxp_list_logs.md),
[`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md),
[`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md),
[`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)

## Examples

``` r
# Default usage (will prompt before any action)
if (FALSE) { # \dontrun{
  rxp_init()
} # }
```
