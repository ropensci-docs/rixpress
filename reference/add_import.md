# Add an Import Statement to Python Files in the \_rixpress Folder Matching a Nix Environment Name

This function appends a specified import statement to the end of each
Python file within the `_rixpress` folder and its subdirectories, but
only for files whose base name matches the provided Nix environment.

## Usage

``` r
add_import(import_statement, nix_env, project_path = ".")
```

## Arguments

- import_statement:

  A character string representing the import statement to be added. For
  example, `"import numpy as np"`.

- nix_env:

  A character string naming the Nix environment file (e.g.
  `"default.nix"` or `"py-env.nix"` or similar).

- project_path:

  Path to root of project, typically ".".

## Value

No return value; the function performs in-place modifications of the
files.

## See also

Other python import:
[`adjust_import()`](https://docs.ropensci.org/rixpress/reference/adjust_import.md)

## Examples

``` r
if (FALSE) { # \dontrun{
add_import("import numpy as np", "default.nix")
add_import("import numpy as np", "default.nix", project_path = "path/to/project")
} # }
```
