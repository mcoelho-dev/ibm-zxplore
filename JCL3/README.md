# JCL3 - Explore and Edit JCL, Check it in SDSF
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering JCL debugging using TSO/ISPF and SDSF. Covers
submitting a JCL job with intentional errors, identifying the errors through
the joblog, editing the JCL to fix them, and resubmitting until the job runs
successfully. The job processes USA Women's Soccer League data using a REXX
exec.

## What I practiced
- **Dataset setup** — submitting `ZXP.PUBLIC.JCL(chalcopy)` to populate
  required datasets and members under my userid
- **Browsing data members** — navigating `ZXP.PUBLIC.DATA` and using `b` to
  browse members (TEAM, CITY, STATE, STADIUM, CAPACITY, COACH)
- **Running a REXX exec** — executing `WSL$` in `ZXP.PUBLIC.EXEC` with `ex`
  to understand the expected output before submitting the JCL
- **Submitting JCL from ISPF** — opening `WSLJCL` in the ISPF editor and
  submitting with `submit` on the command line
- **SDSF job monitoring** — using `=sd;st` and `=sd;o` to navigate to SDSF
  and check job status, using `owner` and `prefix` filters
- **JCL debugging** — identifying a DD name error (`TAAM` instead of `TEAM`)
  and a member name case error (`team` instead of `TEAM`)
- **Editing JCL** — fixing errors in VSCode via Zowe Explorer and resubmitting
- **Job validation** — confirming successful output matches the `WSL$` exec
  result, with `SYSTSPRT` present in the joblog

## Commands used
| Command | Description |
|---|---|
| `tso submit 'dataset(member)'` | Submit JCL from ISPF option line |
| `submit` | Submit JCL from within the ISPF editor |
| `=sd;st` | Jump directly to SDSF Status view |
| `=sd;o` | Jump directly to SDSF Output Queue |
| `owner Z76689;prefix Z*;st` | Filter SDSF to show only your jobs |
| `?` | View joblog files for a job in SDSF |
| `s` | Select a joblog file or view full log |
| `e` | Edit a member in ISPF |
| `b` | Browse a member in ISPF |
| `ex` | Execute a REXX exec in ISPF |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKJCL3)`