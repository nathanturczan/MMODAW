# The Scale Navigator Gameplay Loop: Explore → Capture → Share

Here's the full loop as a normal user experiences it, from opening the app to performing what they found.

---

## Phase 1: EXPLORE

The explore phase is about *moving through harmonic space*. There are two synchronized views of that space (the Navigator and the Scale Network) plus a chord-level view (the Chord Network) that lives inside whatever scale you're currently standing in.

### The Navigator (the hands-on close-up)

The Navigator (`src/components/Navigation/Navigator/Navigator.js`) is a p5.js canvas showing your **current scale as a central polygon**, ringed by its adjacent scales — the scales that differ from it by exactly one pitch class. This "differ by one note" adjacency is Tymoczko's organizing principle, so every neighbor is a smooth voice-leading move away.

- **Hovering a neighbor** (`Navigator.js:442-498`, `third_gen_hover`) fetches *that* neighbor's own neighbors and fans them out in a cascading reveal, so you can preview second-order moves ("if I went here, where could I go next?") without committing. Let go and they animate back inward and vanish.
- **Clicking the center scale** (`Navigator.js:408-410`) does *not* navigate — it stays put and regenerates a chord within the current scale. So the center is your "give me another idea in this key" button.
- **Clicking a neighbor** (`Navigator.js:414-435, 566-620`) animates that polygon into the center, rotates the ring to the new neighbors, and pushes the change into Redux (and out to plugins / ensemble members). That's how you actually *travel*.
- If you're on a **custom scale** outside the 57, the network can't compute neighbors, so the Navigator collapses to a single colored circle — a visual signal that you've stepped off the map.

### The Scale Network (the whole map)

The Scale Network (`src/components/Workspace/Visualization/`) shows all 57 scales at once, so the Navigator is the street view and this is the satellite view.

- **Arrangement** (`ScaleGraph3D/layout.js:182-266`): concentric rings by scale class — diatonic on the outer circle of fifths, then acoustic just inside it, then harmonic major/minor as three nested octagons, then hexatonic, octatonic, and whole-tone toward the center. The octagon groups are rotated/flipped algorithmically to minimize edge crossings.
- **2D vs 3D** (`index.js:291-322`): Planar mode shows the clean mathematical structure (good for seeing adjacencies and for mobile screens); 3D mode drops the scales into a force simulation you can orbit, where edges act like springs. Same graph, two ways of feeling it.
- **The mirror/flip** (`index.js:223-280`): you can flip the planar layout horizontally between "sharps clockwise" and "flats clockwise (Tymoczko)." This matters because different musicians read the circle of fifths in opposite rotational directions — a user who thinks in flats wants the layout oriented their way, so the flip is about matching the map to the player's mental model rather than changing the music. The choice persists to localStorage.
- **Visibility checkboxes** filter which scale classes are live. This is cross-functional: it dims network nodes, blocks Navigator hovers/clicks on hidden classes, prunes the autopilot's candidate scales, and filters the adjacent-scale list broadcast to plugins.

### The Chord Network (harmony inside the current scale)

Once you're standing in a scale, the Chord Network (`src/components/Workspace/Chords/VoiceLeadingGraph.js`, the newer feature set) shows every triad available in that scale, connected by single-note voice-leading edges — a lattice of where you can go chord-wise without leaving the key.

- **Why different layouts per scale class** (`VoiceLeadingGraph.js:256-401`): each scale class has a hand-authored template that reveals its *canonical* structure rather than letting physics scramble it. Diatonic is a 7-cycle ring; acoustic is a 7-cycle with the augmented triad placed asymmetrically; harmonic major/minor are hub layouts with a central mediant and two bridges; hexatonic is a cube rendered as two offset squares; octatonic is a rigid 4×4 grid (dim/major/minor/dim rows) pinned in place. The templates are transposition-invariant, so one template drives all 12 keys. The point is that the *shape teaches the theory* — the geometry of octatonic harmony genuinely differs from diatonic harmony, and the layout makes that legible.
- **Different uses**: (1) click a triad to select it; (2) hover/tap a triad to expand a satellite ring of extended chords (7ths, 9ths, etc.) on that root that fit the scale; (3) read the parsimonious edges to find smooth chord-to-chord paths; (4) watch continuity across scale changes — shared triads hold their position while new ones fly in from the left and departing ones exit right, so you keep your bearings when you modulate.
- Selection prefers the root-matched triad, so a C maj9 lights up the "C" node even though it adds notes.

### The chord checkboxes + voice-leading slider (steering the auto-generator)

These control the "Next Chord" auto-selection (`src/components/Workspace/Chords/Chords.js:957-1015`, engine in `ToneJS/ChordChooser.js`):

- **Allowed chord qualities** — which chord types are eligible (major, minor, 7ths, sus, etc.). Shift-click solos one, Alt-click enables all, Cmd-click inverts — fast moves for live play.
- **Allowed root movements** — which intervals between chord roots are permitted (unison, step, third, fourth/fifth, tritone), with jazz-style voice-position rules.
- **Voice-Leading Smoothness slider (0–100)** — a softmax *temperature* on chord choice. At 0 the next chord is basically random within your constraints; at 100 it always picks the chord whose notes move the least from the current one (cost computed via a Hungarian voice-assignment with penalties for added/dropped voices and big leaps). It biases *which chord you land on*, not which scales are reachable.
- **Pivot modulations** (`Chords.js:803-839`) list every scale that contains your current chord — one click uses that chord as a pivot to modulate. This is the bridge back to the scale layer: your chord tells you your exit doors.

