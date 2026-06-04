# PDS2 - Thankx for the Memberies
IBM Z Xplore | Advanced

## Overview
Advanced challenge focused on filtering, editing, and managing Partitioned
Data Set (PDS) members on z/OS, including uploading local files, running a
sort/merge JCL job, and allocating a custom dataset via Zowe Explorer.

## What I practiced
- **Uploading members** — uploading local `.txt` files directly into a PDS
  via Zowe Explorer's "Upload Member" option
- **JCL Symbolics** — understanding how `&SYSUID.` is substituted at
  runtime by JES, allowing shared JCL scripts to work across different users
- **SORT utility** — using the IBM SORT program via JCL to merge and sort
  multiple input members into a single output member
- **Dataset allocation** — creating a new PDS from scratch in Zowe Explorer,
  including setting allocation unit from CYL to TRK to avoid REST API errors
- **Member operations** — renaming output members and deleting temporary
  datasets after use
- **Dataset attributes** — understanding qualifiers, HLQ naming rules, and
  the 8-character limit per qualifier

## Files
| File | Description |
|------|-------------|
| MERGSORT.jcl | JCL job that merges ROCKS1, ROCKS2 and ROCKS3 members and sorts the output alphabetically |

## Completion
Submitted CHKAPDS2 verification job from ZXP.PUBLIC.JCL successfully.