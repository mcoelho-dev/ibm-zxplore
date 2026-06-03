# PDS1 - Files for Miles
IBM Z Xplore | Advanced

## Overview
Challenge focused on working with Partitioned Data Sets (PDS) and members
on z/OS using the Zowe Explorer extension in VS Code.

## What I practiced
- **HLQ filter** — configuring the Data Sets view to show only datasets
  matching a specific High Level Qualifier
- **Favorites** — marking frequently used datasets for quick access
- **Dataset attributes** — inspecting volume, recfm, lrecl, dsorg and
  other metadata via right-click
- **Member operations** — copying and pasting members across datasets
- **JCL job submission** — submitting a job via Zowe Explorer and
  observing output members created in a PDS
- **Renaming members** — renaming job output to meet validation requirements
- **PDS vs sequential vs VSAM** — understanding the structural differences
  between dataset types on z/OS

## Files
| File | Description |
|------|-------------|
| PDS1CCAT.jcl | JCL job that concatenates PDSPART1 and PDSPART2 into a new member |

## Steps completed
1. Set HLQ filter to my Z-userid in Zowe Explorer
2. Marked SOURCE, INPUT, and OUTPUT as favorites
3. Switched HLQ to `ZXP.PUBLIC.*` and located the dataset on volume VPWRKD
4. Copied `PDSPART1` and `PDSPART2` from `ZXP.PUBLIC.INPUT` into SOURCE
5. Copied `PDS1CCAT` from `ZXP.PUBLIC.JCL` into my JCL dataset
6. Submitted `PDS1CCAT`, which generated member `PDS1OUT` inside SOURCE
7. Renamed `PDS1OUT` to `RECIPE`

## Completion
Submitted CHKAPDS1 verification job from ZXP.PUBLIC.JCL successfully — CC 0000.