# Create a Directed Acyclic Graph (DAG) Representing the Pipeline Using `{visNetwork}`

Uses `{visNetwork}` to generate the plot. `{visNetwork}` is a soft
dependency of `{rixpress}` so you need to install it to use this
function. When derivations are organized into pipelines using
[`rxp_pipeline()`](https://docs.ropensci.org/rixpress/reference/rxp_pipeline.md),
nodes use a dual-encoding approach: the interior fill shows the
derivation type (R, Python, etc.) while the border shows the pipeline
group colour.

## Usage

``` r
rxp_visnetwork(
  nodes_and_edges = get_nodes_edges(),
  color_by = c("pipeline", "type"),
  colour_by = NULL
)
```

## Arguments

- nodes_and_edges:

  List, output of `get_nodes_edges()`.

- color_by:

  Character, either "pipeline" (default) or "type". When "pipeline",
  nodes show type as fill colour and pipeline as border. When "type",
  nodes are colored by their derivation type (rxp_r, rxp_py, etc.).

- colour_by:

  Character, alias for `color_by`.

## Value

Nothing, this function opens a new tab in your browser with the DAG
generated using `{visNetwork}`.

## See also

Other visualisation functions:
[`rxp_ggdag()`](https://docs.ropensci.org/rixpress/reference/rxp_ggdag.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  rxp_visnetwork()
  rxp_visnetwork(colour_by = "type")  # Color by derivation type instead
} # }
```
