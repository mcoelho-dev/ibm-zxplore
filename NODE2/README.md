# NODE2 - Using Node.js and ZOAU to Access z/OS Data
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering the evolution of a basic Node.js HTTP server into
a mini RESTful framework with URL pattern matching and ZOAU integration.
Covers building custom request routing using regular expressions, and using
the zoau Node.js module to read z/OS dataset members and return their
content directly to a web client, including graceful error handling.

## What I practiced
- **Copying and extending a base program** — duplicating `program1.js` into
  `program2.js` as the starting point for the new functionality
- **Configurable port via environment variable** — changing the hardcoded
  port to `process.env.PORT || 0`, allowing the listening port to be set at
  runtime with `PORT=<value> node program2.js`
- **Refactoring response logic** — extracting repeated response code into a
  reusable `sendResponse(res, content, code, type)` function
- **URL pattern matching with regex** — using regular expressions
  (`/^\/$/`, `/^\/hello\//`, `/^\/data\/.*/`) and `.test()` to recognize and
  route different request URLs
- **Avoiding premature server shutdown** — relocating `server.close()`
  inside each matching route block to prevent the server from closing on
  unrelated requests like `/favicon.ico`
- **Extracting URL parameters** — using `.replace()` with regex capture
  groups to pull dynamic values (name, dataset member) out of the request URL
- **Building a RESTful service with ZOAU** — importing the `zoau` Node.js
  module and using `datasets.read()` to asynchronously retrieve the contents
  of a z/OS dataset member and return it to the browser
- **Asynchronous handling with promises** — using `.then()` to process the
  dataset content once the read operation completes
- **Graceful error handling** — adding a `.catch()` to the `datasets.read()`
  call to return a 404 response when a requested dataset member doesn't exist,
  instead of crashing the server

## Commands used
| Command | Description |
|---|---|
| `ssh Z76689@204.90.115.200` | Connect to IBM Z Xplore via SSH |
| `cd node` | Navigate to the node directory in USS |
| `PORT=6689 /usr/lpp/IBM/cnj/v20r0/IBM/node-latest-os390-s390x/bin/node program2.js` | Run the server with a custom port via environment variable |

## Files
| File | Description |
|---|---|
| `program2.js` | RESTful Node.js server with ZOAU dataset integration |
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKNODE2)`