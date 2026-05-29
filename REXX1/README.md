# REXX1 - Enterprise IT Duct Tape

IBM Z Xplore | Fundamentals

## Overview

Introduction to REXX (Restructured Extended Executor), a scripting language native to the mainframe. This challenge covers running REXX programs on z/OS via TSO using the Zowe CLI.

## What I practiced

- **REXX** — reading and running REXX programs on z/OS
- **TSO Address Spaces** — creating persistent mainframe sessions to run interactive programs
- **Zowe CLI** — interacting with the mainframe from a local command line
- **z/OSMF** — the z/OS management service used by Zowe under the hood
- **Dataset management** — copying members between datasets using Zowe Explorer

## Programs

| Member | Description |
|--------|-------------|
| SOMEREXX | Displays a greeting message on the mainframe |
| GUESSNUM | Interactive number guessing game (1-10) running in a TSO address space |

## Key commands used

```bash
zowe tso issue command "exec 'Z76689.SOURCE(somerexx)'" --ssm
zowe tso start as
zowe tso send as {as-key} --data "exec 'Z76689.SOURCE(guessnum)'"
zowe tso send as {as-key} --data "5"
```

## Completion

Submitted CHKREXX1 verification job from ZXP.PUBLIC.JCL successfully.