# Export DAG of Pipeline and Prepare It for Rendering on CI

This function generates a DOT file representation of the pipeline DAG,
suitable for visualization, potentially on CI platforms. It is called by
[`rxp_ga()`](https://docs.ropensci.org/rixpress/reference/rxp_ga.md).

## Usage

``` r
rxp_dag_for_ci(
  nodes_and_edges = get_nodes_edges(),
  output_file = "_rixpress/dag.dot"
)
```

## Arguments

- nodes_and_edges:

  List, output of `get_nodes_edges()`. Defaults to calling
  `get_nodes_edges()`.

- output_file:

  Character, the path where the DOT file should be saved. Defaults to
  `"_rixpress/dag.dot"`. The directory will be created if it doesn't
  exist.

## Value

Nothing, writes the DOT file to the specified `output_file`.

## See also

Other ci utilities:
[`rxp_ga()`](https://docs.ropensci.org/rixpress/reference/rxp_ga.md),
[`rxp_write_dag()`](https://docs.ropensci.org/rixpress/reference/rxp_write_dag.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  # Generate the default _rixpress/dag.dot
  rxp_dag_for_ci()

} # }
```
