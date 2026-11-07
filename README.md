# GK GAME BOOSTER

Package: `com.gk.gamebooster` · Kotlin · Android 7.0+ (minSdk 24) · targetSdk 30 (Android 11) · White + Red gaming theme
कोई paid library नहीं — सिर्फ AndroidX / Material (free).

## Features / फीचर्स
1. Gaming Dashboard (RAM, battery, temperature, storage + BOOST NOW)
2. Headshot Training Mode (Easy / Medium / Hard, accuracy, best score, vibration)
3. Free Fire Sensitivity presets (Rusher / Balanced / Precision)
4. Free Fire MAX support
5. BGMI + PUBG Mobile support (launch + sensitivity presets)
6. RAM & Performance guide + Clean RAM
7. Add Game (कोई भी installed game जोड़ें)
8. One-Tap Game Launcher (▶ PLAY, optional auto-boost)
9. Gaming Tips (9 categories)
10. Settings screen
+ Offline AI Gaming Assistant

Supported package names: Free Fire `com.dts.freefireth`, Free Fire MAX `com.dts.freefiremax`,
BGMI `com.pubg.imobile`, PUBG Mobile `com.tencent.ig`.

> यह app किसी game को modify नहीं करता और cheat नहीं देता। सिर्फ launcher, training और tips हैं।

## Project structure
```
.github/workflows/android.yml   ← GitHub पर APK अपने-आप बनाता है
settings.gradle.kts, build.gradle.kts, gradle.properties
app/build.gradle.kts            ← app की settings (package, SDK, libraries)
app/src/main/AndroidManifest.xml
app/src/main/java/com/gk/gamebooster/
  MainActivity.kt        Dashboard
  TrainerActivity.kt / TrainerView.kt   Headshot Training
  SensitivityActivity.kt Sensitivity presets
  PerformanceActivity.kt RAM & Performance
  AddGameActivity.kt     Add Game
  TipsActivity.kt        Gaming Tips
  SettingsActivity.kt    Settings
  AssistantActivity.kt   AI Assistant (offline)
  GameStore.kt           Games list, Booster, battery
  Prefs.kt, Ui.kt, BaseActivity.kt
app/src/main/res/ (anim, drawable, values)
```

## APK कैसे बनाएँ (सिर्फ Android phone से)

### Step 1 — Termux install करें
F-Droid से Termux install करें (Play Store वाला पुराना है, उसे न लें).

### Step 2 — Tools install करें
```
pkg update -y && pkg upgrade -y
pkg install -y git gh unzip
termux-setup-storage
```
(storage permission पूछे तो Allow दबाएँ)

### Step 3 — ZIP खोलें
ZIP फ़ाइल Downloads में होनी चाहिए:
```
cd ~
unzip -o ~/storage/downloads/GK-GAME-BOOSTER.zip
cd GK-GAME-BOOSTER
```

### Step 4 — Git में अपना नाम डालें
```
git config --global user.name "YourName"
git config --global user.email "your@email.com"
git config --global init.defaultBranch main
```

### Step 5 — GitHub में login करें
(पहले github.com पर free account बना लें)
```
gh auth login
```
GitHub.com → HTTPS → "Login with a web browser" चुनें। Termux एक code दिखाएगा; browser में वह code डालें।

### Step 6 — Project upload करें
```
git init
git add .
git commit -m "GK GAME BOOSTER first version"
gh repo create gk-game-booster --public --source=. --remote=origin --push
```

### Step 7 — Build का इंतज़ार
```
gh run watch
```
3–6 मिनट लगते हैं। हरा ✓ आए तो APK तैयार है।
(या browser में: GitHub → आपकी repo → Actions tab)

### Step 8 — APK download करें
```
gh run download -n GK-GAME-BOOSTER-debug-apk -D ~/storage/downloads/GK-APK
```
Browser से: Actions → latest run → नीचे **Artifacts** → GK-GAME-BOOSTER-debug-apk (ZIP में APK मिलेगा, extract करें)।

### Step 9 — Install करें
Files app → Downloads → GK-APK → `app-debug.apk` → "Install unknown apps" allow करें → Install.
Play Protect warning आए तो "More details → Install anyway" (यह आपका अपना debug APK है).

## Code बदलकर दोबारा build
```
cd ~/GK-GAME-BOOSTER
git add . && git commit -m "update" && git push
```
Push करते ही नया APK अपने-आप बनता है।

## Troubleshooting
- `gh: command not found` → `pkg install gh`
- `unzip: cannot find` → ZIP का नाम/जगह जाँचें: `ls ~/storage/downloads`
- Build लाल ✗ हो → `gh run view --log-failed` का error मुझे भेजें।
- Game "Not installed" दिखे → game phone में installed होना चाहिए; या Add Game से जोड़ें।

## Android Studio (optional)
Android Studio में "Open" करके यह folder खोलें; Gradle sync अपने-आप होगा।
