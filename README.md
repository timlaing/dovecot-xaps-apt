# dovecot-xaps-apt

[![License](https://img.shields.io/github/license/timlaing/dovecot-xaps-apt)](LICENSE)
[![Check](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/checks.yml/badge.svg)](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/checks.yml)
[![CodeQL](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/codeql.yml/badge.svg)](https://github.com/timlaing/dovecot-xaps-apt/actions/workflows/codeql.yml)
[![Dependabot](https://img.shields.io/badge/dependabot-enabled-025e8c)](https://github.com/timlaing/dovecot-xaps-apt/security/dependabot)

[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=ncloc)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Duplicated Lines (%)](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=duplicated_lines_density)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=coverage)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)

[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=vulnerabilities)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=security_rating)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=sqale_rating)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=reliability_rating)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=bugs)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)
[![Technical Debt](https://sonarcloud.io/api/project_badges/measure?project=timlaing_dovecot-xaps-apt&metric=sqale_index)](https://sonarcloud.io/summary/new_code?id=timlaing_dovecot-xaps-apt)

APT repository for Apple push notification support in Dovecot. Packages are
built and released from the [dovecot-xaps-plugin](https://github.com/timlaing/dovecot-xaps-plugin)
and [dovecot-xaps-daemon](https://github.com/timlaing/dovecot-xaps-daemon) source repositories.

## Changelog

See [`CHANGELOG.md`](CHANGELOG.md) for a history of changes.

## Client Installation

Add the signing key and repository. Choose the suite that matches your Dovecot major:

| Dovecot version | Example OS   | Suite      |
| --------------- | ------------ | ---------- |
| 2.4             | Ubuntu 26.04 | `resolute` |
| 2.3             | Ubuntu 24.04 | `noble`    |

```sh
curl -fsSL https://raw.githubusercontent.com/timlaing/dovecot-xaps-apt/main/public-key.asc \
  | sudo gpg --dearmor --yes -o /usr/share/keyrings/dovecot-xaps-archive-keyring.gpg

# Dovecot 2.4 (Ubuntu 26.04 and newer)
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/dovecot-xaps-archive-keyring.gpg] https://timlaing.github.io/dovecot-xaps-apt resolute main" \
  | sudo tee /etc/apt/sources.list.d/dovecot-xaps.list

# Dovecot 2.3 (Ubuntu 24.04): use noble instead
# echo "deb [arch=amd64 signed-by=/usr/share/keyrings/dovecot-xaps-archive-keyring.gpg] https://timlaing.github.io/dovecot-xaps-apt noble main" \
#   | sudo tee /etc/apt/sources.list.d/dovecot-xaps.list

sudo apt update && sudo apt install dovecot-xaps-plugin xapsd
```

Each suite is self-contained: it holds the matching Dovecot plugin build plus the daemon. The `noble` plugin version sorts below the 2.4 build, so the two cannot collide within a single suite. Suite names follow the Ubuntu release codenames (`resolute` for 26.04, `noble` for 24.04).

## Signing Key

**Fingerprint:** `D6F4 7642 A542 4C78 332C  CD8E EAD2 766F 4E85 7693`

See [`SECURITY.md`](SECURITY.md) for key rotation and revocation procedures.
