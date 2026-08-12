# Screenshot walkthrough

These screenshots show the sanitized public shortcut template. They use placeholders only and do not contain a real Govee API key or real device ID.

## Overview

| Step | Screenshot | What to check |
|---:|---|---|
| 1 | <img src="images/01-api-key-and-state-url.jpg" width="220"> | API key placeholder and `device/state` URL |
| 2 | <img src="images/02-state-body-and-call.jpg" width="220"> | State request body and `BodyState` variable |
| 3 | <img src="images/03-state-payload-list.jpg" width="220"> | Read `payload`, `capabilities`, and item index `2` |
| 4 | <img src="images/04-read-state-value.jpg" width="220"> | Read `state.value` |
| 5 | <img src="images/05-save-current-power.jpg" width="220"> | Save current `powerSwitch` value |
| 6 | <img src="images/06-current-power-text-if.jpg" width="220"> | Convert current value to text and compare with `1` |
| 7 | <img src="images/07-new-power-if-otherwise.jpg" width="220"> | Set `NewPower` to `0` or `1` |
| 8 | <img src="images/08-otherwise-and-control-body.jpg" width="220"> | Finish the If block and start control request body |
| 9 | <img src="images/09-control-body-start.jpg" width="220"> | Build the `device/control` JSON body |
| 10 | <img src="images/10-control-body-newpower.jpg" width="220"> | Insert the `NewPower` variable and save `BodyControl` |

## Notes

- The screenshots are from Apple Shortcuts in English.
- Keep all public screenshots sanitized.
- Do not publish a screenshot containing a real API key or real device ID.
- Some screenshots use `H607C` because that is the tested example device.
