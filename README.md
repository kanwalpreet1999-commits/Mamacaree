# Mama Care: native Android and iOS app (Capacitor)

The app is the web code in `www/`. Capacitor wraps it in a real Android/iOS app.
Reminders use native local notifications, so they fire daily even when the app is closed.

## One-time setup
- Install Node.js 20 or newer.
- Android: install Android Studio. iOS: a Mac with Xcode (iOS cannot be built on Windows or Linux).

## Build steps
```
npm install
npx cap add android        # and/or: npx cap add ios
npm run assets             # makes app icons + splash from the assets/ folder
npx cap sync
npx cap open android       # or: npx cap open ios
```

## Android: make the APK
In Android Studio: Build > Build Bundle(s) / APK(s) > Build APK(s).
Send the APK to a phone to install, or use Build > Generate Signed Bundle for the Play Store (AAB).

## iOS
In Xcode: pick your team under Signing & Capabilities, press Run for a phone, or Product > Archive for the App Store.
Publishing needs an Apple Developer account (paid yearly). Google Play needs a one-time developer fee.

## Notes
- Exact reminder times on Android 12+ may need the "Alarms & reminders" permission; the app falls back to approximate timing otherwise.
- Edit content (tips, checkups, warning signs) in `www/index.html`, then run `npx cap sync`.
- Package versions move on; if `npm install` complains, run `npm install @capacitor/core@latest @capacitor/cli@latest @capacitor/android@latest @capacitor/ios@latest @capacitor/local-notifications@latest`.
- This is general pregnancy guidance, not medical advice. Have a doctor review the content before public release.
