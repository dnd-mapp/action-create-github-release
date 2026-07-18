# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Composite GitHub Action that creates a GitHub Release and its mirroring "Announcements" Discussion, reading notes from `.github/release-notes.md` and tagging under the `"Announcements"` discussion category. Optional `assets` input: a newline-separated list of literal paths or glob patterns to attach as extra release files (see [ADR 0001](docs/adr/0001-newline-separated-glob-assets-input.md)).
