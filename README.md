# action-create-github-release

[![Push to main](https://github.com/dnd-mapp/action-create-github-release/actions/workflows/push-main.yml/badge.svg)](https://github.com/dnd-mapp/action-create-github-release/actions/workflows/push-main.yml)
[![License](https://img.shields.io/github/license/dnd-mapp/action-create-github-release)](LICENSE)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://prettier.io)

A composite GitHub Action that creates a GitHub Release and its mirroring "Announcements" Discussion, optionally attaching caller-supplied release assets.

## Usage

```yaml
steps:
    - name: Create GitHub release
      uses: dnd-mapp/action-create-github-release@<SHA> # vX.Y.Z
      with:
          assets: |
              dist/*.tgz
```

### Inputs

| Name     | Description                                                                                                                                                             | Default |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| `assets` | Newline-separated list of extra files to attach to the release. Each line may be a literal path or a glob pattern; a line whose glob matches no files fails the action. | `''`    |

Omit `assets` (or leave it empty) to create a release with no attached files.

### Requirements

This action is zero-config beyond `assets`: it reads release notes from `.github/release-notes.md`, creates the release under the `"Announcements"` discussion category, and tags it `$GITHUB_REF_NAME`. None of that is configurable.

The calling job needs `permissions: contents: write` and `permissions: discussions: write`; the built-in `${{ github.token }}` (used internally by this action) is sufficient, no separate token input is required.

Pin to a commit SHA (not a floating tag) as shown above; the `# vX.Y.Z` comment is just a human-readable label of which release that SHA corresponds to. See [CHANGELOG.md](CHANGELOG.md) for release history, and the git tags for available versions (each release is tagged `vX.Y.Z`, with the `v1` tag floating to the latest `v1.x.y`).

## Contributing

See the org-wide [CONTRIBUTING.md](https://github.com/dnd-mapp/.github/blob/main/CONTRIBUTING.md) for how to propose changes, and [DEVELOPMENT.md](DEVELOPMENT.md) for how to work in this repository day-to-day. This project follows the [Code of Conduct](https://github.com/dnd-mapp/.github/blob/main/CODE_OF_CONDUCT.md).

## Security

See [SECURITY.md](https://github.com/dnd-mapp/.github/blob/main/SECURITY.md) for how to report a vulnerability.

## Support

See [SUPPORT.md](https://github.com/dnd-mapp/.github/blob/main/SUPPORT.md) for how to get help.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release history.

## License

[MIT](LICENSE)
