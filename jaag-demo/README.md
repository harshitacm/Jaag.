# Jaag — Rider Safety Monitor (demo prototype)

Single-file HTML/CSS/JS prototype for the iQOO City Battles Hyderabad submission.

## How to run
Just open `index.html` in a browser (Chrome recommended on Android for camera + motion sensor access).
No build step, no dependencies, no server required — but if camera/sensor permissions
misbehave when opened as a local `file://` path, serve it locally instead:

```
cd jaag-demo
python3 -m http.server 8000
```

Then open http://localhost:8000 on your phone (same wifi network) or http://localhost:8000 on the same machine.

## What's real vs simulated
- Real: front camera feed, live accelerometer/gyroscope readings, voice warnings (Web Speech API),
  countdown-based escalation logic, manual SOS flow, platform dashboard toggle, face-visibility fallback toggle.
- Simulated (labeled in the UI): eye-closure/drowsiness scoring — use the "Simulate drowsy eyes" and
  "Simulate erratic riding" buttons. A production Android build would replace this with on-device
  ML Kit face landmarks running on the Snapdragon NPU.

## Demo flow
1. Rider tab → let it sit a few seconds.
2. Tap "Simulate drowsy eyes" → moderate risk → voice warning fires.
3. Tap again (or add "Simulate erratic riding") → high risk → "Are you okay?" countdown appears.
4. Let it hit zero → auto-call screen with mock emergency contact + location.
5. Toggle "face visible" to show the helmet/mask/night-riding fallback branch.
6. Tap the SOS button separately → skips straight to the call screen, no confirmation step.
7. Switch to "Platform" tab (mirror to laptop via Office Kit) → shows the delivery-platform dashboard,
   safety hold state, and early-resume approval.
