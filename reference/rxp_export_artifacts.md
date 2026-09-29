# Export Nix Store Paths to an Archive

Creates a single archive file containing the specified Nix store paths
and their dependencies. This archive can be transferred to another
machine and imported into its Nix store.

## Usage

``` r
rxp_export_artifacts(
  archive_file = "_rixpress/pipeline_outputs.nar",
  which_log = NULL,
  project_path = "."
)
```

## Arguments

- archive_file:

  Character, path to the archive, defaults to
  "\_rixpress/pipeline-outputs.nar"

- which_log:

  Character or NULL, regex pattern to match a specific log file. If NULL
  (default), the most recent log file will be used.

- project_path:

  Character, defaults to ".". Path to the root directory of the project.

## Value

Nothing, creates an archive file at the specified location.

## See also

Other archive caching functions:
[`rxp_import_artifacts()`](https://docs.ropensci.org/rixpress/reference/rxp_import_artifacts.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Export the most recent build to the default location
  rxp_export_artifacts()

  # Export a specific build to a custom location
  rxp_export_artifacts(
    archive_file = "my_archive.nar",
    which_log = "20250510"
  )
} # }
```
