# dovecot-xaps-apt

APT repository for [dovecot-xaps](https://github.com/jayme-github/dovecot-xaps) — push notification support for Dovecot.

## Client Installation

Add the signing key and repository:

```sh
curl -fsSL https://raw.githubusercontent.com/jayme-github/dovecot-xaps-apt/main/public-key.asc \
  | sudo gpg --dearmor -o /usr/share/keyrings/dovecot-xaps-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/dovecot-xaps-archive-keyring.gpg] https://jayme-github.github.io/dovecot-xaps-apt stable main" \
  | sudo tee /etc/apt/sources.list.d/dovecot-xaps.list

sudo apt update && sudo apt install dovecot-xaps
```

## Signing Key

**Fingerprint:** `093A 73B6 D553 7505 EB70  F917 958C 5D29 E4E2 3742`

See [`SECURITY.md`](SECURITY.md) for key rotation and revocation procedures.
