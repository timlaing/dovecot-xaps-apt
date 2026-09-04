# Security Policy

## Signing Key

This APT repository is signed with the following GPG key:

- **Fingerprint:** `093A 73B6 D553 7505 EB70  F917 958C 5D29 E4E2 3742`
- **UID:** Dovecot XAPS APT Repo Signing <dovecot-xaps-apt@users.noreply.github.com>
- **Public Key:** [`public-key.asc`](public-key.asc)

## Key Rotation Procedure

When rotating the signing key:

1. Generate a new 4096-bit RSA key pair locally:

   ```sh
   gpg --full-generate-key   # RSA 4096, no expiration, no passphrase
   ```

2. Update `conf/distributions` with the new fingerprint:

   ```sh
   SignWith: <NEW_FINGERPRINT>
   ```

3. Export and commit the new public key:

   ```sh
   gpg --export --armor <NEW_KEY_ID> > public-key.asc
   ```

4. Re-sign all existing repository metadata:

   ```sh
   reprepro --basedir . cleartrust
   reprepro --basedir . maintainreleases
   ```

5. Add the new private key as GitHub Actions secret `APT_SIGNING_PRIVATE_KEY`.

6. Remove the old private key from GitHub Actions secrets.

7. Update the fingerprint in this file and in `README.md`.

## Key Revocation

If a signing key is compromised:

1. Revoke the compromised key immediately:

   ```sh
   gpg --gen-revoke <KEY_ID> > revoke.asc
   gpg --import revoke.asc
   ```

2. Upload the revocation to a keyserver:

   ```sh
   gpg --keyserver hkps://keys.openpgp.org --send-keys <KEY_ID>
   ```

3. Follow the Key Rotation Procedure above to generate and deploy a new key.

4. Remove the compromised private key from GitHub Actions secrets.

## Contact

For security issues, please open a private issue or contact the repository maintainer directly.
