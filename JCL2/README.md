# JCL2 - ON the Job
IBM Z Xplore | Advanced

## Overview
Debugging challenge focused on fixing broken JCL. Starting from a job that combines data from multiple source files, the goal was to interpret job output, diagnose the missing piece, and correct the JCL so the job completes successfully.

## What I practiced
- **Copying JCL members** — using Zowe Explorer's "Copy Member" / "Paste Member" to bring `JES2JOB1` from `ZXP.PUBLIC.JCL` into my own `Z76689.JCL` dataset for editing
- **Reading DD statements** — understanding that `DD` (Data Definition) statements tell a program which datasets to use and how (`DISP=SHR`, member references, etc.)
- **Submitting jobs and reading condition codes** — using "Submit Job" and interpreting `CC 0008` as a definite error
- **Diagnosing failures via job output** — reviewing `JESMSGLG`, `JESJCL`, and `JESYSMSG` to find the root cause
- **Interpreting IRX error messages** — reading `IRX0555E The input or output file ARTIST is not allocated` and `IRX0670E EXECIO error` to identify a missing input file
- **Fixing JCL by pattern-matching an existing DD** — using the `BRAND` DD statement as a template to build the missing `ARTIST` DD statement, keeping proper spacing/alignment
- **Save-before-submit discipline** — confirming that unsaved changes cause the job to run the old version again
- **Validating the fix** — checking `OUTPUT(GUITAR)` for correct report content and re-submitting until reaching `CC 0000`
- **Running an IBM validation job** — submitting `CHKJCL2` from `ZXP.PUBLIC.JCL` to confirm the fix was accepted

## The Problem
The job `JES2JOB1` runs the `IRXJCL` REXX program with a `COMBINE` parameter, pulling data from `NICKNAME` and `BRAND` input files to build a report in `OUTPUT(GUITAR)`. The job failed with `CC 0008`. JESYSMSG showed: "IRX0555E The input or output file ARTIST is not allocated. It cannot be opened for I/O.
IRX0670E EXECIO error while trying to GET or PUT a record."

A third DD statement, `ARTIST`, was missing.

## The Fix
```jcl
//ARTIST    DD DSN=ZXP.PUBLIC.SOURCE(ARTIST),DISP=SHR
```
Added after the `BRAND` DD statement, pointing to the `ARTIST` member in `ZXP.PUBLIC.SOURCE`.

## Commands used
| Command | Description |
|---|---|
| Copy Member / Paste Member | Copy `JES2JOB1` from `ZXP.PUBLIC.JCL` into own JCL dataset |
| Submit Job | Run the JCL and generate output |
| `F 'IRX0555E'` (SDSF/JESYSMSG) | Locate the specific error message identifying the missing file |

## Files
| File | Description |
|---|---|
| `JES2JOB1` | Corrected JCL member with added `ARTIST` DD statement |
| `README.md` | Challenge notes and documentation |

## Completion
✅ Job resubmitted after fix — CC 0000
✅ `OUTPUT(GUITAR)` produced correct Item/Brand/Artist report
✅ CHKJCL2 validation job submitted with success