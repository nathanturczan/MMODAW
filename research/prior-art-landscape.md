# Prior Art Landscape

A wide survey of games, tools, and platforms that overlap with the MMODAW — single-player music-making games, multiplayer/social music worlds, and VR/AR + DAW-collaboration tools — and what to take from each. This extends [prior-art.md](prior-art.md) (which covers *IV-V-I* and other harmony games) with the full competitive field.

The lens throughout is the MMODAW loop (Explore → Capture → Craft → Rehearse → Perform → Share) and the ten design pillars — especially **Pillar 2** (tool fully unlocked, world adds richness only), **Pillar 4** (the artifact-export north star), and **Pillar 8** (shared harmonic *state*, not shared audio).

---

## The one-paragraph verdict

Across ~80 products spanning three decades, **nothing combines all of the MMODAW's core bets**: a fully-unlocked tool wrapped in a richness-only progression world, a genuine MIDI/DAW-session export loop, and shared *harmonic state* multiplayer. Individual bets each have strong precedent — Ableton's Learning Synths proves the export loop, PatchWorld proves multiplayer VR jamming into a DAW, Fortnite Patchwork proves "can't hit a wrong note" at massive scale — but no one has assembled them, and the single most defensible finding is that **no networked music tool in history transmits symbolic harmonic state instead of audio.** That architecture is genuinely unclaimed.

---

## Closest siblings, ranked

| Rank | Product | Category | Why it's the closest | The gap it leaves |
|---|---|---|---|---|
| 1 | **Ableton Learning Music / Learning Synths** | Single-player toy | Free, no-theory browser tool that **exports a real Ableton Live Set** — the north-star mechanic, shipping today | No world, no NPCs, no progression, no multiplayer |
| 2 | **PatchWorld / PatchXR** | Multiplayer VR | Multiplayer VR jamming + MIDI/OSC/Ableton Link into real DAWs; "feeds, doesn't replace" the DAW | No harmonic-constraint layer; demands synthesis skill; no song-arrangement Workbench |
| 3 | **Audiotool / Nexus** | Multiplayer DAW | Browser multiplayer-DAW-by-design, open SDK, AI co-creation, a hackathon "Games" track | Project-state sync (not harmonic-state); no world/VR/collections |
| 4 | **Sentris** | Single-player | Same stated mission ("unlock innate musical creativity" via play, not theory); promised WAV export | Small scope, no shared state, no living world |
| 5 | **Fract OSC** | Single-player | Best tool/world split — a puzzle world unlocks a full free-play synth studio with WAV export | Audio-only export, no multiplayer, no collections |
| 6 | **Endlesss** (defunct) | Multiplayer | The only shipped product combining live jamming **and** export | Shut down May 2024 — the cautionary tale (no retention/world layer) |
| 7 | **Loom (1990)** | Single-player | Direct ancestor of the "differ by one note" magic system | No export; note-gating is power-gating, not richness |

---

## 1. Single-player music-making games (Track A)

### Ableton "Learning Music" & "Learning Synths"

Free interactive browser courses from Ableton that gamify music-theory and synthesis fundamentals with click-to-toggle pattern blocks and drag-based synth exploration.

