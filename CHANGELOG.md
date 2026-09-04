# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog],
and this project adheres to [Semantic Versioning].

## [Unreleased]

### Added

- **APT repository foundation**: GPG signing key (`public-key.asc`) with `conf/distributions` reprepro configuration for the `stable` `amd64` suite.
- **Security policy**: `SECURITY.md` documenting the signing key, key rotation and revocation procedures, and contact information.
- **Publish workflow**: manually-triggered workflow that imports `.deb` release assets from the source repositories, signs the index, and deploys to GitHub Pages.
- **SonarQube scanning**: CI workflow and project configuration for branch and pull-request analysis.
- **Repository governance**: dependabot, CodeQL, release drafter, autolabeler, and PR/issue templates.
- **Pre-commit hooks**: `.pre-commit-config.yaml` running hygiene, linting, and formatting checks.
- **Documentation**: README with client installation steps and signing key fingerprint, plus PR and issue templates.

### Changed

- Corrected README repository URLs from the placeholder owner to `timlaing`.
- **Rotated the APT signing key** to a passphrase-less key (`D6F4 7642 A542 4C78 332C  CD8E EAD2 766F 4E85 7693`) so `reprepro` can sign non-interactively in CI; updated `public-key.asc`, `fingerprint`, `conf/distributions`, README, and SECURITY policy.
- **Fixed publish workflow GPG setup**: create `~/.gnupg`, configure loopback pinentry (`gpg-agent.conf` / `gpg.conf`), and install `pinentry-curses`.

### Fixed

- Publish workflow no longer fails signing the repository index with `GPGME:1: General error` caused by a passphrase-protected key in a non-interactive runner.
