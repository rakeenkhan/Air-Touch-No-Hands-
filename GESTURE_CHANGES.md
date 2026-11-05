# AirTouch gesture controls — Revision 2

## Gesture map

| Pose | How to perform | Action |
|---|---|---|
| Closed fist | Curl index, middle, ring, pinky and hold ~0.8s | Open the app selected by **Fist opens** |
| Open palm, moving upward | All four fingers extended; move your entire open hand upward, following your index finger | Swipe/scroll up |
| Open palm, moving downward | All four fingers extended; move your entire open hand downward, following your index finger | Swipe/scroll down |
| Middle finger alone | Extend only your middle finger, hold ~0.85s | Skip forward 10 seconds (if player supports it) |
| Ring finger alone | Extend only your ring finger, hold ~0.85s | Skip backward 10 seconds (if player supports it) |

Index-only, pinky-only, and static open-palm poses do **not** trigger controls. The old open-palm hold-to-pause and OK/peace shortcuts have been intentionally disabled to avoid conflicts.

## Stability

- Uses smoothed palm and index-fingertip vertical movements, requiring both to move in the same direction.
- Ignores sideways or tiny movements, and slow camera drift.
- Uses a minimum distance and speed threshold, an action cooldown, and a stillness-to-rearm rule to prevent accidental opposite-direction swipes on the way back.
- Prevents repeats of fist/middle/ring held gestures until the pose changes.
- Every Start begins in Practice mode. This blocks all phone actions (including opening the selected app) until the user chooses **Enable live controls**. Five gestures appear in the progress indicator.

## Testing

Plain Kotlin simulation cases passed when compiled with kotlinc. The full Android APK was not built in this environment; physical phone recognition remains to be checked in Android Studio.
