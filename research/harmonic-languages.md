# Composer NPCs & harmonic languages

Two of the MMODAW's collections — **Languages** (styles/frameworks: functional, jazz, serial, polystylist) and the **NPCs as composers** who teach them (pillars 5 and 6) — already have a working engine room: `/Users/soney/Github/harmony-tools`. It is a modular collection of harmonic idioms, voice-leading systems, and composer-specific rule-sets, built on Tymoczko's Pitch → Chord → Key/Scale → Musical-space hierarchy (the same foundation as the 57-scale network). Each idiom is a self-contained module that can be **stacked** with others (e.g. a Romanesca bass under Ravel voicings with Huron spacing), which is exactly how "collect a language, combine it with another" should feel in play.

The design fit is direct: **a harmonic language is a rule-set that transforms the player's input into a style; a composer NPC is the character who embodies that rule-set and hands it over.** Meeting the NPC doesn't unlock a locked feature — it shows you a framework you didn't know existed (pillar 6).

---

## The idiom modules (candidate NPCs)

Each `harmony-tools` subdirectory is a documented harmonic idiom, several with working Python/JS implementations. Mapped to composer-NPC archetypes:

| Idiom / module | NPC archetype | What the rule-set does | Status |
|---|---|---|---|
| `functional-harmony/` | Common-practice composer | Roman-numeral analysis, T / PD / D function classification, Bach–Haydn Markov progressions | Implemented |
| `boyd-chord-categories/` | Jazz musician | Boyd Position 1/2 system, root-movement rules, smooth voice-leading scoring, 114 voicing types | Implemented (in Dashboard) |
| `barry-harris/` | Linear chromaticist | Barry Harris chromatic scales extended to Tymoczko's 7 scale classes | Implemented |
| `messiaen/` | Modernist | 7 modes of limited transposition, modal planing, chord extraction | Spec + MIDI dataset |
| `ravel/` | Impressionist / colorist | Added-note chords, extended dominants, quartal voicings, chromatic mediants | Spec |
| `hindemith/` | Acoustic theorist | Overtone-based root-finding, 6 chord groups by tension | Spec + MIDI dataset |
| `bartok-lendvai/` | Symmetry composer | Axis systems, golden-section proportions | Spec |
| `serialism/` | Post-tonal composer | 12-tone matrix, row operations, combinatoriality | Spec |
| `polystylism/` | Style-mixer (Schnittke) | Citation, allusion, interpolation between idioms | Spec |
| `huron-voiceleading/` | (global constraint) | Perceptually optimal SATB spacing, from 10,000+ Bach/Haydn sonorities | Implemented (M4L) |
| `tymoczko/` | (global parameter) | Brightness ordering along the circle of fifths (dark ↔ bright) | Documented |

The two "global" rows are not NPCs but **world physics**: Huron spacing and Tymoczko brightness apply underneath whatever language is active, the way gravity applies regardless of biome.

---

## How a language plays

Each NPC's rule-set is a transform on player input, e.g.:

- **Functional NPC:** player melody → functional analysis → Roman-numeral labeling → chord generation, spaced by Huron rules.
- **Jazz (Boyd) NPC:** player input → scale-membership filter → Position rules → voice-leading rank.
- **Modernist (Messiaen/Bartók) NPC:** player note → quantize to mode / axis → parallel/symmetric chord → Huron spacing.
- **Serial NPC:** phrase length → choose row form (P/R/I/RI) → generate serial progression.
- **Polystylism NPC:** two languages + a blend ratio → hybrid progression that crossfades between idioms.

**Combining languages is the deep mechanic.** Because the modules stack, collecting a second language doesn't replace the first — it composes with it. The polystylism module is literally the tool for interpolating between two collected idioms, so "meet Schnittke" becomes "gain the ability to blend the languages you already hold."

---

## The progression concatenator (harmony as terrain to walk)

`progression-concatenator/` chains 690+ real MIDI progressions (Schoenberg 198, Boyd jazz 122, Reger 123, Messiaen 101, Hindemith 65, Hanson 52, …) by matching endpoint chord qualities, transposing, and linking them into arbitrarily long modulating sequences via a random walk through a transition graph. Each source is its own Markov model, so edges can be weighted toward one style or blended across several.

This is the harmonic-language analogue of LALORK's auto-conductor walking the 57-scale network (see [lalork.md](lalork.md)): a way for the world to generate stylistically-coherent harmonic journeys on its own, and a collectible library the player can chain in real time. The stated integration goal is to map each progression's chords to scale supersets and generate scale-aware concatenations — i.e. run the concatenator **through** the 57-scale network.

---

## Scale Navigator integration (already wired)

`harmony-tools` is not a separate universe; it plugs into the same substrate:

- **Barry Harris + Messiaen** inherit Tymoczko/Pressing's 7 scale classes directly.
- **`functional-harmony/FUNCTIONAL_ANALYSIS_NOTES.md`** maps tonic/dominant function onto the 57-scale network's modal layer, treating functional parsing as complementary to the voice-leading geometry.
- **Boyd chord categories** are already integrated into the Scale Navigator Dashboard's chord workspace (scale-membership filtering: all chord tones must be in the scale).
- **Brightness ordering** adds a second navigation axis (harmonic color) alongside scale proximity.

For the MMODAW this means the Languages collection and the Harmony collection share one coordinate system: a language is a set of rules for *moving through and voicing* the same harmonic space the player already explores.

---

## Key source files

- `/Users/soney/Github/harmony-tools/README.md` — constraint-stacking philosophy, Tymoczko hierarchy
- `/Users/soney/Github/harmony-tools/functional-harmony/functional_dataset_all.json` — chord → function mappings
- `/Users/soney/Github/harmony-tools/functional-harmony/FUNCTIONAL_ANALYSIS_NOTES.md` — 57-scale-network mapping
- `/Users/soney/Github/harmony-tools/boyd-chord-categories/chord_types.json` — jazz voicing types + positions
- `/Users/soney/Github/harmony-tools/barry-harris/barry_harris.py` — 7-scale-class chromatic generator
- `/Users/soney/Github/harmony-tools/messiaen/README.md` — 7 modes, planing, extraction code
- `/Users/soney/Github/harmony-tools/ravel/`, `hindemith/`, `bartok-lendvai/`, `serialism/`, `polystylism/` — idiom specs
- `/Users/soney/Github/harmony-tools/progression-concatenator/README.md` — 690+ progression graph walk
- `/Users/soney/Github/harmony-tools/huron-voiceleading/` — SATB spacing lookup
- `/Users/soney/Github/harmony-tools/tymoczko/brightness-ordering.md` — brightness spectrum
