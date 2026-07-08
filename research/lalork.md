# LALORK — the MMODAW, offline

**MMODAW is LALORK online.** LALORK (the LA Laptop Orchestra) is a public music ritual: for two hours, a room full of strangers explores a changing harmonic landscape together. There is no stage; everyone plays at once. It already runs the MMODAW's core loop in a physical room, on the same tech — Scale Navigator and Ensemble Jammer — so it is the closest working proof of the design, and its hard-won practical knowledge (how people join, how a room stays coherent, why ensembles collapse) transfers almost directly to the online world.

Its one-line vision is **"share harmony."** That is the MMODAW's pillar 8 ("shared harmonic state, not shared audio") stated as a social goal rather than an architecture.

Source repos: `/Users/soney/Github/lalork` (strategy, philosophy, event design, research) and `/Users/soney/Github/lalork-website` (the participant portal and shared-state backend).

---

## What LALORK proves for the MMODAW

- **Shared harmonic state works, live.** The room holds one harmonic state (scale, chord, tempo); every client renders it locally. This is exactly the MMODAW sync model, already load-bearing in front of real audiences.
- **Everyone plays, no stage.** "Somehow a room full of strangers were making music together" is the frozen success metric. It is the wedge (pillar 9) minus the DAW export.
- **Mass convergence is the emotional center.** The peak moment is everyone joining one harmonic state at once — the online analogue of pillar 5's "collective harmonic gravity."
- **Onboarding is the real problem, not features.** LALORK's bottleneck is people in rooms, and its research is largely about how a newcomer understands where to go within ten seconds. The MMODAW inherits this: the friction is discovery and joining, never creation (pillar 3).

---

## Shared-state architecture (the sync answer, in production)

The `lalork-website` participant portal (`enter.lalaptoporchestra.com/{roomId}`) is a live reference implementation of client-side rendering:

- A Firestore **room document** holds the shared harmonic state: `{ scaleData, chordData, bpm }`.
- Clients are **read-only** subscribers. Snapshot listeners push state changes to every participant; each client turns the state into sound or notation locally.
- The portal offers modes that map cleanly onto MMODAW "instruments" (pillar's Instruments collection): **READ** (live notation / tablature for your instrument), **MIDI** (route the room's harmony into your own DAW or synth), **PLAY / JAM** (play along in the browser via Ensemble Jammer), and **CODE** (live-coding via Strudel).
- The onboarding line — "You have entered the harmonic field" — is the join ritual the online world needs.

The lesson for the MMODAW: the multiplayer substrate is a tiny synchronized harmonic-state document plus local rendering, exactly as pillar 8 claims, and it is cheap enough to already be running on Vercel + Firestore.

### Auto-conductor (a world that plays itself)

An auto-conductor process random-walks the 57-scale network: it steps between adjacent scales, picks pivot chords and the smoothest voice-leading (root circular distance plus chord-type match), and writes the new state to Firebase every 20–60 seconds. This is the MMODAW's "world with its own harmonic weather" — a solo player is never in a dead room, and it doubles as an NPC conductor when no human is steering.

### Anticipation / lookahead

Clients run a client-side lookahead so players can prepare for a change before it lands: presets range from Rehearsal (2000 ms) through Relaxed, Standard, Quick, to Expert (300 ms), with an idle → preview → commit state machine. This is the mechanic that turns "following shared state" into something playable rather than reactive — directly relevant to the Rehearse phase and to accessibility for newcomers.

### Harmonic logger → the Share bridge

A harmonic logger writes timestamped `TIMECODE | SCALE | CHORD | BPM` records of a session, with a standing TODO to convert those logs into skeleton / sketchpad JSON for Ableton. That conversion **is** the Share → Rehearse → Export bridge in the loop: a live exploration becomes a score becomes a DAW artifact. The MMODAW should treat the session log as the raw material a score is minted from.

### Roadmap features that are already MMODAW mechanics

