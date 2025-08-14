# Browser Haptics — Haptic Video Player

A minimal demo that pairs an HTML5 video with browser-side haptic feedback (vibration/haptics), tuned for an F1 clip. The player uses the Vibration API on supporting mobile devices and includes progressive fallbacks for iOS where the standard vibration API is not available.

## Features

- Play an MP4 video with synchronized haptic events (pre-defined timeline).
- Background RPM-style haptic patterns between events.
- Intensity control via a slider.
- Device-aware fallbacks: standard `navigator.vibrate()` on Android, iOS-specific checkbox `switch` haptic technique (iOS 18+) and visual feedback where hardware haptics aren't supported.

## Files

- `index.html` — main demo UI and JavaScript logic.
- `f1-video.mp4` — example video (local file included in repo).
- `README.md` — this file.

## Quick start (local)

Open the demo in a browser by either double-clicking `index.html` or serving the folder and visiting it from a mobile device to test haptics.

Recommended (serving with Python from PowerShell):

```powershell
# from the repository root
python -m http.server 8000
# then open http://localhost:8000 in your browser or on your phone (same network)
```

Or use any static file server / Live Server extension.

## How to use

1. Open the page in a browser.
2. Tap the Play button to start the video. Haptics are enabled automatically when playback starts (if supported).
3. Use the intensity slider to scale haptic strength.
4. Use the Test Vibration button to check device feedback.

## Haptics & Platform notes

- Android / Chromium-based mobile browsers: the demo uses the standard Web Vibration API (`navigator.vibrate`) and should provide haptic feedback when allowed.
- iOS (Safari): iPhones historically do not support `navigator.vibrate()`; starting with iOS 18 WebKit added limited haptic feedback for `<input type="checkbox" switch>`. The demo includes a progressive fallback that attempts to use that technique and otherwise provides visual feedback.
- Desktop: most desktops do not have vibration hardware; the demo will still run and show visual feedback and timeline events.

## Testing recommendations

- For full haptic testing, use a modern Android phone (Chrome) for `navigator.vibrate` behavior.
- For iOS haptics, test on Safari with iOS 18+ to experience the checkbox-switch fallback. Other iOS browsers are currently wrappers over WebKit and may not expose the same behavior. Possibly not working on iPhones.

## Known limitations

- iOS does not support the standard Vibration API; haptic behavior may be limited or unavailable depending on OS/browser.
- Autoplay is restricted on mobile; the user must interact (tap Play) for playback and haptics to start.