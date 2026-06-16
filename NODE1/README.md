# NODE1 - Node.js Web Server on z/OS
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering the creation and execution of a Node.js web server
running directly in the z/OS USS environment. Covers creating a USS directory
and JavaScript file, copying example source code from a z/OS dataset, running
the server via SSH, and validating it with a JCL job.

## What I practiced
- **USS directory setup** — creating a `node` directory under `/z/Z76689/`
  using the Zowe Explorer USS panel in VS Code
- **Creating a USS file** — creating `program1.js` inside the node directory
  via right-click in the Zowe Explorer
- **Copying source code** — opening `ZXP.PUBLIC.SOURCE(NODE1)` in VS Code
  and pasting the Node.js web server code into `program1.js`
- **Editing the program** — updating line 15 to use `server.address().port`
  instead of `${port}` to display the actual assigned port at runtime
- **SSH connection** — connecting to the IBM Z Xplore system via SSH in the
  VS Code terminal using `ssh Z76689@204.90.115.200`
- **Running Node.js on z/OS** — executing the server using the full path to
  the node binary since it was not on the default PATH
- **Port identification** — noting the dynamically assigned TCP port from the
  server startup message
- **Job submission** — submitting `CHKNODE1` from `ZXP.PUBLIC.JCL` with the
  server running (without opening the browser first, since `server.close()`
  causes the server to shut down after the first request)

## Commands used
| Command | Description |
|---|---|
| `ssh Z76689@204.90.115.200` | Connect to IBM Z Xplore via SSH |
| `cd node` | Navigate to the node directory in USS |
| `/usr/lpp/IBM/cnj/v20r0/IBM/node-latest-os390-s390x/bin/node program1.js` | Run the Node.js server using full binary path |
| `ps -ef \| grep node` | Check for running node processes |

## Files
| File | Description |
|---|---|
| `program1.js` | Node.js web server program |
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKNODE1)`