The `lalork-website` issues read like an MMODAW feature list: **WATCH** (3D harmonic network view), **PROMPT** (a live direction banner — the conductor's instruction to the room), **SCORE** (repertoire sight-reading), **CONDUCT** (scheduled conductor slots), **RHYTHM** (a shared pulse), **DRAW** (contour → notation cells).

---

## Score → Rehearse → Perform looks back to the Scratch Orchestra

LALORK's practice is grounded in a lineage the MMODAW should claim explicitly: the score as a **prompt for a room** rather than fixed notation, realized collectively and differently every time.

- **Cornelius Cardew & the Scratch Orchestra.** Cardew's *Scratch Music* (152 improvisation rites, 1972) and *The Great Learning* are the direct ancestor of a harmony-guided score that structures listening and interaction instead of dictating notes. LALORK's improvisation playbook builds an exercise directly on *The Great Learning* Paragraph 7 (a listening chain where each pitch is chosen from a sound still ringing in the room, so silence is the selection mechanism). Cardew's later *Stockhausen Serves Imperialism* (1974) documents the Scratch Orchestra's collapse from the inside — a failure-mode reference for any large open ensemble, online or off.
- **The philosophical frame:** Alphonso Lingis, *The Community of Those Who Have Nothing in Common* — a room bound not by shared taste but by the shared act. This is the MMO's promise: strangers who cohere through play.
- **Adjacent open-form lineage** the playbook and bibliography draw on: Riley's *In C* (shared modules, players choose when to advance), Reich's phasing, Oliveros' Deep Listening (respond only to what you hear), Zorn's *Cobra* (cues govern transitions, content is free), Butch Morris's Conduction (a hand-signal vocabulary — Sustain / Repeat / Memory — for real-time composition), and Rzewski's "if you get lost, stay lost." Cage's *Musicircus* (100+ musicians, simultaneous, no conductor) is the most direct precedent for the no-stage room.

For the MMODAW, this lineage supplies both the pedigree and the concrete mechanics for the open Rehearse / Perform phases: conduction cues become in-game gestures, *In C*–style module choice becomes a low-friction way for newcomers to contribute, and the Cardew principle keeps improvisation coherent without teaching theory (pillar 1).

---

## The improvisation playbook (constraint as a mechanic)

`lalork/improvisation_playbook.md` is 17 constraint-based improv exercises, each framed as *Question → Miniature (30–60s) → Mechanic* and grounded in a real score or study. Its thesis is the MMODAW's whole approach to onboarding harmony: **experts do not invent from nothing; they work from a referent** (Pressing's referent model), and constraint is what makes a good take possible rather than the enemy of one. Neuroscience backs the payoff: skilled improvisers deactivate the self-monitoring prefrontal cortex (Limb & Braun 2008) — the flow state the game is trying to induce.

Each exercise is a ready-made game mode / tutorial:

- **#16 Guide-Tone Field** — a slow-moving 3-note field players anchor to; the playbook itself calls it "essentially a live Scale Navigator patch." This is the single clearest bridge between the improv pedagogy and the 57-scale network.
- **#8 The Great Learning Para 7** — silence-as-selection (Cardew, above).
- **#6 In C for two** — modular drift over a shared pulse (maps to RHYTHM).
- **#12 Conduction** — one player steers with three cues (maps to PROMPT / CONDUCT).
- **#14 Respond Only** — pure reactivity (Oliveros); a constraint that makes a shape self-organize.

---

## Onboarding & scene-formation research (how the world stays alive)

LALORK's research folder is effectively the MMODAW's live-ops and world-design manual:

- **Onboarding frameworks** (`lalork/research/ONBOARDING_FRAMEWORKS.md`) — escape room, museum, Sacred Harp choir, improv theater as models for getting a stranger playing fast. Directly applicable to the MMO's first-session flow.
- **Scene formation** (`lalork/research/research_scene_formation.md`) — how Dublab, Low End Theory, TOPLAP, PLOrk/SLOrk, Deep Listening, and Unsound built durable communities. The MMODAW needs the same: a world is a scene, not just a server.
- **Failure modes** (bibliography thread) — why ensembles collapse: over-practicing kills the magic; "45 minutes of noise and nobody felt like anything happened" (beginning-middle-end is non-negotiable); a 60/40 listening-to-playing ratio. These are balance constraints for multiplayer sessions.
- **The busking pivot** (`lalork/busking/BUSKING_PIVOT.md`) — "no wrong notes" because a human holds the harmonic field open; the autoharp as Scale Navigator made physical; an observable transformation with a visual center. The MMODAW's version: the world (or an NPC conductor) holds the field so a newcomer literally cannot play a wrong note.

---

## What to carry into the MMODAW

| LALORK (offline) | MMODAW (online) |
|---|---|
| One room, one shared harmonic state | Firestore-style room doc, client-side render (pillar 8) |
| "You have entered the harmonic field" | The join ritual / first-session onboarding |
| Auto-conductor walking the 57-scale network | A world with harmonic weather; NPC conductor |
| Anticipation lookahead presets | Rehearse-phase playability + difficulty scaling |
| Harmonic logger → Ableton sketchpad JSON | Session log → **score** → Export (the loop's spine) |
| Portal modes READ / MIDI / PLAY / CODE | Instruments collection (pillar 5) |
| Scratch Orchestra / Conduction / *In C* | Open Rehearse & Perform mechanics |
| Improvisation playbook (17 constraints) | Tutorials / game modes for learning harmony by play |
| Scene-formation & failure-mode research | Live-ops, session balance, community design |

---

## Key source files

- `/Users/soney/Github/lalork/README.md` — vision ("share harmony"), frozen principles, event design
- `/Users/soney/Github/lalork/improvisation_playbook.md` — 17 sourced constraint exercises + full bibliography
- `/Users/soney/Github/lalork/research/ONBOARDING_FRAMEWORKS.md` — join-flow models
- `/Users/soney/Github/lalork/research/research_scene_formation.md` — how scenes form and last
- `/Users/soney/Github/lalork/busking/BUSKING_PIVOT.md` — "no wrong notes," field-holding
- `/Users/soney/Github/lalork-website/README.md` — portal architecture, modes, roadmap
- `/Users/soney/Github/lalork-website/research/BIBLIOGRAPHY_OVERVIEW.md` — Cardew / Scratch Orchestra lineage, conducting tradition, ritual thread
