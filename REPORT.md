# E5. AR Flashcard Learning System: Report

## 1. Topic selection and flashcard content design
- **Topic:** the Solar System (six planets). Chosen because the subject is visual and 3D, so AR adds real value over paper cards.
- **Card design:** front = a question plus an unnamed 3D planet on the marker; back = the planet's name and one fact.
- **Principles:** one idea per card, a question that cannot be answered without recalling, a single supporting fact.
- **Table:** copy the `DECK` array from `index.html` (marker ID, question, answer, fact).

## 2. AR trigger mechanism design
- **Tracking:** MediaPipe Hands (21 landmarks per hand) runs on the webcam feed in real time. The planet is anchored to the palm centre; its size follows wrist-to-knuckle distance, so it scales with depth.
- **Triggers:** (a) pinch (thumb-index distance / hand size below 0.3, with hysteresis) reveals the answer; (b) touching the planet with the index fingertip of the second hand also reveals it; (c) carrying the planet into the green or red target for 0.8 s rates the card. Mouse, touch and keyboard are fallbacks.
- **Why markerless:** no printed cards or extra hardware, works offline, light enough for an 8 GB M2 Air.
- **Diagram:** hand detected -> planet anchored -> pinch/poke -> answer -> carry to target -> feedback ring -> next card.

## 3. Visualization and feedback strategy
- **Visualization:** a shaded, rotating planet drawn on the live camera feed (Saturn has rings). The planet's name stays hidden until reveal, forcing recall.
- **Feedback:** the ring around the marker turns green (Got it) or red (Review again); a message states the new Leitner box; the mastery % updates.
- **Spaced repetition:** Leitner boxes 1 to 3 stored in `localStorage`. "Got it" moves up; "Review" resets to Box 1.
- **UI:** Apple HIG: systemBlue accent, system font, 8pt spacing, 44pt tap targets, translucent glass panels, light/dark adaptive.

## 4. Prototype / workflow demo
- Run steps are in `README.md`. Code walkthrough: sections 1 to 5 in `index.html`.

## 5. Screenshots / demo video
Insert here: (a) marker detected with question, (b) revealed answer and label, (c) green and red feedback rings, (d) Deck view, (e) 30 to 60 s screen recording.

## 6. Self-learning effectiveness reflection
Write this from your own use. Suggested method and prompts:
1. Test yourself on all six cards before using the system (score /6), use it for 10 minutes, then retest next day (score /6).
2. Did the 3D planet help recall compared with plain text? Why?
3. Did the dwell trigger feel natural, or did you prefer tapping?
4. Limits: marker dependence, lighting, six cards only, recognition vs. free recall.
5. Improvements: more topics, audio, image-target tracking (MindAR), per-card scheduling by date.
