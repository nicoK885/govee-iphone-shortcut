# Publishing a public iCloud Shortcut

Use this checklist before sharing an iCloud Shortcut link publicly.

The goal is to publish a **template**, not your personal working shortcut.

## Why this matters

When you share an Apple Shortcut, the shared shortcut can include embedded text, URLs, request bodies, variable defaults, and other values. If your API key is stored in a Text action, it can become part of the shared shortcut.

For this project, that means a public shortcut must never contain:

- your real Govee API key
- your real Govee device ID
- personal room names or notes
- screenshots that reveal secrets

## Safe release process

### 1. Duplicate your working shortcut

In the Shortcuts app:

1. Long-press your working shortcut.
2. Tap **Duplicate**.
3. Rename the copy to something like:

```text
Govee Toggle Template
```

Keep your original private shortcut unchanged.

### 2. Replace personal values with placeholders

In the copied shortcut, replace these values:

```text
YOUR_GOVEE_API_KEY
YOUR_SKU
YOUR_DEVICE_ID
```

Recommended placeholder values:

| Field | Public placeholder |
|---|---|
| API key | `YOUR_GOVEE_API_KEY` |
| SKU | `YOUR_SKU` |
| Device ID | `YOUR_DEVICE_ID` |

Do not leave any value that belongs to your own account or lamp.

### 3. Make sure the public template cannot control your lamp

Before sharing, check the shortcut manually:

- no real API key in Text actions
- no real device ID in JSON bodies
- no real device ID in comments or notes
- no real values in duplicated hidden branches
- no screenshots with secrets

### 4. Share the sanitized copy

Only after sanitizing:

1. Open the copied shortcut.
2. Tap **Share**.
3. Choose **Copy iCloud Link**.
4. Paste the link into the README or release notes.

### 5. Optional: rotate your API key

If you previously created an iCloud link from a shortcut that contained your real API key, rotate the key before publishing the repository widely.

## README wording

Use wording like this:

```md
## Import the shortcut

Import the sanitized template:

[Add Govee Toggle Shortcut](https://www.icloud.com/shortcuts/REPLACE_WITH_SANITIZED_LINK)

After importing, replace:

- `YOUR_GOVEE_API_KEY`
- `YOUR_SKU`
- `YOUR_DEVICE_ID`
```

## Do not claim official status

Use:

```text
Unofficial community template
```

Do not use:

```text
Official Govee Shortcut
Govee-approved app
Govee integration by Govee
```
