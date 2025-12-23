# minimal-reproduction-template (TBD)

First, read the [Renovate minimal reproduction instructions](https://github.com/renovatebot/renovate/blob/main/docs/development/minimal-reproductions.md).

Then replace the current `h1` with the Renovate Issue/Discussion number.

## Current behavior

uv version 0.9.17 adds support for relative timestamps in its `exclude-newer` option. As part of the implementation, any change to the lockfile saves the `exclude-newer` timestamp.
This timestamp is the absolute time relative to the time `uv` is being run, so it will change every time (e.g. with a `1 week` exclude-newer, this time will be 1 week in the past from the last time Renovate was run).

As a result, the Renovate uv manager will see the changed timestamp as a changed artifact, which will trigger it to update the commit (for update branches). For lockfile maintenance, this manifests as "empty" maintenance commits that do nothing beyond updating the lockfile.

## Expected behavior

Commits are only updated if there is a change to package versions, ignoring `exclude-newer` date.

## Link to the Renovate issue or Discussion

TBD

