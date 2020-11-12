---
title: nix
---

## current state

### PM's

* do in place mutations
  * cannot be undone, hard to trace
  * makes upgrades dangerous
  * installs can cause un-inteded breaks
  * rollbacks only done through snapshots
      * fragile and non-composable
  * config tends to drift
  * testing package is a nightmare because of all the possible configurations


* nix packages are determined using hashes of content and deps.
  * packages build in isolation
  * no timestamps
  * no incremental builds
  * package defs are pure functions
* no globals
  * bin is mutable
  * packages refer to deps using hashes
  * nix is used to launch package
  * user profile is env of symlinks
  * upgrades doesn't install over old packages
  * upgrades are atomic (based on hashes)
  * all applications are sandboxed

* implications
  * two versions of the same can exist
  * changes are non-destructive

* nix has garbage collection
  * when a package is no longer linked to, it is removed
