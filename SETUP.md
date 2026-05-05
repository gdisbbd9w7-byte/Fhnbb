# Guard AI Pro — Setup

## Open in Android Studio
1. Unzip `GuardAIPro.zip`.
2. Android Studio → **Open** → select the `GuardAIPro` folder.
3. Let Gradle sync (requires JDK 17, Android SDK 34).
4. Run on a device with Android 8.0+ (API 26).

## In-app Setup Steps
1. **Enable Accessibility Service**
   - Open the app → tap **1. Enable Accessibility Service**
   - Settings → Accessibility → **Guard AI Pro** → toggle ON → Allow.
2. **Grant Overlay Permission**
   - Tap **2. Grant Overlay Permission** → enable “Display over other apps”.
3. **Set PIN Lock**
   - Tap **3. Set / Change PIN** → enter a 4-digit PIN → Save.
4. **Start Protection Service**
   - Tap **4. Start Protection Service**. A persistent notification “Guard AI is protecting you” appears.

## Test
- Open Chrome and type `xxx` or `porn` in the URL bar / a page → the black warning screen launches and Bangla TTS speaks the warning. Back button is disabled for 2 seconds.

## Notes
- Bangla TTS requires a Bangla voice (Settings → System → Languages → Text-to-speech). If absent, it falls back to the device default.
- Remote blocklist URL is in `BlockListManager.REMOTE_URL` — replace with your endpoint serving `{"keywords":["..."]}`.
- NSFW image detection uses a skin-tone heuristic in `NsfwDetector.kt`. Swap with a TFLite model or a moderation API for production.
- Disabling the accessibility service from system settings cannot be programmatically blocked by Android; the app PIN-gates re-enabling and any in-app config changes.
