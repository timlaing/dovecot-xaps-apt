# dovecot-xaps-apt

[![License](https://img.shields.io/github/license/timlaing/dovecot-xaps-apt)](LICENSE)
[![Release](https://img.shields.io/github/v/release/timlaing/dovecot-xaps-apt)](https://github.com/timlaing/dovecot-xaps-apt/releases)
[![Check](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/checks.yml/badge.svg)](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/checks.yml)
[![CodeQL](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/codeql.yml/badge.svg)](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/codeql.yml)
[![Dependabot](https://img.shields.io/badge/dependabot-enabled-025e8c)](https://github.com/timlaing/dovecot-xaps-apt/security/dependabot)

APT repository for Apple push notification support in Dovecot. Packages are
built and released from the [dovecot-xaps-plugin](https://github.com/timlaing/dovecot-xaps-plugin)
and [dovecot-xaps-daemon](https://github.com/timlaing/dovecot-xaps-daemon) source repositories.

## Changelog

See [`CHANGELOG.md`](CHANGELOG.md) for a history of changes.

## Client Installation

Add the signing key and repository:

```sh
curl -fsSL https://raw.githubusercontent.com/timlaing/dovecot-xaps-apt/main/public-key.asc \
  | sudo gpg --dearmor --yes -o /usr/share/keyrings/dovecot-xaps-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/dovecot-xaps-archive-keyring.gpg] https://timlaing.github.io/dovecot-xaps-apt stable main" \
  | sudo tee /etc/apt/sources.list.d/dovecot-xaps.list

sudo apt update && sudo apt install dovecot-xaps-plugin dovecot-xaps-daemon
```

## Signing Key

**Fingerprint:** `093A 73B6 D553 7505 EB70  F917 958C 5D29 E4E2 3742`

See [`SECURITY.md`](SECURITY.md) for key rotation and revocation procedures.