---

## Phase 2: CAPTURE

Exploration is ephemeral; the Sketchpad (`src/components/Sketchpad/`) is where you keep the good stuff. Think of it as picking your favorite toys out of the toychest so you can play with just those.

- **Capturing what you discovered**: hit the 💾 button and the current scale+chord becomes a node (`Navigation.js:923-983` → `useSketchpadState.js:161-199`). These "discovered" nodes carry the scale id, root, chord name, and labels.
- **Custom nodes**: via the Custom Node modal (`CustomNodeModal.js`) you can define your own scale/chord from a 12-pitch-class grid (right-click sets the root; the one rule is chord ⊆ scale). These carry their definition *inline* on the node (`custom: { scale, chord }`), so they don't depend on the 57-scale database and survive export and ensemble sync. They render with a dashed border and a plain circle to distinguish them from network-standard nodes.
- **Arranging progressions** (`Sketchpad/index.js`): the Sketchpad is a React Flow canvas. Drag nodes to reposition, drag from handle to handle to draw connections (edges become your progression/flow, bidirectional pairs get special rendering), right-click for a context menu to delete nodes or prune incoming/outgoing edges. You're literally building a narrative path through the harmony you liked.
- **Saving**: auto-persists to localStorage in the browser, or rehydrates from the DAW project when running as a plugin. You can also export/import the whole sketchpad as JSON (drag-and-drop to re-import), which is how a sketch travels between machines or into a session.
- **Playing back a node**: click any node to restore that harmonic state. And because of a recent fix (`6b638a14b`, `504cd24b2`), each such click is recorded into the **Score** history rather than silently replacing the current chord.

### The Score (the running record)

The Score (`src/components/Workspace/Score/Score.js`, history in `prevStateController.js`) is the automatic ledger of every scale/chord move you make — from the Navigator, the Chord Network, or Sketchpad clicks. It renders your journey as real music notation (VexFlow, with custom scales spelled correctly per `5378dea5d`), and it doubles as undo/redo: right-click any chord in the Score to revert the whole session to that point. It's both a memory and a time machine.

---

## Phase 3: SHARE

Capture gives you a frozen harmonic idea; share is where you *elaborate, decorate, and perform* it. Three broad exits:

### Tablature (make it playable by humans)

The Tablature workspace (`src/components/Workspace/Tablature/`) renders the current scale and chord across 11+ instruments — guitar (standard, drop D, open G), ukulele, mandolin, banjo, autoharp, flute fingerings, piano, and treble/bass/alto/sax staves, plus chord-reference views like the triad circle. Scale tones light up, chord tones and roots get their own colors, and each instrument can be transposed independently. This is the "here's how you actually play what you found" layer — it hands your discovered harmony to a performer on their instrument.

### MIDI out (make it drive gear and the DAW)

Two channels of output:

- **Web MIDI** (`Chords/Midi.js`, `OutputTypes.js`, `MidiOutputSettings.js`): enable MIDI, pick outputs/channels, and broadcast the harmony as any of several mappings — scale pitch classes, scale class, scale root, chord root, chord voicing, Ableton Scale-Awareness, or a video-index for triggering clips. A map/calibration flash helps you wire it to hardware.
- **Plugin events** (`Navigation.js:314-449`): the app dispatches `scaleChanged`, `chordChanged`, `availableScalesChanged`, `availableChordsChanged`, and `availablePivotModulationsChanged`, using self-contained "Harmony Payload v2" so even custom scales/chords carry their full definition. This is the "harmonic middleware" role — the Dashboard becomes the one source of truth telling every harmony-aware plugin what key you're in, even with its own UI closed.
- Plus **exports**: the Score history dumps to MIDI (`exportMidi.js`), LilyPond sheet music (`exportLilypond.js`), and PDF.

### Ensembles (make it a shared performance)

Ensembles turn a solo exploration into a group one:

- **Firebase rooms** (`Ensemble/Ensemble.js`, `RoomView/`): a host creates a room, others join by URL, and the host's scale/chord/BPM stream out via Firestore `onSnapshot`. Members' Navigators jump to follow, out-of-scale chords are guarded against, and every change is logged to their Score too.
- **Bluetooth LE** (`src/ble/`): on native iOS/Android, a host can broadcast zero-infrastructure over Bluetooth to nearby Ensemble Jammer instances, using a compact binary codec that packs scale/chord/BPM into a single ~20-byte GATT notification.

The through-line: everyone in the room is *following the harmony you discovered and arranged*, elaborating it on their own instruments in real time. The Dashboard is only the broadcast half of this; the perform-together half is a separate app, **Ensemble Jammer** (see below).

---

## Ensemble Jammer: the multiplayer face of SHARE

