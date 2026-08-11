# Security policy

This repository is a template for Apple Shortcuts. It should never contain real user secrets.

## Never commit or publish

Do not commit, upload, or share:

- Govee API keys
- real Govee device IDs
- screenshots containing API keys or device IDs
- exported `.shortcut` files that contain personal values
- public iCloud Shortcut links that contain personal values

Use placeholders instead:

```text
YOUR_GOVEE_API_KEY
YOUR_SKU
YOUR_DEVICE_ID
```

## If a secret is leaked

If you accidentally expose a Govee API key:

1. Revoke or regenerate the key in your Govee account.
2. Replace the key inside your private shortcut.
3. Remove the exposed key from Git history, issues, screenshots, and iCloud Shortcut links where possible.
4. Publish only a sanitized replacement.

## Reporting a leak in this repository

If you find a leaked secret here:

1. Open a GitHub issue without repeating the secret.
2. Mention only the file path and line number.
3. The maintainer should remove the secret and rotate the affected key.

## Privacy model

This project:

- does not run a server
- does not collect telemetry
- does not store user data
- does not proxy Govee API requests

The shortcut runs locally on the user's device and sends requests directly to the Govee Open API.

## Public shortcut links

Before publishing an iCloud Shortcut link, follow [`docs/publishing.md`](docs/publishing.md).

A public link should be treated as public software distribution, not as a private backup.
