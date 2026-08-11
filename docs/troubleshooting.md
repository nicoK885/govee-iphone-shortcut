# Troubleshooting

Common problems when building or running the shortcut.

## Shortcut says a parameter is missing

Likely cause:

- an **If** action contains an empty second condition

Fix:

1. Open the red action.
2. Look for an empty row named **Condition** / **Bedingung**.
3. Remove only the empty condition row.
4. Do not delete the whole If block.

## The `If` action does not offer `is`

Likely cause:

- Shortcuts treats the value as a dictionary/object instead of text

Fix:

1. Add a **Text** action.
2. Put the variable into that Text action.
3. Set a new variable from the Text action.
4. Use the new text variable in the **If** condition.

Example:

```text
CurrentPower → Text → CurrentPowerText
If CurrentPowerText is 1
```

## Shortcut returns code 401

Likely cause:

- wrong API key
- missing `Govee-API-Key` header
- API key copied with spaces or line breaks

Fix:

- paste the API key again
- check the header name exactly:

```text
Govee-API-Key
```

## Shortcut returns code 400

Likely cause:

- wrong JSON body
- wrong `sku`
- wrong `device` ID
- `NewPower` inserted as literal text
- missing `Content-Type: application/json`

The control body should contain:

```json
"value": 1
```

or:

```json
"value": 0
```

Not:

```json
"value": "1"
```

and not:

```json
"value": "NewPower"
```

## Shortcut runs but does not toggle

Check whether the state response contains:

```json
{
  "type": "devices.capabilities.on_off",
  "instance": "powerSwitch",
  "state": {
    "value": 1
  }
}
```

If `powerSwitch` is not the second capability in your response, change the **Get Item from List** index in the shortcut.

For the tested H607C response, `powerSwitch` was at index `2`.

## Shortcut shows the number 0 or 1 at the end

Likely cause:

- a temporary test output action is still present

Remove actions like:

- Quick Look
- Show Result
- Show Alert

## API works in testing but not from Lock Screen

Try:

- run the shortcut once from the Shortcuts app
- approve any permission prompts
- then run it from the Lock Screen again
- check Wi-Fi or mobile data
- check whether a Focus mode blocks Shortcuts prompts

## Device is offline

Check:

- device is powered on
- device is connected in the Govee app
- API key belongs to the same Govee account
- device appears in the `user/devices` response

## I exposed my API key

Immediately:

1. Revoke or regenerate the key in your Govee account.
2. Replace it inside your private iPhone Shortcut.
3. Delete or replace screenshots that contained the key.
4. If you shared an iCloud Shortcut link containing the key, stop using that link and publish a sanitized copy instead.
