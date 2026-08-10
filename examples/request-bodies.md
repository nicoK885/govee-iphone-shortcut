# Request body examples

These examples use placeholders. Replace them with your own values.

```text
YOUR_SKU
YOUR_DEVICE_ID
```

## Get current device state

Endpoint:

```text
POST https://openapi.api.govee.com/router/api/v1/device/state
```

Headers:

```text
Govee-API-Key: YOUR_GOVEE_API_KEY
Content-Type: application/json
```

Body:

```json
{
  "requestId": "iphone-state",
  "payload": {
    "sku": "YOUR_SKU",
    "device": "YOUR_DEVICE_ID"
  }
}
```

## Turn light on

Endpoint:

```text
POST https://openapi.api.govee.com/router/api/v1/device/control
```

Body:

```json
{
  "requestId": "iphone-on",
  "payload": {
    "sku": "YOUR_SKU",
    "device": "YOUR_DEVICE_ID",
    "capability": {
      "type": "devices.capabilities.on_off",
      "instance": "powerSwitch",
      "value": 1
    }
  }
}
```

## Turn light off

Endpoint:

```text
POST https://openapi.api.govee.com/router/api/v1/device/control
```

Body:

```json
{
  "requestId": "iphone-off",
  "payload": {
    "sku": "YOUR_SKU",
    "device": "YOUR_DEVICE_ID",
    "capability": {
      "type": "devices.capabilities.on_off",
      "instance": "powerSwitch",
      "value": 0
    }
  }
}
```

## Toggle logic

Pseudo logic:

```text
state = current powerSwitch value

if state == 1:
    NewPower = 0
else:
    NewPower = 1

send NewPower to device/control
```
