# Pull Request

<!-- Thank you for contributing to the Dovecot XAPS APT repository! Please fill
     out the template below to help us review your change. Every contribution
     is appreciated. -->

## Summary

<!-- Briefly describe the change and the problem it solves. -->

## Type of change

<!-- Check the box that applies. -->

- [ ] 🚀 Feature (`feature` / `enhancement`)
- [ ] 🐛 Bug fix (`bug` / `fix`)
- [ ] 🛠 Maintenance (`maintenance` / `dependencies`)
- [ ] 📚 Documentation (`documentation`)

## Related issues / PRs

<!-- Link any related issues or pull requests, e.g. Fixes #123. -->

## Changes

<!-- Describe the changes in detail. For metadata or signing-key changes,
     include the affected files (conf/distributions, public-key.asc) and any
     new fingerprint.

     Keep this PR focused: each PR should be a single, self-contained change.
     If your work spans multiple distinct fixes or features, split them into
     separate PRs so each can be reviewed and merged independently. -->

## Documentation

<!-- Check the boxes that apply. -->

- [ ] Updated `SECURITY.md` / `README.md` if the change affects installation or trust
- [ ] Updated `conf/distributions` if the fingerprint or suite changed
- [ ] Updated the fingerprint in `SECURITY.md` / `README.md` if the key changed

## Verification

<!-- What did you do to verify the change?

     Changes will not be processed unless the verification checks below are
     completed. Ensure every box that applies to your change is ticked before
     requesting a review. -->

- [ ] This PR is a single, self-contained change (one fix or feature only)
- [ ] The PR is editable by maintainers (`maintainer_can_modify` / "Allow edits from maintainers")
- [ ] Ran `.venv/bin/prek run --all-files` — all hooks pass
- [ ] Ran `npx prettier --check` on any changed YAML / markdown files
- [ ] Signing-key or metadata changes were verified with `reprepro check` and `gpg --import public-key.asc`
- [ ] No private key material (`private-key.asc`, `APT_SIGNING_PRIVATE_KEY`) is introduced

---

<!-- Thanks again for your contribution! 🙌 -->
