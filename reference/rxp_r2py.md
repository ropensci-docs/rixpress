# Transfer R Object into a Python Session

Transfer R Object into a Python Session

## Usage

``` r
rxp_r2py(name, expr, nix_env = "default.nix", project_path = ".")
```

## Arguments

- name:

  Symbol, name of the derivation.

- expr:

  Symbol, R object to be saved into a Python pickle.

- nix_env:

  Character, path to the Nix environment file, default is "default.nix".

- project_path:

  Character, path to the project root, default is ".".

## Value

An object of class `rxp_derivation`.

## Details

`rxp_r2py(my_obj, my_r_object)` saves an R object to a Python pickle
using
[`reticulate::py_save_object()`](https://rstudio.github.io/reticulate/reference/py_save_object.html).

## See also

Other interop functions:
[`rxp_py2r()`](https://docs.ropensci.org/rixpress/reference/rxp_py2r.md)