If the Dashboard is the host that explores and captures harmony, **Ensemble Jammer** (`/Users/soney/Github/Ensemble-Jammer`) is the client where everyone else performs it. It's the "many voices playing" endpoint of the SHARE phase — the networked instruments that turn a solo discovery into a live jam, with the host steering the key for the whole room.

### What it is

- Built as **React 19 + Vite + Tone.js**, shipping on Web, iOS, Android, and Desktop (Capacitor + Electron), currently v3.3.0.
- Shares the Dashboard's data files (`pressing_scale_dict.json`, `chords_no_supersets.json`), so both apps speak the same 57-scale language.
- **Read-only counterpart to the Dashboard's ensemble host**: the Dashboard writes scale/chord/BPM to a room; Ensemble Jammer reads it and never writes back.

### How it follows the host

It rides the same dual transport the Dashboard broadcasts on, abstracted behind a `RoomStateSource` interface (`src/state/roomStateSource.ts`) so instruments don't care where state comes from:

- **Firestore** (online): joins by room slug/ID and attaches an `onSnapshot` listener that fires the instant the host changes scale/chord/BPM (`src/firebase.ts:283-312`).
- **Bluetooth LE** (offline/nearby): connects to the host's GATT peripheral using the *exact same* service/characteristic UUIDs and binary codec as the Dashboard's `src/ble/` (`src/state/bleRoomSource.ts:10-16`). This is why they pair with zero infrastructure — nearby-device play with no internet.
- **Harmony Payload v2**: custom (non-57) scales and chords ride inline in the room document, so even a host's user-invented harmony reaches the jammers intact (`src/scale/instrumentNotes.ts:29-143`).

### What performers actually do

Each jammer picks one of ~9 scale-aware instruments — Touch Harp (20 velocity-sensitive strings), X/Y Lead (2D theremin pad), Melody Maker (16-step sequencer synced to host BPM), Tanpura Drone, Venn Instrument (tap-a-region chords), Snap Sequencer / Snaps Looper (auto-pitch-shifted samples), and Tilt / Compass (device-motion instruments). Every instrument's playable surface is **constrained to the host's current scale or chord** (`buildInstrumentNotes`, `src/scale/instrumentNotes.ts:314-337`), so a player literally cannot hit a wrong note.

### The modulation moment

The payoff is what happens when the host modulates. When the Dashboard moves from, say, C diatonic to octatonic:

1. The Firestore/BLE update fires in every connected jammer.
2. Each instrument re-computes its note list against the new scale/chord.
3. Notes **glide to the nearest valid pitch with smart voice leading** (`instrumentNotes.ts:221-272`) rather than jumping — active voices portamento instead of re-triggering, register is preserved, and the visuals recolor (harp strings remap, drone roots shift, sequencer rows re-assign).

Everyone stays together harmonically with zero synchronization effort; the Scale Navigator middleware handled it. Sound is Tone.js through a master limiter (`src/utils/audioEngine.ts`), with optional MIDI-out to a DAW (`src/utils/midiBus.ts`) so a jammer's part can drive external gear too.

### Where it sits in the loop

Explore and Capture happen on the Dashboard; Ensemble Jammer is one of the three SHARE exits (alongside tablature and MIDI/plugin middleware) — specifically the *perform-together* one. A host explores the network and arranges a Sketchpad progression, opens an ensemble room, and broadcasts; jammers join on their phones with different instruments and elaborate the harmony in real time. Then a chord suggests a pivot, the host modulates, every instrument retunes, and the group is exploring together.

---

## The loop in one breath

You **explore** by traveling the scale network (Navigator for the close-up, the 57-scale graph for the map) and browsing chords inside each scale (Chord Network + the smoothness/quality/root steering); you **capture** the states you love into Sketchpad nodes — discovered or custom — and wire them into progressions while the Score keeps the receipt; then you **share** by handing that harmony to players (tablature), machines (MIDI/plugin middleware), or a networked ensemble (Firebase/BLE) so a static discovery becomes a living performance. Then a chord suggests a pivot, and you're exploring again.

---

## The Wedge: Shared Rehearsal Room with Instant Artifact Export

The vision doesn't require an MMO, AR, or a persistent world sim to start. The smallest thing that has **never existed** and sits directly on top of what's already built is a **shared rehearsal / performance room with instant artifact export.**

The loop:

- A host drives Scale Navigator. Several people join on Ensemble Jammer instruments. *This works today.*
- Add two things: (1) the room **records** the harmonic timeline plus everyone's parts, (2) when you leave, the room **hands you an Ableton session / MIDI / sketchpad** of what just happened.

> Walk in, jam with strangers, walk out with a session you finish in your DAW.

That single loop is the entire vision in miniature — a feature, not a five-year world-build. If that moment lands, the MMO, the persistent world, and eventually AR are all just *more room around a thing that already works.* If it doesn't land, no amount of weather-changing-with-scales will save it.

**The north star that governs it:** every hour someone spends should leave them with something they can take into the rest of their musical life. Fake grind fails this test. A jam recording that exports to Ableton passes it. Keep that as the constitution and most "which feature" questions answer themselves.
