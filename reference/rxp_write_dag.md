# Generate a DAG From a List of Derivations

Creates a JSON representation of a directed acyclic graph (DAG) based on
dependencies between derivations. Is automatically called by
[`rxp_populate()`](https://docs.ropensci.org/rixpress/reference/rxp_populate.md).

## Usage

``` r
rxp_write_dag(rxp_list, output_file = "_rixpress/dag.json")
```

## Arguments

- rxp_list:

  A list of derivations.

- output_file:

  Path to the output JSON file. Defaults to "\_rixpress/dag.json".

## Value

Nothing, writes a JSON file representing the DAG.

## See also

Other ci utilities:
[`rxp_dag_for_ci()`](https://docs.ropensci.org/rixpress/reference/rxp_dag_for_ci.md),
[`rxp_ga()`](https://docs.ropensci.org/rixpress/reference/rxp_ga.md)

## Examples

``` r
if (FALSE) { # \dontrun{
  rxp_write_dag(rxp_list)
} # }
```
