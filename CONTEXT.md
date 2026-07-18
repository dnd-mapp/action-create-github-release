# @dnd-mapp/action-create-github-release

A reusable composite GitHub Action that creates a GitHub Release (and its mirroring "Announcements" Discussion) for a pushed `vX.Y.Z` tag, optionally attaching caller-supplied release assets.

## Language

**Release**:  
See the org-wide [Release Tooling context](https://github.com/dnd-mapp/.github/blob/main/docs/release-tooling/CONTEXT.md#language). This action creates one in a single `gh release create` call; it has no part in tagging, the calling workflow's act of pushing the `vX.Y.Z` tag that triggers it.

**Asset**:  
A file the caller supplies via the `assets` input (one path or glob pattern per line) that this action attaches to the Release. Excludes GitHub's own auto-generated "Source code (zip)/(tar.gz)" archives, which this action neither produces nor controls.

**Release notes**:  
The pre-written contents of `.github/release-notes.md`, passed to `gh release create --notes-file`. This action only reads that file at a hardcoded path; producing it is out of scope here (owned upstream, e.g. by `action-extract-release-notes`).  
_Avoid_: "changelog" for this file specifically, the two may be related upstream, but this action doesn't know or care how the file was produced.
