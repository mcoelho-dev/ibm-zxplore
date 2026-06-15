# DOCK1 - Docker
IBM Z Xplore | Extended

## Overview
Hands-on challenge covering the setup and use of Docker Desktop integrated
with VS Code. Covers installing the Docker and Remote Development extensions,
pulling and running an Ubuntu container image, and attaching to the running
container directly from VS Code to explore its filesystem.

## What I practiced
- **Docker Desktop setup** — installing and launching Docker Desktop on
  Windows, including resolving a WSL version issue before the engine could start
- **Docker extension** — installing the Docker extension for VS Code and
  verifying the container and image appear without warning triangles
- **Pulling and running an image** — using `docker run -it ubuntu bash` in the
  VS Code terminal to pull the Ubuntu image and start an interactive shell
  inside the running container
- **Remote Development extension** — installing the Remote Development
  extension suite and using Remote Explorer to locate the running container
- **Attaching to a container** — right-clicking the Ubuntu container in Remote
  Explorer and attaching a VS Code window directly to it
- **Navigating the container filesystem** — opening `/root/` via the Explorer
  panel inside the attached VS Code window
- **Job submission** — submitting `CHKADOCK` from `ZXP.PUBLIC.JCL` via Zowe
  Explorer to validate completion

## Commands used
| Command | Description |
|---|---|
| `wsl --update` | Update WSL to a version compatible with Docker Desktop |
| `docker run -it ubuntu bash` | Pull Ubuntu image and start an interactive container shell |

## Files
| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via `ZXP.PUBLIC.JCL(CHKADOCK)`
