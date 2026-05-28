# DuckDB Snap Package (Prototype)

This directory contains a [Snapcraft](https://snapcraft.io/) configuration to
package DuckDB as a Canonical snap.

> **⚠️ Prototype / Dev Branch**
> This snap uses `grade: devel`, which means it can only be released to the
> `edge` channel on the Snap Store. It signals that this package is experimental
> and not yet ready for stable use.

## Prerequisites

- Ubuntu 22.04+ (or any Linux distro with snapd)
- [Snapcraft](https://snapcraft.io/docs/snapcraft-overview) installed:

```bash
sudo snap install snapcraft --classic
```

## Building the Snap

From the repository root:

```bash
snapcraft
```

This will produce a `.snap` file (e.g., `duckdb_<version>_amd64.snap`).

## Installing Locally

Install the built snap in dev mode (required for `grade: devel` snaps that
aren't published to the store):

```bash
sudo snap install duckdb_*.snap --devmode
```

## Running

Once installed, run DuckDB from the command line:

```bash
duckdb
```

Or open a specific database file:

```bash
duckdb my_database.db
```

## Publishing to the Snap Store (Edge Channel)

Since `grade: devel` is set, this snap can only be published to the `edge`
channel:

```bash
snapcraft login
snapcraft upload duckdb_*.snap --release=latest/edge
```

Users can then install the edge version with:

```bash
sudo snap install duckdb --edge
```

## About the Dev Branch / Grade

The `grade: devel` field in `snap/snapcraft.yaml` marks this snap as a
development/prototype build:

- It **cannot** be released to the `stable` or `candidate` channels
- It is intended for early testing and feedback
- Once the snap is mature, change `grade` to `stable` to enable releases to
  all channels

## Confinement

This snap uses `strict` confinement with the following interface plugs:

| Plug             | Purpose                                      |
|------------------|----------------------------------------------|
| `home`           | Access files in the user's home directory    |
| `network`        | Allow network access (e.g., extension downloads) |
| `removable-media`| Access mounted USB drives and external storage |

## Further Reading

- [Snapcraft Documentation](https://snapcraft.io/docs)
- [DuckDB Documentation](https://duckdb.org/docs/)
- [Snap Store](https://snapcraft.io/store)
