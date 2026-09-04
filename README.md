# dovecot-xaps-apt

APT repository for Apple push notification support in Dovecot. Packages are
built and released from the [dovecot-xaps-plugin](https://github.com/timlaing/dovecot-xaps-plugin)
and [dovecot-xaps-daemon](https://github.com/timlaing/dovecot-xaps-daemon) source repositories.

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
