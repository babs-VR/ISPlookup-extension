# 🌐 ISP Lookup — Microsoft Edge Extension / Chrome

A lightweight Edge extension for VoIP analysts and help desk agents to instantly look up ISP, ASN, location, and connection type for any public IP address — without leaving the browser.

---

## Features

- **ISP / Organization** — identifies the carrier or company behind the IP
- **ASN** — Autonomous System Number for routing and peering lookups
- **Location** — city, region, and country
- **Connection type** — detects Proxy/VPN, Mobile, and Datacenter flags
- **Timezone** — useful for scheduling cross-region call tests
- **VoIP-aware tips** — automatically surfaces relevant notes based on what it finds:
  - Warns about CGNAT / double NAT for residential ISPs
  - Flags datacenter IPs as likely PBX or hosted VoIP infrastructure
  - Notes business/telecom IPs and shifts focus to QoS and firewall rules
- **Copy buttons** on every field for fast ticket entry
- **Enter key support** — no need to click the button

---

## Screenshots

> _Add your screenshots here_

---

## Installation

This extension is not published to the Edge Add-ons store. Install it manually as an unpacked extension:

1. Download or clone this repository
2. Open Microsoft Edge and navigate to `edge://extensions`
3. Enable **Developer mode** (toggle in the top-left)
4. Click **Load unpacked**
5. Select the `isp-lookup-extension` folder
6. The 🌐 icon will appear in your toolbar

To update after pulling new changes, go to `edge://extensions` and click the **refresh** icon on the extension card.

---

## Usage

1. Click the 🌐 icon in the Edge toolbar
2. Paste or type a public IP address into the input field
3. Press **Enter** or click **Look Up**
4. Results appear instantly with copy buttons on each field

### Supported formats

- IPv4: `8.8.8.8`
- IPv6: `2001:4860:4860::8888`

> **Note:** Private/internal IPs (e.g. `192.168.x.x`, `10.x.x.x`) will return a lookup failure — only public IPs are supported by the API.

---

## How It Works

Uses the free [ip-api.com](http://ip-api.com) JSON API — no API key required. Requests are made directly from the extension popup.

**Rate limit:** 45 requests/minute on the free tier. For higher volume, see [ip-api.com/docs](http://ip-api.com/docs).

**Fields requested:** `status`, `message`, `country`, `regionName`, `city`, `isp`, `org`, `as`, `query`, `timezone`, `mobile`, `proxy`, `hosting`

---

## File Structure

```
isp-lookup-extension/
├── manifest.json       # Extension manifest (MV3)
├── popup.html          # UI layout and styles
├── popup.js            # Lookup logic and API call
└── icons/
    ├── icon16.png
    ├── icon48.png
    └── icon128.png
```

---

## Customizing the Icon

Replace the files in the `icons/` folder with your own images at the correct sizes:

| File | Size |
|------|------|
| `icon16.png` | 16×16 px |
| `icon48.png` | 48×48 px |
| `icon128.png` | 128×128 px |

[favicon.io](https://favicon.io) is a quick free tool to generate all three sizes from an image or emoji. After replacing the files, hit **refresh** on `edge://extensions`.

---

## Privacy

- No data is stored locally or sent anywhere other than `ip-api.com`
- No user accounts, tracking, or analytics
- The extension requests no browser permissions beyond `http://ip-api.com/*`

---

## Related Tools

- [Phone Number Converter](../phone-converter-extension/) — convert between `(000) 999-9999` and `0009999999` formats with batch support

---

## License

MIT
