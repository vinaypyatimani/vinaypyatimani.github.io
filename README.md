# Baden Marathon Trainer — Build Your Own APK

This folder is a complete, installable PWA (Progressive Web App). Follow these
steps to turn it into a real `.apk` you can sideload onto any Android phone —
no coding, no Android Studio required.

## Step 1 — Put it online (free, ~2 minutes)

Android's app-packaging tool needs your app to live at a real `https://` URL
(this is a security requirement called Digital Asset Links — it proves you
own the app). Easiest free option:

**Netlify Drop** (no account needed):
1. Go to https://app.netlify.com/drop
2. Drag this entire folder onto the page
3. You'll get a live URL like `https://random-name-123.netlify.app`

Alternatives: GitHub Pages, Vercel, Cloudflare Pages — all free and similar.

## Step 2 — Generate the APK with PWABuilder (free, no code)

1. Go to https://www.pwabuilder.com
2. Paste your Netlify URL (from Step 1) into the box and click **Start**
3. PWABuilder scans your app and shows a report — you should see green
   checkmarks for Manifest and Service Worker (already set up for you here)
4. Click **Package for stores** → choose **Android**
5. Leave the default options (they're sensible) and click **Generate**
6. Download the `.zip` — inside it you'll find a signed `.apk` file
   (and a `.aab` if you ever want to publish to the Play Store)

## Step 3 — Install it on your phone

1. Transfer the `.apk` to your Android phone (email, Drive, USB — any way)
2. Tap the file on your phone
3. If prompted, allow "Install unknown apps" for that source (one-time
   Android security prompt — this is normal for sideloaded apps)
4. Tap **Install** — it now lives as a real app icon, no browser needed

## What's in this folder

- `index.html` — the entire app (plan, workouts, nutrition, journal)
- `manifest.json` — tells Android the app's name, icon, and colors
- `sw.js` — service worker, makes the app work offline and installable
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — app icons
  (placeholder design — swap these with your own artwork any time,
  keep the same filenames and sizes)

## Notes

- Your training data (runs/workouts you log) is stored **locally on the
  device** the app is installed on. It does not sync between devices —
  use the Export CSV / Import CSV buttons in the Journal tab to move data
  between phones or back it up.
- If you update `index.html` later, just re-drag the folder to Netlify
  (or re-push to GitHub Pages) and rebuild in PWABuilder to get an updated
  APK.
- This skips the Google Play Store entirely — it's a direct-install APK.
  If you ever want it on the Play Store, PWABuilder's Android package
  also includes the `.aab` file the Store requires, plus a short guide.
