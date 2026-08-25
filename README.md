# ScramDB Releases

Binary releases of [ScramDB](https://scramdb.com), the programmable
distributed hyperscale UTAP SQL database.

## Install

```sh
curl -fsSL https://scramdb.com/install | bash
```

The installer detects your OS, architecture, CPU features and glibc, verifies
every download against `SHA256SUMS`, and never touches an existing data
directory or config. Useful options:

```sh
curl -fsSL https://scramdb.com/install | bash -s -- --pick              # choose a build or version
curl -fsSL https://scramdb.com/install | bash -s -- --version 1.0.0     # a specific version
curl -fsSL https://scramdb.com/install | bash -s -- --help              # everything else
```

Uninstall (removes the binary, packages, config and the data directory):

```sh
curl -fsSL https://scramdb.com/install | bash -s -- --uninstall
```

## Platforms

- Linux x86-64: needs AVX2 (x86-64-v3, Intel Haswell 2013 / AMD Zen 1 2017 or
  newer) and glibc 2.36+.
- Linux arm64: Neoverse-N1 baseline (AWS Graviton2 or newer and comparable).
- macOS: no native build yet; use the container image:

```sh
docker run -p 5432:5432 -p 9090:9090 -p 9191:9191 -v scramdb-data:/var/lib/scramdb scramdb/scramdb:latest
```

## What is here

- `sha-<short>` prereleases: automated builds of the current development line,
  published continuously. A plain install gets the newest one.
- `v<X.Y.Z>` releases: promoted stable versions.
- `versions.json` on this branch: the index the installer reads.

Each tarball unpacks to `scramdb/` with the server binary (`bin/scramdb`), the
default single-node config and the cluster config template (`etc/`), and the
curated UDF package set (`share/dist/`).

Docs: https://scramdb.com/docs/getting-started
