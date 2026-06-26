# RACF1 & RACF2 - zOS Security with RACF
IBM Z Xplore | Extended

## Overview
Two-part introduction to RACF (Resource Access Control Facility), the
external security manager (ESM) protecting z/OS resources. RACF1 covers
core terminology — subjects, objects, profiles, and access permissions —
through hands-on dataset profile commands. RACF2 builds on this with a
scavenger-hunt scenario (Mr. Peabody & Sherman) involving real access
denial troubleshooting, Db2/SPUFI, RACF groups, and a multiple-choice quiz.

## What I practiced
### RACF1
- **Subjects vs. objects** — understanding that subjects (users, software)
  request access, while objects (datasets, profiles) are protected
- **Listing dataset permissions** — using `LISTDSD` (`LD`) to view UACC,
  owner, and personal access for datasets, including generic listings with
  wildcards (`**`)
- **Adding dataset profiles** — using `ADDSD` with `GENERIC` and `UACC`
  to create permissions for a dataset that doesn't exist yet
- **Altering and deleting profiles** — using `ALTDSD` to change UACC from
  `READ` to `UPDATE`, and `DELDSD` to remove a profile entirely
- **Permission vs. restriction in practice** — comparing access to
  `ZXP.PUBLIC.RACF.OPEN` (UACC READ) vs. `ZXP.PUBLIC.RACF.CLOSED` (UACC NONE)
- **Granting access to another user** — using `PERMIT` to give `IBM0001`
  UPDATE access to a newly created sequential dataset

### RACF2
- **Diagnosing access failures in SDSF SYSLOG** — using `BOTTOM` and
  `FIND 'ICH408I' PREV` (repeated with `F5`/RFIND) to locate the exact
  RACF violation message tied to my userid, and reading `ACCESS
  INTENT`/`ACCESS ALLOWED` to understand why access was denied
  (UACC NONE on a generic `TECHTEAM.**` profile)
- **Using Db2/SPUFI through ISPF** — confirming the `DBDG` subsystem ID,
  running SPUFI with `JCL(SQL)` as input and `DB2OUT` as output
- **Writing and running SQL via SPUFI** — `SET CURRENT SCHEMA` and a
  `SELECT *` query against a TECHTEAM table to retrieve dynamic
  instructions for the rest of the challenge
- **Group-based access via TSO command** — running the `TECHTEAM` exec,
  correctly answering a question about the ACCESS ALLOWED value from the
  ICH408I message, to get connected to `GROUP(TECHTEAM)`
- **Verifying group connection** — using `LISTUSER` (`LU`) to confirm
  `GROUP=TECHTEAM` appeared in my connect list
- **Refreshing session permissions** — logging off and back on for the new
  group connection to take effect before re-attempting dataset access
- **Completing a knowledge check** — running the `RACFQUIZ` TSO command
  and answering multiple-choice questions distinguishing subjects, objects,
  and groups

## Commands used
| Command | Description |
|---|---|
| `LD DA('Z76689.**')` | List dataset permissions under own ID |
| `ADDSD 'Z76689.secret' GENERIC UACC(READ)` | Create a dataset profile with read access |
| `ALTDSD 'Z76689.secret' UACC(UPDATE)` | Change UACC from read to update |
| `DELDSD 'Z76689.secret'` | Delete a dataset profile |
| `PERMIT 'Z76689.magic' ID(IBM0001) ACCESS(UPDATE)` | Grant update access to another user |
| `F 'ICH408I' PREV` | Find RACF violation messages in SDSF SYSLOG, searching backward |
| `TSO TECHTEAM` | Run exec to answer access question and join GROUP(TECHTEAM) |
| `LU Z76689` | Confirm group connections |
| `TSO RACFQUIZ` | Run the RACF2 knowledge-check quiz |

## Files
| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ RACF1 — ADDSD/ALTDSD/DELDSD/PERMIT exercises completed
✅ RACF2 — Scavenger hunt completed, RACFQUIZ passed, CHKRACF2 submitted with success
