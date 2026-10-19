# AR Flashcard Learning System (E5): Solar System

Real-time hand-tracked AR flashcards in the browser. Works offline on a MacBook Air M2 (8 GB). No markers, no install, no build step.

## Run it
```bash
cd ar-flashcards
python3 -m http.server 8000
```
Open http://localhost:8000 in Chrome and allow the camera. Keep the `lib/` folder next to `index.html`.

## How the AR works
The webcam feed is the real world. MediaPipe Hands tracks your hand 30+ times a second, and a 3D-shaded planet is **anchored to your palm**: it follows your hand and scales as you move closer to or away from the camera.

| You do | What happens |
|---|---|
| Show an open hand | The planet sits on your palm and follows it |
| Pinch thumb + index finger | Reveals the answer |
| Touch the planet with a fingertip of your other hand | Also reveals the answer |
| Carry the planet into the green or red circle and hold ~1 s | "Got it" or "Review again" |
| Mouse / trackpad | Click the planet, then the circles (or use the buttons) |

Keyboard: `Space` reveal, `G` got it, `R` review, `D` card list, `1`-`6` jump to a card.
Tips: good front lighting, hand about 40 to 70 cm from the camera, palm facing the camera.

## Demo capture on macOS
Screenshot `Cmd+Shift+4`, screen recording `Cmd+Shift+5`.

## Files
- `index.html`: all code, in 6 commented sections (content, learner state, AR/hand tracking, logic, render loop, UI).
- `lib/mediapipe/`: Google MediaPipe Hands (hand-tracking model + WebAssembly), bundled so no internet is needed.
- `REPORT.md`: write-up skeleton for the six deliverables.
