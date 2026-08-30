# Create a Named Pipeline of Derivations

Groups multiple derivations into a named pipeline for organizational
purposes. This allows you to structure large projects into logical
sub-pipelines (e.g., "ETL", "Model", "Report") that are visually
distinguished in DAG visualizations.

## Usage

``` r
rxp_pipeline(name, path, color = NULL, ...)
```

## Arguments

- name:

  Character, the name of the pipeline (e.g., "ETL", "Model").

- path:

  Character path to an R script returning a list of derivations, OR a
  list of derivation objects created by
  [`rxp_r()`](https://docs.ropensci.org/rixpress/reference/rxp_r.md),
  [`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md),
  etc.

- color:

  Character, optional. A CSS color name (e.g., "darkorange") or hex code
  (e.g., "#FF5733") to use for this pipeline's nodes in DAG
  visualizations. If NULL, a default color will be assigned.

- ...:

  Additional arguments (currently unused, reserved for future use).

## Value

An object of class `rxp_pipeline` containing the derivations with
pipeline metadata attached.

## Details

The `rxp_pipeline()` function is used to organize derivations into
logical groups. When passed to
[`rxp_populate()`](https://docs.ropensci.org/rixpress/reference/rxp_populate.md),
the derivations are flattened but retain their group and color metadata,
which is then used in DAG visualizations
([`rxp_visnetwork()`](https://docs.ropensci.org/rixpress/reference/rxp_visnetwork.md)
and
[`rxp_ggdag()`](https://docs.ropensci.org/rixpress/reference/rxp_ggdag.md))
to distinguish different parts of your workflow.

This pattern enables a "Master Script" workflow where you can define
sub-pipelines in separate R scripts that each return a list of
derivations. You then pass the paths to these scripts to
`rxp_pipeline()`:

## See also

Other pipeline functions:
[`rxp_make()`](https://docs.ropensci.org/rixpress/reference/rxp_make.md),
[`rxp_populate()`](https://docs.ropensci.org/rixpress/reference/rxp_populate.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Define derivations in separate scripts
  # pipelines/01_etl.R returns: list(rxp_r(...), rxp_r(...))
  # pipelines/02_model.R returns: list(rxp_r(...), rxp_r(...))

  # Master script (run.R):

  # Create named pipelines with colors by pointing to the files
  pipe_etl <- rxp_pipeline("ETL", "pipelines/01_etl.R", color = "darkorange")
  pipe_model <- rxp_pipeline("Model", "pipelines/02_model.R", color = "dodgerblue")

  # Build the combined pipeline
  rxp_populate(list(pipe_etl, pipe_model))
  rxp_make()

  # Visualize - ETL nodes will be orange, Model nodes will be blue
  rxp_visnetwork()
} # }
```
