# zVM0 - Introducing the original virtualisation system - z/VM
IBM Z Xplore | Extended

## Overview
Conceptual challenge covering the fundamentals of z/VM, IBM's pioneering
hypervisor for IBM Z mainframes. Covers the history of virtualization on
IBM Z, core terminology (CEC, LPAR, CP, CMS), the architecture of virtual
machines, and key concepts like resource overcommitment.

## What I practiced
- **z/VM history and evolution** — from CP-40 (1964) and VM/370 (1972) to
  the modern z/VM product line
- **Z Nomenclature** — mapping mainframe terms (CEC, LPAR, DASD, IPL, CP)
  to their equivalents in distributed/x86 environments
- **Virtualization stack on IBM Z** — understanding how CEC → LPAR → z/VM
  (CP) → Virtual Machines (CMS, Linux, guest z/OS) relate to each other
- **Real, Logical, and Virtual views** — distinguishing how hardware,
  systems programmers, and application developers each perceive the same
  system differently
- **Resource overcommitment** — the concept of allocating more virtual
  resources (CPU, memory, network) than physically exist, since not every
  guest needs 100% of its resources 100% of the time
- **Guest operating systems** — identifying which OSes z/VM can and cannot
  virtualize (e.g., z/OS, Linux, z/VM itself vs. non-Z-architecture systems
  like Windows Server)
- **z/VM components and services** — CP (Control Program), CMS, user
  directory (userids/guests), and automation services like PROP

## Files
| File | Description |
|---|---|
| `README.md` | Challenge notes and documentation |

## Completion
✅ Challenge completed and validated via quiz assessment