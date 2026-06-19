# PYTHON1 - More Python on z/OS
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering Python scripting on z/OS using the zoautil_py
module to interact with MVS datasets. Covers creating a sequential dataset,
writing and reading data from it, and retrieving the executing user's ID,
all from a Python script run via SSH on the IBM Z Xplore system.

## What I practiced
- **Copying starter code** — copying the base script from
  `ZXP.PUBLIC.SOURCE(PYTHON1)`, which imports `zoautil_py` (mvscmd, datasets,
  jobs) and the standard `os` module
- **Creating a USS Python file** — creating `program1.py` inside a `python`
  directory in USS via the Zowe Explorer
- **Setting the HLQ** — defining a `HLQ` variable with my own userid to
  ensure all dataset operations target my own MVS namespace
- **Creating a sequential dataset** — using `datasets.create()` to allocate
  `<HLQ>.PYTHON.DATA` with `dataset_type="seq"`, `record_length=80`,
  `record_format="FB"`, and `primary_space="100k"`
- **Writing to a dataset** — using `datasets.write()` to insert text content
  into the newly created dataset
- **Reading from a dataset** — using `datasets.read()` to retrieve and print
  the dataset's contents back to the terminal
- **Reading environment variables** — using `os.environ.get("USER")` to
  retrieve the executing userid and include it in the program's output
- **Running Python on z/OS via SSH** — connecting via
  `ssh Z76689@204.90.115.200`, navigating to the script directory, and
  executing with `python3 program1.py`

## Commands used
| Command | Description |
|---|---|
| `ssh Z76689@204.90.115.200` | Connect to IBM Z Xplore via SSH |
| `cd python` | Navigate to the script directory in USS |
| `python3 program1.py` | Run the Python script |

## Files
| File | Description |
|---|---|
| `program1.py` | Python script using zoautil_py to create, write, and read an MVS dataset |
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKPYTH1)`