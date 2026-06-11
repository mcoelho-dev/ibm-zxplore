# TSISPF1O2 - Navigate TSO and ISPF
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering the TSO logon procedure and initial ISPF
navigation using a 3270 terminal emulator. Covers logging in, configuring
ISPF defaults, submitting jobs via the TSO command line, and properly
logging off the system.

## What I practiced
- **TSO logon** — connecting to z/OS via 3270 emulator and authenticating
  with the `logon userid` command
- **ISPF navigation** — using the Primary Option Menu, navigating submenus
  and understanding the panel-driven interface
- **ISPF defaults** — configuring Log Data Set settings via the Log/List menu
- **Job submission via TSO** — submitting JCL jobs directly from the ISPF
  option line using `tso submit 'dataset(member)'`
- **TSO logoff** — properly ending a TSO session with the `logoff` command
- **Common ISPF keys** — F1 Help, F3 Exit, F4 Return to menu, F7/F8 Page
  Up/Down, Ctrl (left) to reset locked keyboard

## Commands used
logon Z76689
tso submit 'ZXP.PUBLIC.JCL(CHKTSO2)'
logoff

## Completion
Submitted CHKTSO2 verification job via TSO command line on ISPF successfully.