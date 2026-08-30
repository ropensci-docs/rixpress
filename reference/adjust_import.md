# Adjust Python Import Statements

When calling
[`rxp_populate()`](https://docs.ropensci.org/rixpress/reference/rxp_populate.md),
a file containing Python import statements is automatically generated
inside the `_rixpress` folder. For example, if the `numpy` package is
needed, the file will include a line like `"import numpy"`. However,
Python programmers often write `"import numpy as np"` instead.

## Usage

``` r
adjust_import(old_import, new_import, project_path = ".")
```

## Arguments

- old_import:

  A character string representing the import statement to be replaced.
  For example, `"import pillow"`.

- new_import:

  A character string representing the new import statement to replace
  with. For example, `"from PIL import Image"`.

- project_path:

  Path to root of project, typically ".".

## Value

No return value; the function performs in-place modifications of the
files.

## Details

In some cases, the correct import statement is entirely different. For
example, for the `pillow` package, the generated file will contain
`"import pillow"`, which is incorrect—Python code should import from the
`PIL` namespace instead, e.g., `"from PIL import Image"`.

Because these adjustments cannot be automated reliably, the
`adjust_import()` function allows you to search and replace import
statements programmatically. It reads each file in the `_rixpress`
folder, performs the replacement, and writes the modified content back
to the file.

## See also

Other python import:
[`add_import()`](https://docs.ropensci.org/rixpress/reference/add_import.md)

## Examples

``` r
if (FALSE) { # \dontrun{
adjust_import("import pillow", "from PIL import Image")
adjust_import("import pillow", "from PIL import Image", project_path = "path/to/project")
} # }
```
