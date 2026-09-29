# Import Nix Store Paths from an Archive

Imports the store paths contained in an archive file into the local Nix
store. Useful for transferring built outputs between machines.

## Usage

``` r
rxp_import_artifacts(archive_file = "_rixpress/pipeline_outputs.nar")
```

## Arguments

- archive_file:

  Character, path to the archive, defaults to
  "\_rixpress/pipeline-outputs.nar"

## Value

Nothing, imports the archive contents into the local Nix store.

## See also

Other archive caching functions:
[`rxp_export_artifacts()`](https://docs.ropensci.org/rixpress/reference/rxp_export_artifacts.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Import from the default archive location
  rxp_import_artifacts()

  # Import from a custom archive file
  rxp_import_artifacts("path/to/my_archive.nar")
} # }
```
