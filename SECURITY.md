# Security policy

## Secrets

This project must never contain real user secrets.

Do not commit:

- Govee API keys
- real device IDs
- screenshots containing API keys
- exported shortcut files that contain personal values

## Reporting a secret leak

If you find a leaked API key or real device ID in this repository:

1. Open a GitHub issue without repeating the secret.
2. Mention only the file path and line number.
3. The owner should remove the secret and rotate the affected key.

## For users

If you accidentally shared your Govee API key:

1. Revoke or regenerate it in your Govee account.
2. Replace it inside the iPhone Shortcut.
3. Remove screenshots or exports that contained the old key.

## Scope

This is an unofficial template for Apple Shortcuts. It does not run a server and does not collect user data.
