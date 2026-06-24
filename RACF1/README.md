# RACF1 - zOS Security with RACF
IBM Z Xplore | Extended

## Overview
Hands-on challenge introducing RACF (Resource Access Control Facility), the
external security manager (ESM) that protects z/OS resources. Covers core
RACF terminology (subjects vs. objects, resource profiles, user profiles),
and practices creating, listing, altering, deleting, and permitting access
to dataset profiles using the ISPF Command Shell.

## What I practiced
- **Subjects vs. objects** — understanding that subjects (users, software)
  access objects (datasets, resources), and that this relationship is
  fluid depending on context (e.g. TSO as both subject and object)
- **RACF terminology** — resource classes, resource profiles, group
  profiles, user profiles, and system options
- **Listing dataset permissions** — using `LISTDSD` (`LD`) with wildcards
  (`'Z76689.**'`) to view Owner, Universal Access, and personal access
  levels across all owned datasets
- **Creating a generic dataset profile** — using `ADDSD` with `GENERIC`
  and `UACC(READ)` to pre-define permissions for a dataset that doesn't
  exist yet (`Z76689.SECRET`)
- **Comparing permission vs. restriction** — listing pre-existing datasets
  (`ZXP.PUBLIC.RACF.OPEN` and `ZXP.PUBLIC.RACF.CLOSED`) to observe how
  Universal Access affects read visibility
- **Altering a dataset profile** — using `ALTDSD` with `GENERIC` to change
  `UACC` from `READ` to `UPDATE` on an existing profile, and learning the
  distinction between `ADDSD` (create) and `ALTDSD` (modify) when a
  profile already exists
- **Deleting a dataset profile** — using `DELDSD` with `GENERIC` (without
  `UACC`) to remove a profile, and confirming removal via `LISTDSD`
- **Allocating a real sequential dataset** — using `ALLOC` with
  `DSORG(PS)`, `RECFM(F,B)`, `LRECL(80)`, and `SPACE(5,5) TRACKS` to
  create `Z76689.MAGIC`, since the profile would target a real dataset
  (no `GENERIC` needed)
- **Creating a discrete dataset profile** — using `ADDSD` with
  `UACC(NONE)` to lock down the new dataset by default
- **Granting individual access with PERMIT** — using `PERMIT` with
  `ID(IBM0001)` and `ACCESS(UPDATE)` to grant a specific user write
  access, distinguishing `PERMIT`'s `ID`/`ACCESS` operands from `ADDSD`'s
  `UACC` operand
- **Submitting and validating JCL** — using `S` to select a member in
  `ZXP.PUBLIC.JCL`, `SUBMIT` to run `CHKRACF1`, and confirming success via
  SDSF

## Commands used
| Command | Description |
|---|---|
| `ld da('Z76689.**')` | List dataset permissions for all owned datasets |
| `addsd 'Z76689.secret' generic uacc(read)` | Create a generic profile with read access |
| `ld da('Z76689.secret') all` | List full details of a specific dataset profile |
| `altdsd 'Z76689.secret' generic uacc(update)` | Alter UACC from read to update |
| `deldsd 'Z76689.secret' generic` | Delete a generic dataset profile |
| `alloc dsn('Z76689.MAGIC') new space(5,5) tracks lrecl(80) recfm(f,b) dsorg(ps)` | Allocate a real sequential dataset |
| `addsd 'Z76689.magic' uacc(none)` | Create a discrete profile with no universal access |
| `permit 'Z76689.magic' id(ibm0001) access(update)` | Grant a specific user update access |
| `SUBMIT` | Submit a JCL job from the editor |

## Files
| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKRACF1)`