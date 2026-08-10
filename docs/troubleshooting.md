# Troubleshooting

## The shortcut says a parameter is missing

This usually means an **If** action has an empty second condition.

Fix:

1. Open the red action.
2. Look for an empty row named **Condition** / **Bedingung**.
3. Remove only the empty condition row.
4. Do not delete the whole If block.

## The shortcut returns code 401

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

## The shortcut returns code 400

Likely cause:

- wrong JSON body
- wrong `sku`
- wrong `device` ID
- `NewPower` inserted as text in the wrong place

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

## The shortcut runs but does not toggle

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

## The shortcut shows the number 0 or 1 at the end

You probably still have a temporary test output action.

Remove actions like:

- Quick Look
- Show Result
- Show Alert

## The API works in testing but not from Lock Screen

Try:

- unlock the iPhone once and run it from the Shortcuts app
- then run it from the Lock Screen again
- check that mobile data or Wi-Fi is available
- avoid Focus modes that block Shortcut execution

## I exposed my API key

Regenerate or revoke the key in your Govee account and replace it in the shortcut.
