# Transfer Python Object into an R Session

Transfer Python Object into an R Session

## Usage

``` r
rxp_py2r(name, expr, nix_env = "default.nix", project_path = ".")
```

## Arguments

- name:

  Symbol, name of the derivation.

- expr:

  Symbol, Python object to be loaded into R.

- nix_env:

  Character, path to the Nix environment file, default is "default.nix".

- project_path:

  Character, path to the project root, default is ".".

## Value

An object of class `rxp_derivation`.

## Details

`rxp_py2r(my_obj, my_python_object)` loads a serialized Python object
and saves it as an RDS file using
[`reticulate::py_load_object()`](https://rstudio.github.io/reticulate/reference/py_save_object.html).

## See also

Other interop functions:
[`rxp_r2py()`](https://docs.ropensci.org/rixpress/reference/rxp_r2py.md)
