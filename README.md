# CALMROOT — cat-cottage prototype

A responsive, installable web app for gentle stress-management exercises. The interface is designed to work on desktop and mobile browsers and can be installed on supported Android devices as a Progressive Web App (PWA).

## Features
- Paced breathing pause (60 seconds; optional and stoppable)
- 5–4–3–2–1 grounding exercise
- Optional mood check-ins and private notes
- Local-only storage, data export, and delete-all controls
- Responsive layout, semantic controls, keyboard Escape support, visible focus states, and reduced-motion consideration
- Offline caching after first visit on supported browsers

## Run locally
Service workers and PWA installation require a secure context (`https://` or `localhost`). From this folder, run a local static server, for example:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in a browser.

## Install on Android
Host this folder on an HTTPS site, open it in Chrome on Android, then choose the browser menu and select **Install app** or **Add to Home screen** (wording varies). This is a PWA, not a native APK. A native Android package would require a separate Android/Capacitor wrapper and build/signing process.

## Privacy and health limitations
- Mood and journal data are saved in `localStorage` on the current browser/device only. There is no account, analytics, advertising, or backend.
- Anyone with access to the unlocked device/browser profile may see saved entries. Exported JSON files are not encrypted.
- Clearing browser data may remove entries. Do not save highly sensitive content on a shared device.
- This prototype is not a medical device or treatment. It does not diagnose anxiety or alopecia, predict hair loss, or promise to prevent symptoms. Dermatology and mental-health professionals can provide individualized care.


## Cat-cottage visual update
The interface now uses a warm cream, soft sage, and blush palette; rounded cards and controls; a floating Moss cat hero illustration; and paw-print accents across the sign-in, profile, wellbeing, and companion areas. Core local-only prototype behavior is unchanged.


## Google sign-in setup (CALMROOT Web Client)

The current prototype has Google Identity Services wired to the OAuth Client ID configured by the app owner. Google sign-in uses the official Google-rendered button. After Google returns an ID credential, the page uses the basic name and email to prefill the profile form. **This front-end prototype does not verify the ID token on a server and is not production-grade authentication.** The profile is saved only in this browser's `localStorage`; there is no central user database or cloud sync.

### Test locally

1. In Google Cloud Console, open **Google Auth Platform → Clients** and select `CALMROOT Web Client`.
2. Under **Authorized JavaScript origins**, add `http://localhost:8000` (exactly; no trailing path). Keep the app in Testing mode and add your own Google account as a test user if prompted.
3. In this folder, run `python -m http.server 8000`.
4. Open `http://localhost:8000` in your browser. Do not open `index.html` directly as a `file://` URL.
5. If Google reports `origin_mismatch`, add the exact origin shown in the browser address bar to the OAuth client settings.

Only the public OAuth Client ID is included in this front-end. Never place an OAuth client secret in this HTML file. A production release needs a secure backend to verify Google ID tokens and safely store users' data.
