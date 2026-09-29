# Copy Derivations From the Nix Store to Current Working Directory

When Nix builds a derivation, its output is saved in the Nix store
located under `/nix/store/`. Even though you can import the derivations
into the current R session using
[`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md)
or
[`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md),
it can be useful to copy the outputs to the current working directory.
This is especially useful for Quarto documents, where there can be more
than one input, as is the case for `html` output.

## Usage

``` r
rxp_copy(derivation_name = NULL, dir_mode = "0755", file_mode = "0644")
```

## Arguments

- derivation_name:

  The name of the derivation to copy. If empty, then all the derivations
  are copied.

- dir_mode:

  Character, default "0755". POSIX permission mode to apply to
  directories under the copied output (including the top-level output
  directory).

- file_mode:

  Character, default "0644". POSIX permission mode to apply to files
  under the copied output.

## Value

Nothing, the contents of the Nix store are copied to the current working
directory.

## See also

Other utilities:
[`print.rxp_derivation()`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md),
[`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md),
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
  # Copy all derivations to the current working directory
  rxp_copy()

  # Copy a specific derivation
  rxp_copy("mtcars")

  # Copy with custom permissions (e.g., make scripts executable)
  rxp_copy("my_deriv", dir_mode = "0755", file_mode = "0644")

  # Copy a Quarto document output with multiple files
  rxp_copy("my_quarto_doc")
} # }
```
