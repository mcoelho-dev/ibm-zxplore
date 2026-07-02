# DFSMS1 - z/OS Storage Management System
IBM Z Xplore | Extended

## Overview
Introduction to DFSMS (Data Facility Storage Management Subsystem), the z/OS
subsystem responsible for managing disk storage (DASD). The challenge covers
storage terminology, SMS-managed vs. non-SMS-managed volumes, ACS routines,
and the ISMF panel. The final task involves allocating two datasets — one
non-SMS-managed and one SMS-managed — using knowledge gathered from exploring
the live ACS routine on the IBM Z Xplore system.

## What I practiced

- **Storage terminology** — understanding DASD (Direct Access Storage Device),
  volumes, extents (primary and secondary), and space units (blocks, tracks,
  cylinders)
- **SMS vs. non-SMS allocation** — distinguishing explicit allocation (user
  controls all attributes) from implicit allocation (ACS routines override or
  assign attributes automatically)
- **Navigating ISMF** — accessing the Interactive Storage Management Facility
  through ISPF, setting User Mode to Storage Administrator (mode 2), and
  exploring the full SA menu
- **Exploring DASD volumes** — using the Volume → DASD panel with filters
  (SMS source, ZXP\* serial, Physical and Space data, all storage groups,
  ACTIVE CDS) to view volume serials, allocated space, free extents, physical
  status, and storage group assignments
- **Identifying non-SMS volumes** — switching to Physical source in the volume
  selection panel to find volumes with NONSMS physical status (ZXPTMP, ZXPO02)
- **Reading ACS routines** — opening `VENDOR.PARMLIB` through the ACS →
  Display panel and browsing the three source members (AC\$DATAC, AC\$STORC,
  AC\$STORG) to understand the FILTLIST → WHEN → SET logic
- **Connecting the SMS chain** — tracing how a dataset name triggers a
  DATACLAS (AC\$DATAC), which determines a STORCLAS (AC\$STORC), which
  determines a STORGRP and physical volume (AC\$STORG)
- **Data Class, Storage Class, Storage Groups** — listing all active objects
  in ISMF using `*` as wildcard, identifying which names correspond to the
  ACS routine entries, and using `listvol` to see which volumes belong to each
  storage group
- **Allocating a non-SMS-managed dataset** — naming the dataset with `.NONSMS.`
  in the HLQ chain so the ACS routine assigns DATACLAS=NONSMS → STORCLAS=' '
  (blank) → non-SMS, on volume ZXPTMP
- **Allocating an SMS-managed dataset** — allocating `Z76689.TOOBIG` as a
  LIBRARY with 100 tracks, observing the ACS routine override the size
  (>200KB reduced) and assign DATACLAS=ZXPDX automatically
- **Capturing ACS override messages** — noting the last three words of the
  system message and storing them in a member called MESSAGE inside the new
  dataset
- **Submitting the verification job** — finding `CHKSMS1` in `ZXP.PUBLIC.JCL`
  and submitting it to confirm both datasets were correctly created

## Commands / panels used

| Action | How |
|---|---|
| Open ISMF | ISPF Primary Menu → `IS` |
| Set Storage Administrator mode | ISMF → 0 (Profile) → User Mode → `2` |
| View SMS volumes | ISMF → 2 (Volume) → DASD → Source 2, ZXP\*, Y/Y, \*, ACTIVE |
| View all volumes incl. non-SMS | ISMF → 2 (Volume) → DASD → Source 1, ZXP\*, no SG, no CDS |
| Display ACS routine | ISMF → 7 (ACS) → 5 (Display) → CDS `'ACTIVE'` |
| Browse ACS source members | ISPF Edit → `'VENDOR.PARMLIB'` → S on AC\$DATAC / AC\$STORC / AC\$STORG |
| List Data Classes | ISMF → 4 (Data Class) → CDS ACTIVE, name `*` |
| List Storage Classes | ISMF → 5 (Storage Class) → CDS ACTIVE, name `*` |
| List Storage Groups | ISMF → 6 (Storage Group) → CDS ACTIVE, name `*` |
| View volumes per storage group | `listvol` in line operator column of storage group list |
| Allocate non-SMS dataset | ISPF 3.2 → `'Z76689.NONSMS.TEST'`, vol ZXPTMP, TRKS 5/1, FB/20, PS |
| Allocate SMS dataset | ISPF 3.2 → `'Z76689.TOOBIG'`, no vol, TRKS 100/1, FB/20, LIBRARY |
| Create MESSAGE member | ISPF 2 → `'Z76689.TOOBIG(MESSAGE)'` → type override message |
| Submit verification job | ISPF 3.4 → ZXP.PUBLIC.JCL → SUB on CHKSMS1 |

## Files

| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ DFSMS1 — ACS routine explored, non-SMS and SMS datasets allocated, MESSAGE member created, CHKSMS1 submitted with success