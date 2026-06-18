# PLI1 - Introduction to Building and Running PL/I Programs
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering the compilation and execution of a PL/I program
on z/OS using JCL. Covers reading PL/I source code structure, understanding
a multi-step JCL job (compile, bind, execute), diagnosing a dataset
allocation error from the joblog, and manually allocating an output dataset
with attributes matching the program's file declaration.

## What I practiced
- **Reading PL/I source code** — reviewing `ZXP.PUBLIC.SOURCE(PLICNT)`,
  identifying the PROC OPTIONS(MAIN) entry point, variable and file
  declarations (`PRTLINE`, `PRTDONE`, `SYSPRINT`), a counting loop from 1 to
  1,000,000, and output file writes
- **Understanding multi-step PL/I JCL** — reviewing the compile (PLI), bind
  (IEWBLINK), and execute steps in `ZXP.PUBLIC.JCL(PLICNT)`, including
  STEPLIB/SYSLIN/SYSLMOD allocations and conditional step execution (`IF RC 
  8`, `IF RC < 5`)
- **Diagnosing a JCL error** — submitting the unmodified JCL, identifying the
  failure in JESYSMSG (`IEFA107I ... DATA SET Z76689.PLICNT.PRTLINE NOT
  FOUND`), and recognizing that `PRTLINE DD DSN=&SYSUID..PLICNT.PRTLINE,
  DISP=OLD` requires the dataset to be pre-allocated
- **Matching dataset attributes to program requirements** — reading the
  PL/I file declaration `DCL PRTLINE FILE RECORD OUTPUT ENV(FB,RECSIZE(7))`
  to determine the required RECFM (FB) and LRECL (7) for the output dataset
- **Manual dataset allocation via ISPF** — using ISPF option 3.2 (Data Set
  Utility) to allocate `Z76689.PLICNT.PRTLINE` with RECFM=FB, LRECL=7,
  BLKSIZE=700, after running into SMS/storage class errors when attempting
  allocation through the Zowe Explorer in VS Code
- **Job resubmission and validation** — resubmitting PLICNT after dataset
  allocation to confirm successful completion (RC 0000) across all three
  steps (PLI, BIND, EXECUTE)

## Commands used
| Command | Description |
|---|---|
| ISPF 3.2 → Option A | Allocate a new dataset via Data Set Utility |
| `submit` | Submit JCL from ISPF or via Zowe Explorer |

## Files
| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKPLI1)`