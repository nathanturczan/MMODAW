# Vision

Scale Navigator's core loop already resembles a game.

```text
Explore → Capture → Craft → Share → Rehearse → Perform → Export
```

Share is the social bridge: what you craft solo becomes a score you hand to other players, who arrange, rehearse, and perform it with you. Export is the north star: the artifact leaves as MIDI, an Ableton session, stems, or a recording.

The goal is to make harmony something players learn through exploration rather than theory.

The game is not about learning music theory. It's about making music through exploration, then taking what you made into the real world.

**The central premise:** unlike most creative games, the artifacts produced by play have value *outside* the game. Minecraft produces buildings, Factorio produces factories, Kerbal produces spacecraft — this produces songs people actually want to finish. Players leave with songs they can rehearse, perform, release, or continue producing in a DAW.

---

# The Ten Design Pillars

The commitments that define the MMODAW, and the analysis lens the [research/](research/) uses. The rest of this doc elaborates them; the research tests each against the academic literature and the competitive field.

1. **Music-making is the verb, not note-matching.** Harmony is discovered through play, not taught — remove the music-theory framing entirely.
2. **Tool vs. world separation.** The creative tool is fully unlocked (no gating); the world adds progression only by getting richer — more places, characters, instruments — never by locking features. Collecting is inspiration, not permission.
3. **Friction only in discovery, never in creation.** Exploring, traveling, and meeting NPCs can have friction; playing, recording, rehearsing, performing, and exporting never do.
4. **The artifact-export loop (the north star).** Every session leaves the player something usable in real life — a MIDI file, an Ableton session, stems, a jam recording, a bandmate. The song isn't the goal; the song is the artifact left behind by play. The game feeds existing DAWs, never replaces them.
5. **Four collections.** Harmony (scales, chords, motifs, progressions), Instruments (interfaces and ways to play), Performers (musicians — AI or human), and Languages (styles/frameworks — common-practice, jazz, serialism, polystylism — gathered from NPC composers).
6. **NPCs as composers.** Characters embody a harmonic language and change how you craft (prior art: IV-V-I's composer-named "style cards").
7. **Solo = already rehearsal.** In single-player you assign parts to recruited AI musicians; multiplayer just swaps humans into the same chairs — no mode switch.
8. **Shared harmonic state, not shared audio.** Clients exchange musical intent (`Scale: C Lydian · Chord: IVmaj7 · Tempo: 92`) and render locally — an MMO architecture, far cheaper than synced audio, and the strongest whitespace with zero prior art.
9. **The wedge (the MVP).** A shared rehearsal/performance room with instant artifact export: walk in, jam with strangers, walk out with an Ableton session.
10. **The endpoint: AR — "improvising reality."** Manipulating harmonic objects like clay in space (Jaron Lanier).

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

## Friction is only allowed in discovery

The single design rule, almost a constitution: **only exploration should have friction; creation never does.** You don't earn the right to play piano — you discover music.

- **Friction allowed** — traveling the world, exploring regions, meeting NPCs, discovering stories, finding motifs, finding instruments, finding collaborators.
- **No friction** — playing, recording, rearranging, rehearsing, performing, exporting, using any instrument you already know.

Even the allowed friction is optional: **Scale Navigator is fast travel.** Don't want to walk through the forest? Open the map and jump straight to any harmonic state, like a teleport in an RPG. New players wander; experienced players teleport — which makes Scale Navigator an in-universe artifact you discover: a world map, an atlas, a teleport spell.

This is the difference between **progression** and **discovery**. Progression says "you aren't allowed to use this yet" (restrictive). Discovery says "you didn't know this existed" (magical). Optimize entirely around the second. The game never hides musical possibility — it only contextualizes it: know the harmony you want and get there instantly; don't, and the world helps you find it.

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
- **Multiplayer loop = rehearse + rearrange + perform.** Collaboratively realizing a composition you already made, rather than composing from scratch.

**Scores are the bridge.** What you craft solo becomes a **score**: a shareable artifact carrying the harmony, the structure, and optional arrangements / orchestrations. A score works at two resolutions at once — a **live screen score** that scrolls the moment-to-moment harmony players read as they play, and an **architectural / formal diagram** of the whole piece: its sections, who does what when, the plan for the room. Sharing a score is what pulls other players in, and it is the handoff from the solo loop into the multiplayer loop: they take the score, arrange it, rehearse it, and perform it together.

**Rehearse and Perform stay open.** A score is a starting point rather than a cage, and a group can hold it as tightly or as loosely as they like: play the chart note-for-note, or treat it as a launch pad and improvise the whole set. Exploration, rewriting, and re-orchestration continue through rehearsal and performance, so players can leave the written material, improvise, and weave back in, the way King Gizzard & the Lizard Wizard or Phish thread jams through composed songs. Prewritten structure and live exploration coexist, and the world's harmony-guided constraints keep the improvisation coherent even when players wander off the page. Perform is naturally a spectator event: a set is a stream, so Twitch and similar platforms are a first-class output — an audience watches a room of players realize a score live.

**Lineage: the Scratch Orchestra.** Score → rehearse → perform looks back to Cornelius Cardew and the Scratch Orchestra: a score is a prompt for a room rather than fixed notation, realized collectively and differently every time. Cardew's *Scratch Music* (152 improvisation rites, 1972) and *The Great Learning* treat the written material as a shared constraint that structures listening and interaction, which is exactly what a harmony-guided score does here. This is the direct ancestor of the MMODAW's collaborative Rehearse / Perform phases, and LALORK is where it already runs in a physical room (see [research/lalork.md](research/lalork.md)).

Parallel collections run through both loops: **Harmony** (what you play), **Instruments** (how you play it), **Performers** (who plays), and **Languages** (the style/framework you craft within — functional, jazz, serial, polystylist). A song is where they intersect. The Languages and the composer NPCs who teach them already have a working engine in `harmony-tools` (see [research/harmonic-languages.md](research/harmonic-languages.md)).

## Social layer

The out-of-band coordination a band actually needs — voice, chat, planning — belongs to the world too, and Discord is the obvious first home rather than something to rebuild. A room's voice and text sit alongside its harmonic state; scores, forms, and plans post into a channel the way a setlist or chart gets passed around. Both score resolutions travel here: the live screen score for playing from, and the architectural / formal diagram for deciding what happens when and who carries which section. This is also where a session's exported artifact lands — the MIDI, the Ableton session, the stream link — so the group's chatter, its plans, and its output share one place.

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
- **NPCs as composers** — characters contextualize possibility instead of gating it. A Mozart who offers ideas, history, and a style; Alfred Schnittke in a cave who teaches polystylism. Meeting them doesn't unlock a locked feature — it shows you a framework you didn't know existed. This is how the world *contextualizes* rather than *hides* music.
- **Harmonic languages as collectibles** — styles are frameworks for crafting, gathered from the composers you meet (functional, jazz, serial, polystylist). A fourth collection alongside Harmony, Instruments, and Performers. (Prior art: IV-V-I's composer "style cards" already change the rules of play — see [research/prior-art.md](research/prior-art.md).)
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
