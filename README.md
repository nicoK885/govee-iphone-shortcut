# Govee iPhone Shortcut

[![Status](https://img.shields.io/badge/status-community%20template-blue)](#)
[![Platform](https://img.shields.io/badge/platform-iPhone%20Shortcuts-lightgrey)](#)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

A small **unofficial Apple Shortcuts template** for toggling compatible Govee lights from an iPhone.

It is built for one simple use case:

> Wake iPhone → tap one Lock Screen button → toggle the light on or off.

No custom app. No server. No shared API key. The shortcut calls the Govee Open API directly from Apple Shortcuts.

> [!IMPORTANT]
> This project is **not affiliated with, endorsed by, sponsored by, or maintained by Govee**. Govee is a trademark of its respective owner. This repository is a community template only.

## What it can do

- Toggle a Govee light on/off with one shortcut
- Run from the Shortcuts app
- Run from the iPhone Lock Screen
- Run from the Action Button, Back Tap, Siri, or widgets
- Use each user's own Govee API key
- Work with devices that expose `devices.capabilities.on_off` / `powerSwitch`

## Tested device

| Device | SKU | Status |
|---|---:|---|
| Govee Floor Lamp 2 | `H607C` | Tested |

Other Govee lights may work if their Govee API response contains this capability:

```json
{
  "type": "devices.capabilities.on_off",
  "instance": "powerSwitch"
}
```

## Quick start

1. Get your own Govee API key.
2. Find your device `sku` and `device` ID.
3. Import or build the shortcut.
4. Replace the placeholder values.
5. Add it to the iPhone Lock Screen.

Full guide: [`docs/setup.md`](docs/setup.md)

## Shortcut template link

A public iCloud Shortcut template should only be published after it has been sanitized.

A safe public template must contain placeholders only:

```text
YOUR_GOVEE_API_KEY
YOUR_SKU
YOUR_DEVICE_ID
```

Do **not** publish an iCloud Shortcut link that contains a real API key or real device ID.

Sanitizing checklist: [`docs/publishing.md`](docs/publishing.md)

## Required values

| Value | Example | Notes |
|---|---|---|
| `Govee-API-Key` | `YOUR_GOVEE_API_KEY` | Personal secret. Never publish. |
| `sku` | `H607C` | Product model from the Govee API. |
| `device` | `AA:BB:CC:DD:EE:FF:00:11` | Device identifier from the Govee API. Treat as private. |

How to get them: [`docs/get-device-info.md`](docs/get-device-info.md)

## How it works

The shortcut performs two API calls:

1. `device/state` — read the current `powerSwitch` value.
2. `device/control` — send the opposite value.

Toggle logic:

```text
current value 1 → send 0
current value 0 → send 1
```

Request examples: [`examples/request-bodies.md`](examples/request-bodies.md)

## Repository contents

```text
docs/
  setup.md             Step-by-step shortcut setup
  get-device-info.md   How to find SKU and device ID
  publishing.md        How to publish a safe iCloud template
  troubleshooting.md   Common errors and fixes

examples/
  request-bodies.md    Reusable Govee API request bodies
```

## Security

Never commit or share:

- your Govee API key
- your real device ID
- screenshots containing secrets
- an exported shortcut that still contains personal values

If you accidentally share a shortcut containing your API key, regenerate the key before publishing anything else.

See [`SECURITY.md`](SECURITY.md).

## Roadmap

Possible future improvements:

- sanitized iCloud Shortcut template link
- setup screenshots
- multiple lamp support
- separate shortcuts for brightness/color
- compatibility table for more Govee models

## License

MIT. See [`LICENSE`](LICENSE).
