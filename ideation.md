# Vision

Scale Navigator's core loop already resembles a game.

```text
Explore → Discover → Capture → Craft → Perform → Share
```

The goal is to make harmony something players learn through exploration rather than theory.

The game is not about learning music theory. It's about making music through exploration, then taking what you made into the real world.

**The central premise:** unlike most creative games, the artifacts produced by play have value *outside* the game. Minecraft produces buildings, Factorio produces factories, Kerbal produces spacecraft — this produces songs people actually want to finish. Players leave with songs they can rehearse, perform, release, or continue producing in a DAW.

---

# Tool vs World (the core separation)

A game needs progression. A creative tool needs immediate access. These are different goals — don't merge them into one interface.

- **Music Tool** — everything unlocked. No XP, no grinding, no gated features. Sit down and explore harmony, capture ideas, export MIDI, rehearse, perform, right away. Like Blender or Ableton.
- **World** — progression exists, but never by locking features. The world gradually becomes richer: you discover places, characters, instruments, motifs, performances, collaborators. Minecraft never locks your ability to build; it just gives you more materials. Collecting is inspiration, not permission — finding a strange instrument gives you a new way to express ideas, not "congratulations, you may now use reverb."

```text
Music Tool
    ↑
Game World
```

The world continuously feeds the tool; the tool never requires the world. Spend five minutes, stumble on a progression, hit Export, and leave — or spend all evening rehearsing with friends.

---

# MMO DAW (the umbrella)

A persistent online world where the other directions become mechanics. One product, three spaces:

- **Workbench** — craft songs together
- **Rehearsal (VR)** — jam with friends like Guitar Hero; orchestrate and delegate who plays what
- **Venue (VR/AR)** — perform live

Artifacts leave the game as songs, MIDI, Ableton sessions, stems, and performances.

Journey, creature collecting, and farming (below) are mechanics that live inside this world, not competing directions.

## Solo vs Multiplayer

- **Solo loop = collect + craft.** Chords and motifs are creatures to collect / ingredients to gather, crafted into songs.
- **Multiplayer loop = rehearse + rearrange + perform.** Not composing from scratch — collaboratively realizing a composition you already made.

Three parallel collections run through both loops: **Harmony** (what you play), **Instruments** (how you play it), **Performers** (who plays). A song is the intersection of all three.

## Client-Side Rendering (the sync answer)

Collaborative DAWs sound like a synchronization nightmare. The trick: **render the music client-side.** Players don't exchange audio, they exchange **musical intent** — a tiny message like `Scale: C Lydian · Chord: IVmaj7 · Tempo: 92 · Beat: 41`. Each client turns that into sound locally, so sync hiccups are absorbed into the rendering — the player just experiences the music. Synchronized harmonic state is minuscule next to synchronized audio, so it scales. This is a **multiplayer musical simulation**, closer to how games work than to jamming over Zoom. (Ensemble Jammer already works this way.)

---

# Mechanics Inside the World

## Journey / Exploration ⭐⭐⭐⭐⭐
- scales become places
- chords become discoveries
- sketchpad becomes travel journal

## Creature Collector ⭐⭐⭐⭐☆
- the creatures aren't motifs — they're musicians, each with preferences (loves drones, only plays bass, refuses diminished)
- recruit them into your ensemble
- single-player is already rehearsal; in multiplayer, humans just replace the AI performers

## Cozy Farming ⭐⭐⭐⭐☆
- cultivate harmonic seeds
- grow scales/chords
- harvest ideas

---

# Key Mechanics Worth Prototyping

- **Rehearsal** — the most novel mechanic. Most music games jump straight from composing to performing; this inserts an entire collaborative phase between them, playable like Guitar Hero: assign parts, try arrangements, swap instruments, practice difficult transitions, decide who carries melody, decide who improvises. Almost a management game. Turns a solo arrangement into an ensemble.

```text
Explore → Compose → Rehearse → Perform
```

- **Instruments as collectibles** — a diversity of instrument interfaces (Guitar Hero → Rock Band, but way more). The twist: the instrument interfaces themselves are creatures to collect or recipes to craft. Progression and variety come from *how* you play, not just what you play.
- **Pivot-as-portal** — a chord shared by two scales is a hidden passage between regions. Gates exploration, gives "aha" moments, needs zero theory.
- **Collective harmonic gravity** — where players gather nudges the world's harmony. Ecological, not a vote.

---

# Existing Assets

Already built:
- Scale Navigator
- Ensemble Jammer
- Multiplayer synchronization
- Real-time harmonic retuning
- DAW export

Missing:
- game world
- progression / economy
- persistence

---

# Long-term Vision

Desktop → Multiplayer → Game → AR

Ultimately the interface becomes spatial — harmony becomes something players manipulate directly.
