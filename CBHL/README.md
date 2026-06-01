# CBLH - Here for the Long Haul

IBM Z Xplore | Advanced

## Overview

Advanced COBOL challenge focused on debugging and enhancing a real COBOL program that reads a JSON file and generates a grocery store flyer. The program outputs the flyer in both plain text and HTML format.

## What I practiced

- **COBOL debugging** — identifying and fixing syntax errors, ABENDs, and logic issues
- **JSON in COBOL** — parsing JSON input into a COBOL data structure using `JSON PARSE`
- **JCL debugging** — fixing DD name mismatches that caused ABENDU4038
- **COBOL intrinsic functions** — `INTEGER-OF-DATE`, `FORMATTED-DATE`, `TRIM`, `NATIONAL-OF`, `DISPLAY-OF`
- **COBOL PIC clauses** — using `$9.99` for currency formatting
- **HTML output from COBOL** — generating formatted HTML via JCL `PARM='HTML'`
- **Codepage conversion** — converting EBCDIC to UTF-8 for JSON parsing

## Files

| File | Description |
|------|-------------|
| CBLJSON.cbl | COBOL program that reads JSON inventory and generates a grocery store flyer |
| JSONJCL.jcl | JCL to compile and run the COBOL program |

## Bugs fixed

- Replaced `WHATGOESHERE` placeholder with `INTEGER-OF-DATE` function
- Fixed DD name mismatch (`FLYRFILE` → `FLYYFILE`) that caused ABENDU4038
- Added missing `Write flyer-file` after the store title
- Added `PARM='HTML'` to JCL to enable HTML output
- Fixed currency formatting from `9.99` to `$9.99`
- Added missing `prod-img` field to JSON data structure in COBOL
- Fixed line length exceeding column 72 limit

## Completion

Submitted CHKACBLH verification job from ZXP.PUBLIC.JCL successfully.