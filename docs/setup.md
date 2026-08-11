# Setup guide

This guide creates one iPhone Shortcut named **Govee Toggle**.

The shortcut checks the current power state and sends the opposite value:

```text
current value 1 → send 0
current value 0 → send 1
```

## Before you start

You need:

- an iPhone with the Shortcuts app
- your personal Govee API key
- your Govee device `sku`
- your Govee `device` ID

If you do not know the SKU or device ID, follow [`get-device-info.md`](get-device-info.md).

## Placeholder values

Replace these placeholders everywhere in the shortcut:

```text
YOUR_GOVEE_API_KEY
YOUR_SKU
YOUR_DEVICE_ID
```

Example values:

```text
sku    = H607C
device = AA:BB:CC:DD:EE:FF:00:11
```

Do not publish your real API key or device ID.

## Shortcut structure

Create a new shortcut and name it:

```text
Govee Toggle
```

## 1. Store the API key

Add action: **Text**

```text
YOUR_GOVEE_API_KEY
```

Add action: **Set Variable**

```text
Set variable APIKey to Text
```

## 2. Build the state request body

Add action: **URL**

```text
https://openapi.api.govee.com/router/api/v1/device/state
```

Add action: **Text**

```json
{
  "requestId": "iphone-state",
  "payload": {
    "sku": "YOUR_SKU",
    "device": "YOUR_DEVICE_ID"
  }
}
```

Add action: **Set Variable**

```text
Set variable BodyState to Text
```

## 3. Call `device/state`

Add action: **Get Contents of URL**

Configure it like this:

```text
URL: URL
Method: POST
Headers:
  Govee-API-Key: APIKey
  Content-Type: application/json
Request Body: File
File: BodyState
```

Optional test:

- add **Quick Look** or **Show Result** temporarily
- run the shortcut
- check that the response contains `powerSwitch`
- delete the test output action afterwards

## 4. Read the current power value

Add action: **Get Dictionary Value**

```text
Get payload in Contents of URL
```

Add action: **Get Dictionary Value**

```text
Get capabilities in Dictionary Value
```

Add action: **Get Item from List**

```text
Get item at index 2 from Dictionary Value
```

For the tested H607C response, index `2` is the `powerSwitch` capability.

If your device returns a different order, inspect the JSON response and use the list item where:

```json
"instance": "powerSwitch"
```

Then add action: **Get Dictionary Value**

```text
Get state in Item from List
```

Add action: **Get Dictionary Value**

```text
Get value in Dictionary Value
```

Add action: **Set Variable**

```text
Set variable CurrentPower to Dictionary Value
```

## 5. Create the opposite value

Add action: **Text**

Insert the `CurrentPower` variable into the text field.

Add action: **Set Variable**

```text
Set variable CurrentPowerText to Text
```

Add action: **If**

```text
If CurrentPowerText is 1
```

Inside **If**:

Add action: **Text**

```text
0
```

Add action: **Set Variable**

```text
Set variable NewPower to Text
```

Inside **Otherwise**:

Add action: **Text**

```text
1
```

Add action: **Set Variable**

```text
Set variable NewPower to Text
```

Result:

```text
1 → 0
0 → 1
```

## 6. Build the control request body

Add action: **Text**

```json
{
  "requestId": "iphone-toggle",
  "payload": {
    "sku": "YOUR_SKU",
    "device": "YOUR_DEVICE_ID",
    "capability": {
      "type": "devices.capabilities.on_off",
      "instance": "powerSwitch",
      "value": NEWPOWER
    }
  }
}
```

Replace `NEWPOWER` with the `NewPower` variable.

Important:

```json
"value": NEWPOWER
```

Do not put quotation marks around `NewPower`.

Add action: **Set Variable**

```text
Set variable BodyControl to Text
```

## 7. Call `device/control`

Add action: **URL**

```text
https://openapi.api.govee.com/router/api/v1/device/control
```

Add action: **Get Contents of URL**

Configure it like this:

```text
URL: URL
Method: POST
Headers:
  Govee-API-Key: APIKey
  Content-Type: application/json
Request Body: File
File: BodyControl
```

Run the shortcut. The light should toggle.

## Add it to the Lock Screen

1. Long-press the iPhone Lock Screen.
2. Tap **Customize**.
3. Choose **Lock Screen**.
4. Replace one of the bottom controls.
5. Choose **Shortcut**.
6. Select **Govee Toggle**.

## Recommended backup

After it works:

1. Duplicate the shortcut.
2. Rename the copy to **Govee Toggle Backup**.
3. Keep it private.

## Publishing warning

Do not share your personal working shortcut as an iCloud link if it contains your real API key.

For public sharing, create a sanitized copy first. See [`publishing.md`](publishing.md).
