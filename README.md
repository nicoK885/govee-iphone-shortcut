# Govee iPhone Shortcut

Unofficial iPhone Shortcut template to toggle Govee lights from the iPhone Lock Screen, Action Button, Back Tap, widgets, or the Shortcuts app.

This project is intentionally simple: it uses the Govee Open API directly from Apple Shortcuts. No server, no extra app, no shared API key.

> This project is not affiliated with, endorsed by, or sponsored by Govee.

## What it does

- Toggles a Govee light on or off
- Works from iPhone Shortcuts
- Can be placed on the iPhone Lock Screen
- Uses the user's own Govee API key
- Supports the Govee Open API `powerSwitch` capability
- Tested with the Govee H607C Floor Lamp 2

## Quick start

1. Get your own Govee API key.
2. Find your device `sku` and `device` ID.
3. Build the shortcut using the steps in [`docs/setup.md`](docs/setup.md).
4. Add the shortcut to your Lock Screen or Action Button.

## Required values

You need three values:

| Value | Example | Notes |
|---|---|---|
| `Govee-API-Key` | `your-api-key-here` | Never publish this. |
| `sku` | `H607C` | Your Govee product model. |
| `device` | `AA:BB:CC:DD:EE:FF:00:11` | Your device identifier from the Govee API. |

## Supported devices

This template should work with Govee devices that expose this capability:

```json
{
  "type": "devices.capabilities.on_off",
  "instance": "powerSwitch"
}
```

It was created and tested with:

- Govee Floor Lamp 2 / H607C

Other Govee lights may work by changing `sku` and `device`.

## Repository contents

- [`docs/setup.md`](docs/setup.md) — step-by-step iPhone Shortcut setup
- [`docs/get-device-info.md`](docs/get-device-info.md) — how to find your SKU and device ID
- [`docs/troubleshooting.md`](docs/troubleshooting.md) — common problems and fixes
- [`examples/request-bodies.md`](examples/request-bodies.md) — reusable API request templates

## Safety

Do not commit or share:

- your Govee API key
- your real device ID
- screenshots containing secrets

If you accidentally expose your API key, revoke or regenerate it in your Govee account.

## License

MIT. See [`LICENSE`](LICENSE).