- **The single strongest precedent found anywhere:** as of an April 2022 update, Learning Synths **exports browser-made patches and sequences directly as an Ableton Live Set**, and Learning Music lets you "export the music you make... as an Ableton Live Set to develop it further" ([Ableton blog](https://www.ableton.com/en/blog/new-in-learning-synths-export-to-live-record-your-creations-and-more/); [Sonic Bloom](https://sonicbloom.net/two-interactive-websites-by-ableton-learning-music-learning-synths/)).
- **What to take from it:** This is the industry's own version of the MMODAW north star — a free, playful, no-theory tool built by a DAW vendor explicitly to feed its own DAW. It proves the export loop works today, at zero price. The MMODAW's differentiation must therefore be *the game/world/collections layer wrapped around* a proven export mechanic — not the export mechanic itself.

### Sentris

Solo designer **Samantha Kalman** (Timbre Interactive), Kickstarted in 2013 ($56,361), released 2015. Players drop colored "Sound Blocks" into rotating loops to hit puzzle targets; an original, player-authored song emerges from their choices ([Wikipedia](https://en.wikipedia.org/wiki/Sentris); [PC Gamer](https://www.pcgamer.com/sentris-a-rhythm-puzzle-music-game-minus-the-plastic-instruments/)).

- Kalman's mission — "to unlock everybody's innate musical creativity through game mechanics" — is nearly identical to the MMODAW thesis. Puzzle mode plus **Performance and Remix modes** is an explicit tool/world split, and the Kickstarter promised **WAV export**.
- **What to take from it:** The closest single-developer philosophical sibling found. Same "no wrong notes" constraint, same "play not theory" mission, same export ambition. Its niche commercial footprint underlines that mission alone isn't enough — the world/retention layer matters.

### Fract OSC

Montreal studio **Phosfiend Systems**, released 2014. A Myst-like 3D world built from modular-synth machinery; roughly half is environmental puzzle-solving, half is manipulating in-world synth consoles to unlock a free-play mode ([Wikipedia](https://en.wikipedia.org/wiki/Fract_OSC); [New Music USA](https://newmusicusa.org/nmbx/games-played-fract-osc/)).

- **The closest precedent to Pillar 2:** completing the puzzle-adventure world opens a dedicated free-play Sound Editor that works as a standalone modular synth/sequencer, with **WAV export**. Progression unlocks a full creative tool, not content.
- **What to take from it:** Proof that "a world gates access to a fully-unlocked creative tool" carries an acclaimed game. Gap: audio-only export (no MIDI/session), no multiplayer, no collections or NPCs-as-composers.

### Loom (1990)

**LucasArts**, designed by **Brian Moriarty**. The protagonist has no inventory and no text commands — every interaction is a 4-note "draft" (spell) played on a magical staff. Drafts reverse by playing backward; available notes expand (starting with just C-D-E) as the story progresses ([Lucasfilm retrospective](https://www.lucasfilm.com/news/lucasfilm-games-rewind-loom/)).

- **What to take from it:** The direct spiritual ancestor of Scale Navigator's "differ by one note" adjacency principle — an entire acclaimed game built around single-note transformations of motifs as the mechanism for change in the world. Moriarty's planned tonal-magic sequels were never made — the "franchise built on tonal magic" is itself whitespace.

### The "can't-hit-a-wrong-note" cluster

A recurring trick appears across many toys, always via a hardcoded scale/key or opaque ML — never an explicit navigable harmonic network:

- **Mixolumia** (2020) — a falling-block puzzler where clearing blocks in the correct key plays a generative, harmonically-consistent soundtrack ([davemakes](https://www.davemakes.com/project/mixolumia)).
- **Blob Opera** (2020, Google) — drag four singing blobs; an ML model keeps the four voices harmonically plausible ([Google Arts & Culture](https://artsandculture.google.com/experiment/blob-opera/AAHWrq360NcGbw?hl=en)).
- **Chrome Music Lab — Song Maker** (Google) — grid sequencer with scale presets (pentatonic to guarantee "no wrong notes"), shareable via URL, no DAW export ([Chrome Music Lab](https://musiclab.chromeexperiments.com/)).
- **What to take from it:** These validate that constraint-guarantees-good-music delights users, but all hardcode a scale or hide it in ML. **Nobody pairs the trick with an explicit, named theory of harmonic adjacency** the way Scale Navigator's Tymoczko-derived network does — that is the differentiation.

### Export-native generative tools (power-user end)

- **Orca** (hundredrabbits) — a 2D grid live-coding language with no built-in synth; entire output is **MIDI/OSC/UDP** to external gear ([esolangs.org](https://esolangs.org/wiki/Orca)).
- **Nodal** (Monash) — node-graph generative sequencer, **MIDI export core to its design** ([nodalmusic.com](https://nodalmusic.com/)).
- **Strudel / TidalCycles** (Alex McLean, Felix Roos) — browser/Haskell live-coding pattern languages, MIDI/OSC out ([tidalcycles.org](https://tidalcycles.org)).
- **What to take from it:** The purest "feeds existing tools, never replaces them" architecture in the whole survey — but all require learning code/pattern syntax, the exact opposite of the MMODAW's "remove the theory/technical framing" pillar. They show what frictionless *export* looks like; they are the anti-model for *accessibility*.

### Ephemeral-by-design toys (the anti-Pillar-4)

**Electroplankton** (Toshio Iwai, 2005) and **Patatap** (Jono Brandel × Lullatone, 2014) both deliberately refuse a save/export feature — Iwai wouldn't add saving because "the software would become more like a tool." Pure, celebrated, ephemeral play.

- **What to take from it:** The values-opposite of the MMODAW's export north star — proof that "no artifact by design" is a legitimate, even revered choice, and precisely the road the MMODAW is *not* taking. Useful as a clarifying contrast for why the export loop is a deliberate stance, not a default.

### Correctly-excluded adjacents (note-matching / scripted performance)

Rez, Child of Eden, Lumines, Sayonara Wild Hearts, The Artful Escape, Wandersong, Everhood, Melatonin, and various osu!-style rulesets all appear in "music game" discourse but are **note-matching or scripted performance**, not composition. They're useful negative controls confirming where the "music-making as the verb" line sits — with The Artful Escape's legacy-vs-self, NPC-composer framing being thematically resonant despite the mechanical mismatch.

---

## 2. Multiplayer & MMO-adjacent music worlds (Track B)

### Audiotool / Nexus

A browser-based multiplayer DAW, multiplayer "by design" since ~2009, that in **January 2026** launched **Nexus** — branded "the first open developer platform for collaborative music production." By May 2026 it reported 300,000+ MAU across 200+ countries, 10M tracks, and a "Let's Build!" hackathon with sponsor credits from OpenAI, ElevenLabs, and others ([Yahoo Finance](https://finance.yahoo.com/news/audiotool-launches-multiplayer-cloud-daw-170000346.html); [Sonicstate](https://sonicstate.com/news/2026/05/11/music-software-creation-for-all-/)).

- Nexus gives read/write API access to a live multiplayer DAW project — developers and AI agents can act as "players" inside a shared session. Its hackathon even includes a **"Games — gamified approaches to making, experiencing, and learning music"** track ([developer.audiotool.com](https://developer.audiotool.com)).
- **What to take from it:** The single most important company to watch — it is building the exact "Workbench" layer and gesturing at the MMODAW's genre-blend. But it is **project-state sync (a Google Doc for a DAW), not harmonic-state sync**, and has no World, no VR/AR, no collections. It's a Workbench with no Rehearsal or Venue — leaving the MMODAW's differentiation intact, for now.

### Endlesss (2018–2024, defunct)

Tim Exile's real-time collaborative looping/jamming app. Reached 100,000+ users and a funded round, then pivoted to a Web3/NFT/token layer in late 2021, and **shut down May 31, 2024** ([CDM](https://cdm.link/endlesss-discontinued/); [Forbes](https://www.forbes.com/sites/alisoncoleman/2021/10/17/the-tech-that-connects-music-makers-all-over-the-world/)).

- **What to take from it:** The best historical proof that "jam with strangers → walk away with an artifact" has real demand — and the clearest cautionary tale. It transmitted **audio, not state** (limiting session size and geography), never separated tool from world, and diluted its core loop with speculative token mechanics. Its death is direct market evidence that the MMODAW's world/collections/NPC layer (Pillars 2, 5, 6) is commercially load-bearing for retention, not just flavor.

### BandLab, Splice, Soundtrap, Korg Gadget

The surviving social music sandboxes. **BandLab** passed 100M users by 2024 with "forkable" remixable tracks; **Splice** (~$500M valuation) built a sample marketplace + cloud collaboration; **Soundtrap** and **Korg Gadget** offer real-time co-editing ([Music Business Worldwide](https://www.musicbusinessworldwide.com/music-making-app-bandlab-surpasses-100-million-users/)).

- **What to take from it:** They validate Pillar 4 as the correct call — every survivor treats the session as a feeder into a real, keepable file. But none have a "world" at all; they're tools with social layers. The MMODAW's "world adds richness only" pillar has no analog here.

### Rhythm/music games with real multiplayer creation

- **Fuser** (Harmonix) — multiplayer DJ/mixing gameplay with **zero durable export**; when Epic shut it down (Dec 2022), years of user mixes vanished ([Wikipedia](https://en.wikipedia.org/wiki/Fuser_(video_game))). **The sharpest negative case study for Pillar 4.**
- **Fortnite Festival / Patchwork** — up to 4 players combine loops live; the LEGO/Patchwork sequencer makes wrong notes structurally impossible ([Epic docs](https://dev.epicgames.com/documentation/en-us/fortnite/build-your-own-lego-music-concert-in-fortnite-creative)). **The closest existing analog to Pillar 1 — a major platform validating the exact "no wrong notes" teaching mechanic at massive scale.**
- **Dreams** (Media Molecule) — a full music-creation suite whose **multiplayer was planned but cancelled and never shipped** ([Wikipedia](https://en.wikipedia.org/wiki/Dreams_(video_game))).
- **What to take from it:** Fuser proves a multiplayer music game without export is hostage to the publisher's lifespan. Fortnite proves the "can't hit a wrong note" mechanic scales. Dreams proves even a first-party studio couldn't ship multiplayer music creation.

### The proven-demand negative space: virtual-world concerts

Roblox and Fortnite concerts draw enormous crowds — a Bruno Mars Roblox concert hit a record **12.8M concurrent users** (Jan 2026); Travis Scott and the Fortnite "Remix Finale" drew 12–14M+ ([Music Business Worldwide](https://www.musicbusinessworldwide.com/bruno-mars-pulls-record-12-8m-concurrent-users-to-roblox-concert/)). Meanwhile social-VR music platforms **High Fidelity** and **Wave/TheWaveVR** shut down or pivoted away from VR.

- **What to take from it:** Overwhelming demand exists for "many people + music + virtual world" — but every example is passive spectacle, never collaborative creation. **Nobody has connected the "12 million showed up" phenomenon to an actual multiplayer creation loop.** That's the Venue pillar's opportunity — and the VR-first failures warn that a browser/2D core should anchor any VR/AR ambition.

### The vaporware gap

A dedicated search for cancelled or vaporware "music-making MMO" projects **returned no clean hits** ([Wikipedia vaporware list](https://en.wikipedia.org/wiki/List_of_vaporware)).

- **What to take from it:** The category hasn't been tried and abandoned — it appears genuinely unattempted at the genre level. That lowers "this was already proven not to work" risk and raises the value of being the first mover to frame the category correctly.

---

## 3. VR/AR music tools & real-time DAW collaboration (Track C)

### PatchWorld / PatchXR — the nearest competitor

A "social playground for playing and creating music, worlds, and games in VR and PC," on Quest since July 2022. Users build custom instruments from ~200 modular blocks and jam together live; explicitly supports **MIDI, OSC, and Ableton Link** into real DAWs. Founded 2020 by Eduardo Fouilloux and Mélodie Mousset; lean/bootstrapped funding profile ([XRMust](https://xrmust.com/xrmagazine/patchworld-user-case-music/); [CDM](https://cdm.link/patchworld-multiplayer-vr-music-integrates-with-ableton-live/)).

- Described by its community as deliberately *not* trying to replace Ableton or FL Studio — the world feeds real DAWs, closely matching Pillar 4 philosophy.
- **What to take from it:** The closest living relative to the Rehearsal-VR space — it has solved multiplayer VR jamming + real DAW export. But it has **no harmonic-constraint system, no "can't hit a wrong note," and demands real synthesis literacy**, cutting against Pillar 1. The genuine whitespace is combining PatchWorld's proven jam+export with the MMODAW's harmonically-guided accessibility layer.

### EXA: The Infinite Instrument & Virtuoso VR

- **EXA** (Aesthetic Interactive) pairs genuine **MIDI/WAV export** with **real multiplayer jamming** (added Jan 2019) — arguably the fullest-featured single title in the VR survey, closest to a Workbench+Rehearsal combo ([UploadVR](https://www.uploadvr.com/exa-band-music-make-vr-multiplayer/)).
- **Virtuoso VR** offers real MIDI/WAV export plus Ableton Link sync, but is **single-player only** ([Road to VR](https://www.roadtovr.com/virtuoso-review/)).
- **What to take from it:** Between them they prove every ingredient (multiplayer, export, Link sync) is technically mature — but never with a harmonic-constraint layer, and never all at once with accessibility.

### Ableton Link — the closest real "shared-state protocol"

Ableton's open protocol synchronizes **tempo, beat, and phase** across apps/devices with no master clock — it doesn't sync audio, it syncs a small set of musical facts and lets each client render locally ([used by PatchWorld and Virtuoso](https://cdm.link/patchworld-multiplayer-vr-music-integrates-with-ableton-live/)).

- **What to take from it:** Structurally identical *in spirit* to Pillar 8 — proof the "shared state, not shared audio" architecture is sound and industry-accepted. The key difference: Link carries only tempo/beat/phase, never scale/key/chord. **Ensemble Jammer would be a superset of Link nobody has shipped** — a natural, technically plausible extension.

### Ohm Studio — the architectural warning

A real-time collaborative DAW that tried to synchronize the *audio-producing state itself* live across editors, and failed commercially — the canonical example of how hard shared-audio-state collaboration is.

- **What to take from it:** The single most important negative precedent for Pillar 8. Ohm Studio tried exactly the "shared audio" approach the MMODAW rejects in favor of broadcasting musical intent and rendering locally. Its failure validates the MMO-style shared-state architecture as the more tractable path.

### The AR endpoint — essentially unclaimed

Beyond Jaron Lanier's conceptual writings (the cited source for Pillar 10's "improvising reality") and narrow mixed-reality overlays like Paradiddle's passthrough drum kit, **no product manipulates harmonic/musical material as spatial "clay" in AR** ([see academic-foundations.md §7 for the research literature](academic-foundations.md)).

- **What to take from it:** The clearest whitespace in the entire competitive survey. Prior VR-first social-music attempts mostly failed or pivoted, which argues the AR endpoint should be the *endpoint of a creation pipeline* anchored by a strong browser core — not a standalone destination.

---

## Cross-cutting whitespace: the ten pillars vs. the field

| Pillar | Best prior-art approximation | Verdict |
|---|---|---|
| 1. Music-making as the verb | Fortnite Patchwork (no wrong notes, at scale); Sentris; Fract OSC | Validated in pieces, never as a standalone game built on the premise |
| 2. Tool vs. world separation | Fract OSC (world unlocks a full free-play tool) | Closest single match; no product pairs an unlocked tool with a *richness-only* progression world |
| 3. Friction only in discovery | Frictionless toys (Patatap, Chrome Music Lab) | No product distinguishes friction by loop stage this way — whitespace |
| 4. Artifact export (north star) | Ableton Learning Synths (→ Live Set); PatchWorld/EXA/Virtuoso (MIDI); BandLab/Splice | Strongest validation category — and its **absence correlates with product death** (Fuser, Dreams) |
| 5. Four collections (Harmony/Instruments/Performers/Languages) | Splice's gated sample/plugin model | Whitespace — Splice's model is transactional, the opposite of "collecting is inspiration, not permission" |
| 6. NPCs as composers | IV-V-I's composer style cards (see prior-art.md) | Whitespace across every product surveyed |
| 7. Solo = already rehearsal | None (products split solo vs. multiplayer modes) | Whitespace |
| 8. Shared harmonic state, not audio | Ableton Link (tempo/beat/phase only); PLOrk OSC-sync | **Clearest, most defensible whitespace — no one transmits symbolic harmonic state** |
| 9. The wedge (walk in, jam, walk out with a session) | Endlesss (before it died); EXA | Proven demand, proven failure mode to avoid (don't dilute the loop, do add retention) |
| 10. AR "improvising reality" | Jaron Lanier's writings; Paradiddle MR overlay | Whitespace — no one manipulates harmony as AR "clay" |

### Bottom line for MMODAW strategy

1. **The shared-harmonic-state architecture (Pillar 8) is genuinely novel** — no competitor, past or present, transmits symbolic musical intent instead of audio/project-state. Highest defensibility, highest execution risk (unproven at scale).
2. **The artifact-export obsession (Pillar 4) is empirically correct** — it is the clearest through-line separating survivors (BandLab, Splice, Audiotool, Ableton) from the dead (Fuser, Dreams, Wave, High Fidelity).
3. **Watch Audiotool/Nexus and BeatConnect** — they are building the Workbench layer and already reaching for game/world framing, though neither has a world, VR/AR, or harmonic-state architecture yet.
4. **Differentiation is the assembly, not any single part.** Every ingredient exists somewhere; nobody has combined a fully-unlocked, harmony-guided tool + a richness-only world + genuine DAW export + shared harmonic state. That combination is the moat.
