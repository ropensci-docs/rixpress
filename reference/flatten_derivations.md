# Flatten a list of derivations and pipelines

Takes a potentially nested list containing both `rxp_derivation` objects
and `rxp_pipeline` objects and returns a flat list of derivations with
metadata preserved.

## Usage

``` r
flatten_derivations(derivs)
```

## Arguments

- derivs:

  A list that may contain `rxp_derivation` objects, `rxp_pipeline`
  objects, or a mix of both.

## Value

A flat list of `rxp_derivation` objects.
