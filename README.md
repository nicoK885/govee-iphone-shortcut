# Govee iPhone Shortcut

[![Status](https://img.shields.io/badge/status-community%20template-blue)](#)
[![Platform](https://img.shields.io/badge/platform-iPhone%20Shortcuts-lightgrey)](#)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

An **unofficial Apple Shortcuts template** for toggling compatible Govee lights from an iPhone with a single tap.

> Wake iPhone → tap a Lock Screen control → toggle the light on or off.

No custom app, no server, and no shared API key. The shortcut talks directly to the Govee Open API using each user's own credentials.

<p align="center">
  <a href="docs/screenshots.md">
    <img src="docs/images/shortcut-walkthrough-preview.jpg" alt="Govee iPhone Shortcut visual walkthrough" width="760">
  </a>
</p>

> [!IMPORTANT]
> This project is **not affiliated with, endorsed by, sponsored by, or maintained by Govee**. Govee is a trademark of its respective owner. This repository is an independent community project.

## Get started

### 1. Import the shortcut

[**Import Govee-Lampe-Toggle-v1 →**](https://www.icloud.com/shortcuts/8e6b064997884d5c97ebe91375867aa1)

The public shortcut is sanitized and contains placeholders only.

### 2. Add your values

Replace these placeholders inside the shortcut:

```text
YOUR_GOVEE_API_KEY
YOUR_SKU
YOUR_DEVICE_ID
```

### 3. Run it once

Run the shortcut from the Shortcuts app and approve any permission prompts.

### 4. Put it where you want it

Use it from the:

- iPhone Lock Screen
- Action Button
- Back Tap
- Siri
- Shortcuts widget
- Apple Watch, where supported

**Guides:** [Setup](docs/setup.md) · [Visual walkthrough](docs/screenshots.md) · [Find device info](docs/get-device-info.md) · [Troubleshooting](docs/troubleshooting.md)

## What it does

The shortcut performs two API calls:

1. `device/state` reads the current `powerSwitch` value.
2. `device/control` sends the opposite value.

```text
current value 1 → send 0
current value 0 → send 1
```

That gives you a true one-button toggle instead of separate ON and OFF shortcuts.

## Tested device

| Device | SKU | Status |
|---|---:|---|
| Govee Floor Lamp 2 | `H607C` | ✅ Tested |

Other Govee lights may work if their API response exposes:

```json
{
  "type": "devices.capabilities.on_off",
  "instance": "powerSwitch"
}
```

> [!NOTE]
> The included H607C shortcut reads `powerSwitch` from capability index `2`. Other models may return capabilities in a different order. See [Troubleshooting](docs/troubleshooting.md) if the shortcut reads the wrong item.

## Required values

| Value | Example | Notes |
|---|---|---|
| `Govee-API-Key` | `YOUR_GOVEE_API_KEY` | Personal secret. Never publish it. |
| `sku` | `H607C` | Product model returned by the Govee API. |
| `device` | `AA:BB:CC:DD:EE:FF:00:11` | Device identifier returned by the Govee API. Treat as private. |

How to retrieve these values: [`docs/get-device-info.md`](docs/get-device-info.md)

## Visual walkthrough

The full shortcut is documented with English iPhone screenshots:

[**Open the screenshot walkthrough →**](docs/screenshots.md)

The screenshots show:

- API key placeholder and state endpoint
- state request body
- reading `payload → capabilities → state → value`
- toggle logic with `CurrentPower` and `NewPower`
- control request body and `powerSwitch`

All public screenshots use sanitized placeholder values.

## Repository contents

```text
docs/
  setup.md             Step-by-step setup guide
  screenshots.md       Visual Apple Shortcuts walkthrough
  images/              Sanitized walkthrough screenshots
  get-device-info.md   Find SKU and device ID
  publishing.md        Publish a safe iCloud template
  troubleshooting.md   Common errors and fixes

examples/
  request-bodies.md    Reusable Govee API request bodies
```

## Security

Never publish:

- your Govee API key
- your real device ID
- screenshots containing secrets
- a shared shortcut that still contains personal values

If you accidentally expose an API key, rotate it before continuing to use or share the shortcut.

See [`SECURITY.md`](SECURITY.md) and [`docs/publishing.md`](docs/publishing.md).

## Contributing

Compatibility reports for other Govee models are welcome. Please remove API keys and real device IDs before posting screenshots, issues, or pull requests.

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Roadmap

Possible future improvements:

- compatibility table for more Govee models
- brightness controls
- color controls
- scene shortcuts
- multiple-light support

## License

MIT. See [`LICENSE`](LICENSE).
