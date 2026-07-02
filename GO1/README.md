# GO1 - Get Going on z/OS
IBM Z Xplore | Extended

## Overview
Introduction to Go (Golang) on z/OS using USS and VS Code. The challenge
covers the basics of Go syntax, packages, compiling and running programs
via the command line, and modifying existing code to produce specific
output. All hands-on work is done through SSH into the z/OS USS environment
with files managed via the Zowe Explorer extension.

## What I practiced

- **Go basics** — understanding package structure (`package main`), the
  `import` statement, the `main()` function as the entry point, and the
  difference between `var` declarations and `:=` short assignments
- **Handling EBCDIC encoding** — opening USS `.go` files via Zowe Explorer
  with "Open with Encoding → Binary" to make EBCDIC-encoded files readable
  in VS Code
- **Copying files in USS** — using `cp /z/public/*.go .` to copy all
  three Go source files from the public directory into a new `~/go`
  directory
- **go build** — compiling a `.go` file into a persistent binary executable
  (`go build code1.go` → `./code1`) for long-term reuse
- **Formatting output** — adding `\n` newline characters inside `fmt.Printf`
  statements to produce cleaner, more readable terminal output
- **go run** — compiling and executing a Go file in one step without
  keeping the binary (`go run code3.go`), useful for quick testing
- **Reading and modifying Go logic** — understanding `strings.Contains`,
  boolean values, and `if/else if/else` control flow in `code3.go`;
  making two targeted changes to produce the expected `false` / "Not found"
  output:
  - Changed the input string from `"seafood"` to one that does not contain
    `"foo"` so `strings.Contains` returns `false`
  - Fixed the `else if check` branch to `else if !check` so the "Not found"
    path is reachable

## Commands used

| Command | Description |
|---|---|
| `mkdir go` | Create a new directory called go in home |
| `cd go` | Navigate into the go directory |
| `cp /z/public/*.go .` | Copy all .go files from /z/public into current directory |
| `go version` | Check the installed Go version |
| `go build code1.go` | Compile code1.go into a binary executable |
| `./code1` | Run the compiled code1 executable |
| `go build code2.go` | Compile code2.go into a binary executable |
| `./code2` | Run the compiled code2 executable |
| `go run code3.go` | Compile and run code3.go in one step (no binary kept) |

## Files

| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ GO1 — code1 and code2 built and executed, code3 modified and run with correct output, CHKGO1 submitted with success