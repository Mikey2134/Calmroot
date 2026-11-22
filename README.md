# CALMROOT — Alopecia-aware wellbeing companion

A responsive, installable web app for emotional check-ins, private reflection, confidence support, breathing, and grounding. It is a wellbeing companion, not a medical service or a treatment for alopecia areata.

## Features
- Google sign-in through Firebase Authentication
- Cloud Firestore profile and app-data sync for signed-in users
- Mood check-ins and private journal notes
- Confidence Corner with gentle affirmations and an optional journal prompt
- “On a difficult day” shortcuts to breathing, grounding, and supportive reminders
- 60-second paced breathing exercise (optional and stoppable)
- 5–4–3–2–1 grounding exercise
- Data export and delete controls
- Responsive mobile layout and installable Progressive Web App (PWA)
- Service worker cache versioning and online-first page navigation

## Deploy on GitHub Pages
1. Keep `index.html`, `sw.js`, `manifest.webmanifest`, `icon.svg`, and `firestore.rules` in the same repository directory.
2. Commit the files to the branch and folder used by GitHub Pages.
3. In GitHub, open **Settings → Pages** and verify the correct source branch/folder.
4. In Firebase Authentication settings, keep the live site's domain in **Authorized domains** (for the current site: `mikey2134.github.io`).
5. In Firebase Console → Firestore Database → Rules, review and publish `firestore.rules` only if it matches the app's intended access policy. Do not weaken rules to make errors disappear.
6. Test Google sign-in, log out, mood saving, journal saving, and reload after signing back in.

## Install on Android
Open the HTTPS GitHub Pages URL in Chrome on Android, tap the three-dot menu, and choose **Install app** or **Add to Home screen** if offered. This creates an installable web app; it is not a native APK.

## Privacy and safety
- When signed in, profile and app data sync to the Firebase project. The project owner administers the database and may technically access stored records; do not enter information you would not want the service operator to handle.
- Preview/local mode stores data in the current browser and does not cloud-sync.
- Exported JSON files are not encrypted. Protect exported files and avoid using a shared, unlocked device for private journaling.
- The app does not diagnose alopecia areata, assess hair loss causes, recommend medication changes, or promise hair regrowth. A dermatologist can advise on medical care; qualified mental-health support may help if distress is persistent.
- Breathing is optional. Stop if dizzy, short of breath, or uncomfortable and return to normal breathing.

## Local testing
Service workers and installation require HTTPS or `localhost`. From this directory, run:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/` in a browser. Firebase authentication will also require the appropriate localhost domain/origin configuration.
