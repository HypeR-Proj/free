<!--
SPDX-FileCopyrightText: 2026 roolrz
SPDX-License-Identifier: Apache-2.0
-->

# free

Capability-scoped physical-memory summary.

Reads the Native memory inspector through `hyper-os` and formats totals, ownership
classes and reclaimability estimates. Argument and quantity parsing use the shared tool-
argument support.

See the [implementation entry](src/main.rs) and [component declaration](component.json)
for the public interfaces, build dependencies and delivered artifacts.

## Usage

In a Native session with the required capabilities:

```sh
free
free --help
```

## Boundaries

Unavailable estimates are displayed as unavailable. Diagnostic reads do not force
reclamation, and logical ramfs capacity is not additional physical memory.

## Build and test

Use this checkout inside the [repo-managed workspace](https://github.com/HypeR-Proj/HypeR).
From this repository directory:

```sh
make
make test
```

An absolute `OUT=/path/to/out` selects a shared output directory. The module
entry delegates to build/system, which prepares the installed SDK and declared
dependencies. Native binaries require HypeR; host module checks cover the tests
selected by component.json. A standalone clone does not contain the workspace’s
other source repositories or Native SDK.
