# 🧪 Pro Cosmetic Chemist AI

> AI-powered cosmetic formulation assistant — build to Android APK using GitHub Actions (no local setup required)

---

## 📦 What This Does

Push your code to GitHub → GitHub automatically builds your `.apk` → Download and install on Android.

**No Android Studio. No JDK. No local setup needed.**

---

## 🚀 Quick Start — Get Your APK in 5 Steps

### Step 1 — Create a GitHub Repository

1. Go to [github.com](https://github.com) → Sign in (or create free account)
2. Click **"New repository"** (green button, top right)
3. Name it: `pro-cosmetic-chemist-ai`
4. Set to **Public** or **Private** (both work)
5. Click **"Create repository"**

---

### Step 2 — Upload This Project

**Option A — GitHub Web UI (easiest, no Git needed):**
1. On your new repo page, click **"uploading an existing file"**
2. Drag and drop ALL files from this folder
3. Make sure to include the `.github/workflows/` folder
4. Click **"Commit changes"**

**Option B — Git command line:**
```bash
git init
git add .
git commit -m "Initial commit - Pro Cosmetic Chemist AI"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/pro-cosmetic-chemist-ai.git
git push -u origin main
```

---

### Step 3 — Watch the Build

1. Go to your GitHub repo
2. Click the **"Actions"** tab (top menu)
3. You'll see **"Build Android APK"** running (yellow dot = in progress)
4. Wait ~5–8 minutes for it to complete (green ✅)

---

### Step 4 — Download Your APK

1. Click the completed workflow run
2. Scroll down to **"Artifacts"** section
3. Click **"pro-cosmetic-chemist-debug-apk"** to download
4. Unzip the downloaded file → you have `app-debug.apk`

---

### Step 5 — Install on Android

1. Transfer `app-debug.apk` to your Android phone (email, USB, Google Drive, etc.)
2. On your phone: open **Files** app → find the APK → tap it
3. If prompted: tap **"Allow from this source"** → **"Install"**
4. Done! Find **Pro Chemist AI** in your app drawer 🎉

---

## 🔄 How to Trigger a New Build

The APK rebuilds automatically every time you push to `main`. You can also trigger it manually:

1. Go to **Actions** tab
2. Click **"Build Android APK"**
3. Click **"Run workflow"** → **"Run workflow"** (green button)

---

## 📁 Project Structure

```
pro-cosmetic-chemist-ai/
├── .github/
│   └── workflows/
│       ├── build-apk.yml       ← Builds debug APK on every push
│       └── release-apk.yml     ← Builds signed release APK on version tags
├── src/
│   └── index.html              ← The complete app
├── capacitor.config.json       ← Android WebView config
├── package.json                ← Capacitor dependencies
└── README.md                   ← This file
```

---

## 🏷️ Create a Release APK (Optional — for distribution)

A **release APK** is signed and suitable for sharing publicly or uploading to app stores.

### Create a Keystore (one time only)
On any computer with Java installed:
```bash
keytool -genkey -v -keystore my-release-key.jks \
  -keyalg RSA -keysize 2048 -validity 10000 \
  -alias prochemist
```

### Convert keystore to Base64
```bash
# Mac/Linux:
base64 -i my-release-key.jks | tr -d '\n'

# Windows PowerShell:
[Convert]::ToBase64String([IO.File]::ReadAllBytes("my-release-key.jks"))
```

### Add GitHub Secrets
1. Go to your repo → **Settings** → **Secrets and variables** → **Actions**
2. Add these 4 secrets:
   - `KEYSTORE_BASE64` → paste the base64 output from above
   - `KEYSTORE_PASSWORD` → your keystore password
   - `KEY_ALIAS` → `prochemist`
   - `KEY_PASSWORD` → your key password

### Trigger a Release
```bash
git tag v1.0.0
git push origin v1.0.0
```
GitHub will build a signed APK and create a **Release** page with the APK attached for download.

---

## ❓ Troubleshooting

| Problem | Fix |
|---------|-----|
| Actions tab not visible | Make sure `.github/workflows/` folder was uploaded |
| Build fails at Gradle step | Check Actions log — usually a sync issue, re-run workflow |
| APK installs but shows white screen | Check your device has internet access |
| "App not installed" error | Uninstall any previous version first |
| Workflow not triggering | Check you pushed to `main` branch (not `master`) |

---

## 💡 Tips

- **Free GitHub accounts** get 2,000 Actions minutes/month — more than enough
- Each build takes ~5–8 minutes
- The debug APK is fully functional — only difference from release is it's not signed
- You can share the APK file directly with anyone — no app store needed

---

## 📱 App Features

- 🧪 Full cosmetic formula generation (INCI list, percentages, phases)
- ⚗️ Batch process design with temperatures & mixing protocols  
- 📊 Stability, pH, and preservation guidance
- 🌿 Natural/vegan/cost-reduced formula variations
- 💾 Persistent formula library (saves across sessions)
- 📱 Mobile-optimized UI with touch-friendly design
- 🤖 Powered by Claude Sonnet 4 (Anthropic)
