# LayerBru Workshop PWA

A progressive web app for controlling your LayerBru workshop devices via Home Assistant.

## Setup

### 1. Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `layerbru-pwa`)
2. Upload all files from this folder into the repo root:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icons/icon-192.png`
   - `icons/icon-512.png`
3. Go to **Settings → Pages → Source → Deploy from branch → main → / (root)**
4. Your PWA will be live at `https://YOUR-USERNAME.github.io/layerbru-pwa`

### 2. Configure Home Assistant

Open the PWA in Safari on your iPad and scroll to **// CONFIGURATION**:

| Field | Value |
|-------|-------|
| HA IP ADDRESS | Your laptop's static IP (e.g. `192.168.1.50`) |
| PORT | `8123` |
| ACCESS TOKEN | Your long-lived HA token |
| TV LIGHTS ENTITY | Your Magic Home entity ID |

To get a long-lived token:
1. In HA, click your username (bottom left)
2. Scroll to **Long-Lived Access Tokens**
3. Click **Create Token**, name it `LayerBru PWA`
4. Copy and paste into the PWA config

### 3. Add to iPad Home Screen

1. Open Safari on your iPad
2. Go to `https://YOUR-USERNAME.github.io/layerbru-pwa`
3. Tap the **Share** icon → **Add to Home Screen**
4. Name it `LayerBru` → **Add**

It will appear as a full-screen app with no Safari chrome.

## Features

- **Garage door** — live state, tap to open/close
- **Left & Right monitors** — toggle individually or both at once
- **Bedroom aircon** — live mode/temp display, quick mode buttons
- **TV lights** — toggle + Warm / Cool / Purple / Off presets
- **Workshop Mode scene** — one tap activates everything
- **HA dashboard links** — quick links to all your dashboards
- **Auto-refresh** — states update every 15 seconds
- **Offline support** — app shell cached via service worker

## Notes

- The PWA calls your HA API directly from the browser. This works on your **local Wi-Fi** since HA is on `192.168.x.x`.
- If you want to control devices **away from home**, you'll need to expose HA externally (e.g. via Nabu Casa / HA Cloud, or a reverse proxy).
- Your token is stored in the browser's localStorage on the iPad — it never leaves your device.
