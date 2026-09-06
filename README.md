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

Add the signing key and repository. Choose the suite that matches your Dovecot major:

| Dovecot version | Example OS           | Suite          |
| --------------- | -------------------- | -------------- |
| 2.4             | Ubuntu 26.04         | `stable`       |
| 2.3             | Ubuntu 24.04         | `stable-dov23` |

```sh
curl -fsSL https://raw.githubusercontent.com/timlaing/dovecot-xaps-apt/main/public-key.asc \
  | sudo gpg --dearmor --yes -o /usr/share/keyrings/dovecot-xaps-archive-keyring.gpg

# Dovecot 2.4 (Ubuntu 26.04 and newer)
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/dovecot-xaps-archive-keyring.gpg] https://timlaing.github.io/dovecot-xaps-apt stable main" \
  | sudo tee /etc/apt/sources.list.d/dovecot-xaps.list

# Dovecot 2.3 (Ubuntu 24.04): use stable-dov23 instead
# echo "deb [arch=amd64 signed-by=/usr/share/keyrings/dovecot-xaps-archive-keyring.gpg] https://timlaing.github.io/dovecot-xaps-apt stable-dov23 main" \
#   | sudo tee /etc/apt/sources.list.d/dovecot-xaps.list

sudo apt update && sudo apt install dovecot-xaps-plugin xapsd
```

The `stable` suite holds the daemon plus the Dovecot 2.4 plugin; `stable-dov23` holds only the Dovecot 2.3 plugin build,
whose package version sorts below the 2.4 build so the two cannot collide within a single suite.

## Signing Key

**Fingerprint:** `D6F4 7642 A542 4C78 332C  CD8E EAD2 766F 4E85 7693`

See [`SECURITY.md`](SECURITY.md) for key rotation and revocation procedures.
