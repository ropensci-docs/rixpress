# Build Pipeline Using Nix

Runs `nix-build` with a quiet flag, outputting to `_rixpress/result`.

## Usage

``` r
rxp_make(verbose = 0L, max_jobs = 1, cores = 1)
```

## Arguments

- verbose:

  Integer, defaults to 0L. Verbosity level: 0 = show progress indicators
  only, 1+ = show nix output with increasing verbosity. 0: "Progress
  only", 1: "Informational", 2: "Talkative", 3: "Chatty", 4: "Debug", 5:
  "Vomit". Values higher than 5 are capped to 5. Each level adds one
  –verbose flag to nix-store command.

- max_jobs:

  Integer, number of derivations to be built in parallel.

- cores:

  Integer, number of cores a derivation can use during build.

## Value

A character vector of paths to the built outputs.

## Details

When the `{chronicler}` package is available, `rxp_make()` automatically
calls
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md)
after a successful build to check for `Nothing` values in chronicle
objects. This helps detect silent failures in pipelines that use
chronicler's `record()` decorated functions. See
[`vignette("chronicler")`](https://docs.ropensci.org/rixpress/articles/chronicler.md)
for more details.

## See also

Other pipeline functions:
[`rxp_pipeline()`](https://docs.ropensci.org/rixpress/reference/rxp_pipeline.md),
[`rxp_populate()`](https://docs.ropensci.org/rixpress/reference/rxp_populate.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Build the pipeline with progress indicators (default)
  rxp_make()

  # Build with verbose output and parallel execution
  rxp_make(verbose = 2, max_jobs = 4, cores = 2)

  # Maximum verbosity
  rxp_make(verbose = 3)
} # }
```
