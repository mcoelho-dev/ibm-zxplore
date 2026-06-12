# DSN1 - Dataset Handling with ISPF
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering dataset manipulation using a 3270 terminal and
ISPF. Covers navigating the ISPF Utility panels, allocating new partitioned
datasets, copying members between datasets, and deleting datasets — mirroring
the same operations previously done in VSCode with the Zowe extension.

## What I practiced
- **ISPF navigation** — using shortcut codes like `=3.3` and `=3.4` to jump
  directly to panels without returning to the Primary Option Menu
- **DSLIST** — filtering and browsing datasets by name level (e.g. `ZXP.PUBLIC`)
- **Viewing members** — opening a PDS and browsing members with `v` and `s` commands
- **Dataset allocation** — using the Data Set Utility to allocate a new PDS
  (`Z76689.JCL.NEW`) based on properties from an existing dataset
- **Move/Copy Utility** — copying all members from a source dataset into a
  newly allocated target dataset using `'Z76689.INPUT(*)'`
- **Dataset deletion** — selecting multiple datasets for deletion with the `d`
  command in DSLIST
- **Job submission** — submitting validation JCL via `tso submit 'ZXP.PUBLIC.JCL(CHKTSO3)'`

## Commands used
| Command / Key | Description |
|---|---|
| `=3.3` | Jump directly to Move/Copy Utility |
| `=3.4` | Jump directly to DSLIST |
| `v` | View a dataset or member in DSLIST |
| `s` | Select a member to open |
| `a` | Allocate a new dataset |
| `c` | Copy in Move/Copy Utility |
| `d` | Mark a dataset for deletion in DSLIST |
| `tso submit 'dataset(member)'` | Submit JCL from the option line |

## Files
| Dataset | Description |
|---|---|
| `Z76689.JCL.NEW` | Newly allocated PDS, populated with members copied from INPUT |
| `ZXP.PUBLIC.JCL` | Source dataset used for reference and member viewing |

## Completion
Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKTSO3)`