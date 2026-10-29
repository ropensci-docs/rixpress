# Package index

## Declaring derivations

Functions that define Nix derivations that run R or Python code, or
compile Quarto or R Markdown documents.

- [`rxp_jl()`](https://docs.ropensci.org/rixpress/reference/rxp_jl.md) :
  Create a Nix Expression Running a Julia Function
- [`rxp_jl_file()`](https://docs.ropensci.org/rixpress/reference/rxp_jl_file.md)
  : Creates a Nix Expression That Reads In a File (or Folder of Data)
  Using Julia
- [`rxp_py()`](https://docs.ropensci.org/rixpress/reference/rxp_py.md) :
  Create a Nix Expression Running a Python Function
- [`rxp_py_file()`](https://docs.ropensci.org/rixpress/reference/rxp_py_file.md)
  : Creates a Nix Expression That Reads In a File (or Folder of Data)
  Using Python
- [`rxp_qmd()`](https://docs.ropensci.org/rixpress/reference/rxp_qmd.md)
  : Render a Quarto Document as a Nix Derivation
- [`rxp_r()`](https://docs.ropensci.org/rixpress/reference/rxp_r.md) :
  Create a Nix Expression Running an R Function
- [`rxp_r_file()`](https://docs.ropensci.org/rixpress/reference/rxp_r_file.md)
  : Creates a Nix Expression That Reads In a File (or Folder of Data)
  Using R
- [`rxp_rmd()`](https://docs.ropensci.org/rixpress/reference/rxp_rmd.md)
  : Render an R Markdown Document as a Nix Derivation

## Building the pipeline

Functions to generate and build the Nix pipeline

- [`rxp_make()`](https://docs.ropensci.org/rixpress/reference/rxp_make.md)
  : Build Pipeline Using Nix
- [`rxp_pipeline()`](https://docs.ropensci.org/rixpress/reference/rxp_pipeline.md)
  : Create a Named Pipeline of Derivations
- [`rxp_populate()`](https://docs.ropensci.org/rixpress/reference/rxp_populate.md)
  : Generate Nix Pipeline Code

## Pipeline organization

Functions for organizing derivations into named sub-pipelines with
visual distinction in DAG visualizations.

- [`rxp_pipeline()`](https://docs.ropensci.org/rixpress/reference/rxp_pipeline.md)
  : Create a Named Pipeline of Derivations
- [`print(`*`<rxp_pipeline>`*`)`](https://docs.ropensci.org/rixpress/reference/print.rxp_pipeline.md)
  : Print Method for rxp_pipeline Objects

## Project utilities

Functions for initializing projects, copying outputs, reading
derivations, and inspecting build artifacts.

- [`print(`*`<rxp_derivation>`*`)`](https://docs.ropensci.org/rixpress/reference/print.rxp_derivation.md)
  : Print Method for Derivation Objects
- [`rxp_check_chronicles()`](https://docs.ropensci.org/rixpress/reference/rxp_check_chronicles.md)
  : Check Pipeline Outputs for Chronicle Status
- [`rxp_copy()`](https://docs.ropensci.org/rixpress/reference/rxp_copy.md)
  : Copy Derivations From the Nix Store to Current Working Directory
- [`rxp_gc()`](https://docs.ropensci.org/rixpress/reference/rxp_gc.md) :
  Garbage Collect Rixpress Build Artifacts and Logs
- [`rxp_init()`](https://docs.ropensci.org/rixpress/reference/rxp_init.md)
  : Initialize Rixpress Project
- [`rxp_inspect()`](https://docs.ropensci.org/rixpress/reference/rxp_inspect.md)
  : Inspect the Build Result of a Pipeline
- [`rxp_list_logs()`](https://docs.ropensci.org/rixpress/reference/rxp_list_logs.md)
  : List All Available Build Logs
- [`rxp_load()`](https://docs.ropensci.org/rixpress/reference/rxp_load.md)
  : Load Output of a Derivation
- [`rxp_read()`](https://docs.ropensci.org/rixpress/reference/rxp_read.md)
  : Read Output of a Derivation
- [`rxp_trace()`](https://docs.ropensci.org/rixpress/reference/rxp_trace.md)
  : Trace Lineage of Derivations

## Archive import/export

Functions for importing and exporting Nix store paths using archive
files.

- [`rxp_export_artifacts()`](https://docs.ropensci.org/rixpress/reference/rxp_export_artifacts.md)
  : Export Nix Store Paths to an Archive
- [`rxp_import_artifacts()`](https://docs.ropensci.org/rixpress/reference/rxp_import_artifacts.md)
  : Import Nix Store Paths from an Archive

## DAG and CI tools

Tools for generating DAGs and preparing pipelines for rendering or
deployment in CI environments.

- [`rxp_dag_for_ci()`](https://docs.ropensci.org/rixpress/reference/rxp_dag_for_ci.md)
  : Export DAG of Pipeline and Prepare It for Rendering on CI
- [`rxp_ga()`](https://docs.ropensci.org/rixpress/reference/rxp_ga.md) :
  Run a Pipeline on GitHub Actions
- [`rxp_write_dag()`](https://docs.ropensci.org/rixpress/reference/rxp_write_dag.md)
  : Generate a DAG From a List of Derivations

## R ↔︎ Python interop

Functions to move data and objects between R and Python runtimes.

- [`rxp_py2r()`](https://docs.ropensci.org/rixpress/reference/rxp_py2r.md)
  : Transfer Python Object into an R Session
- [`rxp_r2py()`](https://docs.ropensci.org/rixpress/reference/rxp_r2py.md)
  : Transfer R Object into a Python Session

## Visualization

Functions for visualizing pipeline DAGs using different backends.

- [`rxp_ggdag()`](https://docs.ropensci.org/rixpress/reference/rxp_ggdag.md)
  :

  Create a Directed Acyclic Graph (DAG) Representing the Pipeline Using
  [ggplot2](https://ggplot2.tidyverse.org)

- [`rxp_visnetwork()`](https://docs.ropensci.org/rixpress/reference/rxp_visnetwork.md)
  :

  Create a Directed Acyclic Graph (DAG) Representing the Pipeline Using
  [visNetwork](https://datastorm-open.github.io/visNetwork/)

## Python import manipulation

Utilities to adjust Python import statements to match project or
environment conventions.

- [`add_import()`](https://docs.ropensci.org/rixpress/reference/add_import.md)
  : Add an Import Statement to Python Files in the \_rixpress Folder
  Matching a Nix Environment Name
- [`adjust_import()`](https://docs.ropensci.org/rixpress/reference/adjust_import.md)
  : Adjust Python Import Statements
