# Get device info

You need your Govee device `sku` and `device` ID.

Do not publish your real values in issues, screenshots, or pull requests.

## Option A: PowerShell on Windows

Open PowerShell and run this as one line:

```powershell
$Key = Read-Host "Govee API Key"; $r = Invoke-RestMethod -Method Get -Uri "https://openapi.api.govee.com/router/api/v1/user/devices" -Headers @{"Govee-API-Key"=$Key}; $r.data | Select-Object deviceName,sku,device
```

You should see output like this:

```text
deviceName     sku     device
----------     ---     ------
Floor Lamp     H607C   AA:BB:CC:DD:EE:FF:00:11
```

Use these values in the shortcut:

```text
sku    = H607C
device = AA:BB:CC:DD:EE:FF:00:11
```

## Filter for one model

Example for H607C:

```powershell
$Key = Read-Host "Govee API Key"; $r = Invoke-RestMethod -Method Get -Uri "https://openapi.api.govee.com/router/api/v1/user/devices" -Headers @{"Govee-API-Key"=$Key}; $r.data | Where-Object { $_.sku -eq "H607C" } | Select-Object deviceName,sku,device
```

## Option B: Inspect the Govee API response

The relevant endpoint is:

```text
GET https://openapi.api.govee.com/router/api/v1/user/devices
```

Required header:

```text
Govee-API-Key: YOUR_GOVEE_API_KEY
```

Look for your device in the response and copy:

- `deviceName`
- `sku`
- `device`

## What not to share

Never share:

- your API key
- your real device ID
- screenshots where either value is visible
