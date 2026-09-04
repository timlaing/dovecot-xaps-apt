# Contributing to dovecot-xaps-apt

Thank you for contributing. This repository hosts a signed APT repository for the
[dovecot-xaps-plugin](https://github.com/timlaing/dovecot-xaps-plugin) and
[dovecot-xaps-daemon](https://github.com/timlaing/dovecot-xaps-daemon) packages and is deployed to GitHub Pages.

## Before you start

Search the existing issues and pull requests before opening a new one. Bugs in the plugin belong in the
[dovecot-xaps-plugin issue tracker](https://github.com/timlaing/dovecot-xaps-plugin/issues) and bugs in the daemon in the
[dovecot-xaps-daemon issue tracker](https://github.com/timlaing/dovecot-xaps-daemon/issues), unless they concern this
repository's own configuration or publishing workflow.

## Development setup

Clone the repository and install the tooling used by this project:

```sh
sudo apt-get update
sudo apt-get install reprepro lintian dpkg-dev gpg
git clone https://github.com/timlaing/dovecot-xaps-apt.git
cd dovecot-xaps-apt
```

Pre-commit hooks run under `prek` and are declared in `.pre-commit-config.yaml`. Install them with:

```sh
prek
```

## Repository layout

- `conf/distributions` - reprepro distribution configuration (codename `stable`, `amd64 arm64`, signed index).
- `public-key.asc` - the APT signing key used to verify the repository.
- `.github/workflows/` - publishing, reconciliation, and quality workflows.
- `CHANGELOG.md` - user-facing change log (Keep a Changelog format).

## Making changes

1. Fork the repository and create a focused branch such as `feature/my-change` or `fix/my-bug`.
2. Keep each pull request limited to one self-contained change.
3. Follow the repository's existing style and keep pull-request titles to conventional prefixes
   such as `feat:`, `fix:`, `docs:`, or `chore:` so Release Drafter can categorize the change.
4. Do not commit the signing key material. `private-key.asc` and `fingerprint` are git-ignored; keep them out of history.

## Verification

Before submitting a pull request, run:

```sh
prek
reprepro --basedir . check
```

Changes to the publish or reconcile workflows should be validated against a published `.deb`; the
`Publish APT Repository` workflow gates packages with `lintian --fail-on error`. Describe any checks you could
not run and why.

Signing-key rotation and revocation procedures live in [`SECURITY.md`](SECURITY.md).

## Pull requests

Complete the pull-request template, link related issues with `Fixes #123` where appropriate, and allow maintainer
edits.
