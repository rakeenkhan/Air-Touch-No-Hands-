# AirTouch — Revised hand gestures (Revision 2)

AirTouch uses the front camera and MediaPipe to recognise finger poses. You start the camera service by pressing **START**. Every start enters **Practice mode**, which blocks all actions until **Enable live controls** is tapped.

## Gestures

| Pose | Action |
|---|---|
| ✊ Closed fist held about 0.8 s | Open the app selected with **Fist opens** |
| ✋ Open palm moving UP | Scroll up / next video |
| ✋ Open palm moving DOWN | Scroll down / previous video |
| Middle finger ONLY held about 0.85 s | Skip forward 10 seconds |
| Ring finger ONLY held about 0.85 s | Skip backward 10 seconds |

**Important:** For either scroll, extend ALL non-thumb fingers, including your index finger. Move your whole hand up/down instead of only bending your index finger. An index-only pose is not a scroll gesture anymore. For each skip, keep only the indicated finger extended.

## Android Studio setup

1. Extract this ZIP and use **File → Open** to open the extracted `AirTouch` folder.
2. Select your connected Samsung phone as the target device, keep **app** selected, and click **Run**.
3. On the phone, enable AirTouch under Accessibility and approve Camera permission, if needed.
4. Press **START**. The camera runs, but every gesture remains non-executing until you explicitly turn live controls on.
5. Practice each of the five gestures, checking the PASS messages and the `0/5`…`5/5` indicator.
6. Tap **Enable live controls** to allow phone actions. Tap **Pause + practice again** to safely turn them off at any time.
7. Use **Fist opens** to select the app that the closed fist should launch.

## Reliability and limitations

- Scroll recognition requires an open palm for approximately 0.25 seconds before measuring deliberate vertical movement. Both the palm and index tip must move up/down together; the code ignores jitter, lateral waves, and small movements.
- After a swipe, make your hand still briefly before another swipe. The engine uses a cooldown and a steady-hand rearm check to help prevent accidental return swipes.
- A hand and face must be visible to the front camera. Use good lighting, keep the phone awake, and avoid excessive motion blur.
- Skip forward/back is carried out by a media key or a double tap in a supporting video player. Not all apps support 10-second skips.
- Opening another app by fist works while AirTouch is already started and live. A closed fist **cannot launch a camera service that is not yet running**.

## Files

- `app/src/main/java/com/airtouch/GestureEngine.kt` — new detection algorithm
- `GestureService.kt` — updated action labels
- `PracticeGate.kt` — safe 5-gesture practice tracking
- `MainActivity.kt` — updated instructions and progress
- `app/src/test/java/com/airtouch/GestureScenarios.kt` — updated Kotlin simulations

Local pure-Kotlin simulations passed. The complete Android app has **not** been built or tested on the physical phone in this environment.
