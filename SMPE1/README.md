# SMPE1 - z/OS System Modification
IBM Z Xplore | Extended

## Overview
Hands-on introduction to SMP/E (System Modification Program Extended), the
base service z/OS uses to install and manage software products and fixes.
Covers the structure of a Consolidated Software Inventory (CSI) — Global,
Target, and Distribution zones — and the hands-on creation of a sample CSI
and its associated SMP/E operational datasets using JCL and IDCAMS.

## What I practiced
- **Copying starter JCL** — copying the sample job from
  `ZXP.PUBLIC.JCL(GIMSAMPU)` into my own library member
  `Z76689.JCL(GIMSAMPU)` using ISPF 3.3 (Move/Copy)
- **Editing JCL with global CHANGE commands** — using the ISPF editor's
  `CHANGE` command to update `&HLQ&`, `&VOLUME&`, and `&UNIT&` placeholders
  throughout the job
- **Allocating VSAM clusters via IDCAMS** — understanding `DEFINE CLUSTER`
  statements that build the Global, Target, and Dlib CSI clusters, each with
  DATA and INDEX components
- **Adjusting space allocations** — converting `CYLINDERS` to `TRACKS` in
  the `DEFZONES` step (2 primary, 1 secondary) and to `TRK` in the
  `ALLOCDS` step (1 primary, 1 secondary; PDS directory space set to 1) to
  keep the sample CSI small given shared system resources
- **Understanding zone structure** — learning the distinction between the
  Global Zone (single index of all SYSMODs and zones), Target Zone (target
  library content/status), and Distribution Zone (DLIB content/status)
- **Verifying job output in SDSF** — checking `MAXCC=0000` to confirm all
  three steps (`DEFZONES`, `ALLOCDS`, `UPDZONES`) completed successfully
- **Locating created datasets** — using ISPF 3.4 (Dslist) to confirm all 19
  cluster and operational datasets under `Z76689.SMP` were created, and
  understanding why `*.CSI` entries show `*VSAM*` instead of a volume
  (catalog entry vs. the underlying DATA/INDEX components)

## Commands used
| Command | Description |
|---|---|
| `CHANGE &HLQ& 'Z76689.SMP' ALL` | Replace the HLQ placeholder throughout the JCL |
| `CHANGE &VOLUME& VPWRKA ALL` | Replace the volume placeholder |
| `CHANGE &UNIT& 3390 ALL` | Replace the unit placeholder |
| `FIND CYL` | Verify no leftover CYL/CYLINDERS allocations remain |
| `SUBMIT` | Submit the GIMSAMPU job |

## Files
| File | Description |
|---|---|
| `GIMSAMPU.jcl` | Edited JCL to allocate and prime the SMP/E CSI and operational datasets |
| `README.md` | Challenge notes and documentation |

## Completion
✅ GIMSAMPU job completed with MAXCC=0000
✅ CHKSMP1 validation job completed