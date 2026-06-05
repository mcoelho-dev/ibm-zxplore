# USS2 - It's Unix. I Know This!
IBM Z Xplore | Advanced

## Overview
Shell scripting and file permissions on z/OS Unix System Services (USS).
The challenge involves reading and fixing a shell script, setting up its
required input files, and making it run correctly via the USS terminal.

## What I practiced
- **USS navigation** — `mkdir`, `touch`, `cd`, `ls`, `pwd`, `cat` refresher
- **File permissions** — reading permission strings (`rwx`) and using
  `chmod +x` to make a script executable
- **Shell script reading** — understanding `IF` conditions, `FOR` loops,
  variable substitution and `echo` redirects in a `.sh` script
- **Script execution** — running scripts with `./script.sh` and passing
  positional parameters (`$1`)
- **VSCode + Zowe** — editing USS files directly through the VSCode
  integrated editor

## Commands used
```bash
# Create input files and output directory
touch animal1 animal2 animal3
mkdir uss2output

# Check file contents
cat animal[123] | wc -l

# Grant execute permission
chmod +x animals.sh

# Run the script with a parameter
./animals.sh Sunny

# Verify output
cat uss2output/message
```

## Files
| File | Description |
|------|-------------|
| animals.sh | Shell script provided by IBM Z Xplore (not authored by me) |

## Completion
Submitted CHKUSS2 verification job via Zowe Explorer in VSCode successfully.