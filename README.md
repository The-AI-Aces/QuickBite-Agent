# Anandha's AI Ordering Assistant — Mobile App Setup

This folder is a ready-to-install **Progressive Web App (PWA)**. To turn it into
a real `.apk` you can install on Android (and optionally publish to the Play
Store), follow the two steps below. Both are free and take about 10 minutes
total.

---

## Step 1 — Put the app online (required before making the APK)

An APK-building tool needs a live web address to "wrap." Pick ONE free host:

### Option A: Netlify (easiest, drag & drop)
1. Go to https://app.netlify.com/drop
2. Drag this entire folder onto the page.
3. You'll get a live URL like `https://random-name-123.netlify.app`

### Option B: GitHub Pages
1. Create a new GitHub repo, upload these files (index.html, manifest.json,
   sw.js, icon-192.png, icon-512.png).
2. Repo Settings → Pages → set source to the main branch.
3. Your live URL will be `https://yourusername.github.io/your-repo-name`

Test the URL on your phone's browser first — you should see the app, and your
browser should offer "Add to Home Screen" / "Install app." If that works, the
APK step below will work too.

---

## Step 2 — Generate the real APK

1. Go to **https://www.pwabuilder.com** (free tool by Microsoft, used by real
   companies to ship PWAs to app stores).
2. Paste your live URL from Step 1 and click **Start**.
3. It will scan your app and show a readiness score (your manifest and
   service worker are already set up correctly for this).
4. Click **Package for Stores** → choose **Android**.
5. Download the generated **.apk** (for direct install/testing) or **.aab**
   (the format required for Google Play Store).

## Installing the APK on your phone
1. Transfer the `.apk` file to your Android phone (email, USB, Google Drive).
2. Tap the file. Android will ask you to allow installs from this source —
   approve it.
3. The app installs with its own icon, name, and splash screen — exactly like
   any app from the Play Store.

## Publishing to the Play Store (optional)
Use the `.aab` file from PWABuilder, create a free Google Play Developer
account ($25 one-time fee), and upload it through the Play Console. PWABuilder
also generates the signing key and store listing assets for you.

---

## What was fixed in this package
- The zip you uploaded had a broken, incomplete file split (index.html
  pointed to a `css/` and `js/` folder that didn't exist, and a missing
  `cart.js`). The working version was the standalone
  `Anandha's ai agent final.HTML` file — that's what this package is built
  from, now wired up properly as an installable app:
  - `manifest.json` — app name, icons, colors, standalone display mode
  - `sw.js` — offline caching so the app still opens without signal
  - `icon-192.png` / `icon-512.png` — app icons
  - `index.html` — your original app, now linked to the manifest and service
    worker, with iOS install support tags added too
