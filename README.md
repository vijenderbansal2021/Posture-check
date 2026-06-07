# Posture Check — PWA

A minimal, beautiful posture reminder app. Works offline, no account required, free to publish everywhere.

---

## What It Does

- Random posture reminders every **20–40 minutes**
- Energetic synthesized chime (Web Audio API — no audio files needed)
- Haptic vibration on supported devices
- Background notifications (when permission granted)
- Tracks daily reminder count + streak days
- Fully offline via Service Worker
- Stores state in localStorage — no server, no account

---

## Files

```
posture-check/
├── index.html       ← Full app (single file)
├── sw.js            ← Service Worker (offline + caching)
├── manifest.json    ← PWA manifest (install prompt, icons, theme)
├── icons/
│   ├── icon.svg     ← Source icon
│   ├── icon-192.png ← Required for PWA / Android
│   └── icon-512.png ← Required for splash screen / stores
└── README.md
```

---

## Publishing Guide

### 🌐 Web (Free Hosting)

**Netlify** (recommended — free forever):
1. Drag the entire `posture-check/` folder to netlify.com/drop
2. Done — you get a live URL instantly
3. Optional: connect a custom domain

**GitHub Pages**:
1. Push to a GitHub repo
2. Settings → Pages → Deploy from main branch
3. Live at `https://yourusername.github.io/posture-check`

**Vercel / Cloudflare Pages**: Also free, same drag-and-drop or Git-connect flow.

---

### 📱 Google Play Store (Android) — Free via PWABuilder

1. Host the app on any HTTPS URL (Netlify above)
2. Go to **pwabuilder.com** → enter your URL
3. Click **Package for Stores** → **Android (TWA)**
4. Download the `.aab` bundle
5. Create a free Google Play Console account ($25 one-time fee)
6. Upload the bundle → Publish as free app

---

### 🍎 Apple App Store (iOS) — Free via PWABuilder

1. Same hosted URL
2. pwabuilder.com → **iOS** package
3. Download the Xcode project
4. Open in Xcode (Mac required), set your Bundle ID
5. Apple Developer account ($99/year) → Archive & submit
6. Or publish as a web app — iOS users can "Add to Home Screen" and it works natively

---

### 🪟 Microsoft Store (Windows) — Free via PWABuilder

1. Same hosted URL
2. pwabuilder.com → **Windows** package
3. Download the `.msix` installer
4. Microsoft Partner Center (free account) → Publish as free app
5. Also works as a standalone install from Edge (PWA install prompt)

---

### 📦 Amazon Appstore / Samsung Galaxy Store

Both accept Android APKs. Use the TWA APK from PWABuilder (same as Google Play flow), then re-submit to each store.

---

## Customization

**Change reminder interval**: Edit `MIN_MS` and `MAX_MS` in `index.html`
**Add reminder messages**: Edit the `MESSAGES` array
**Change chime notes**: Edit the `notes` array in `playChime()`
**Colors**: Edit CSS variables in `:root`

---

## Technical Notes

- **Audio**: Uses Web Audio API to synthesize a three-note ascending chime (C5→E5→G5 + bell). No audio files. Works offline.
- **Notifications**: Requested contextually when user taps Start. Falls back gracefully if denied.
- **Background**: Service Worker caches all assets. App works with zero network connection after first load.
- **Privacy**: Zero data collection, zero analytics, zero external requests after fonts load.
