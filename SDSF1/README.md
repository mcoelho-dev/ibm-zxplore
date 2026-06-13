# SDSF1 - Run, Check, Print
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering the basics of SDSF (System Display and Search
Facility), a utility used to monitor active jobs, inspect joblog output, and
manage spool data. Covers navigating the SDSF panels, submitting JCL jobs
from within SDSF, viewing output queues, and saving joblog output to a
dataset member.

## What I practiced
- **SDSF navigation** — entering SDSF from the ISPF Primary Option Menu
  using `SD` and navigating between panels (ST, O)
- **Filtering views** — using `owner Z76689`, `prefix Z*` and `st` commands
  to limit the display to jobs owned by my userid
- **set display on** — enabling the active filter header to confirm prefix,
  owner and other settings
- **Job submission from SDSF** — submitting JCL via
  `tso submit 'zxp.public.jcl(CHKTSO4)'` directly from the COMMAND INPUT line
- **Output Queue** — navigating to the Output Queue with `O` to monitor
  completed jobs
- **Joblog inspection** — selecting a job with `s` to open and scroll through
  the joblog output
- **Saving output** — using `xdc` to write joblog output to a dataset member
  (`Z76689.OUTPUT(TSO4)`) with SHR disposition
- **Command chaining** — using `;` to execute multiple SDSF commands in
  sequence (e.g. `tso submit '...';st`)

## Commands used
| Command | Description |
|---|---|
| `SD` | Open SDSF from ISPF Primary Option Menu |
| `owner Z76689` | Filter display to your userid |
| `prefix Z*` | Filter to jobs starting with your Z-userid |
| `st` | Show job status based on owner and prefix |
| `set display on` | Show active filters in the panel header |
| `O` | Navigate to Output Queue |
| `s` | Select a job to view joblog |
| `xdc` | Print/save joblog output to a dataset |
| `tso submit 'dataset(member)'` | Submit JCL from SDSF command line |
| `command1;command2` | Chain multiple commands with semicolon |

## Completion
✅ Challenge completed — job `@SDSF1` submitted and validated via
`ZXP.PUBLIC.JCL(CHKTSO4)`