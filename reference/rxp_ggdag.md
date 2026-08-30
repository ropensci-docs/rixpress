# Create a Directed Acyclic Graph (DAG) Representing the Pipeline Using `{ggplot2}`

Uses `{ggdag}` to generate the plot. `{ggdag}` is a soft dependency of
`{rixpress}` so you need to install it to use this function. When
derivations are organized into pipelines using
[`rxp_pipeline()`](https://docs.ropensci.org/rixpress/reference/rxp_pipeline.md),
nodes use a dual-encoding approach: the interior fill shows the
derivation type (R, Python, etc.) while a thick border shows the
pipeline group colour.

## Usage

``` r
rxp_ggdag(
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
  nodes are coloured entirely by derivation type (rxp_r, rxp_py, etc.).

- colour_by:

  Character, alias for `color_by`.

## Value

A `{ggplot2}` object.

## See also

Other visualisation functions:
[`rxp_visnetwork()`](https://docs.ropensci.org/rixpress/reference/rxp_visnetwork.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  rxp_ggdag()  # Dual encoding: fill = type, border = pipeline
  rxp_ggdag(colour_by = "type")  # Color entirely by derivation type
} # }
```
