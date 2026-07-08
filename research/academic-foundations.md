# Academic Foundations

The peer-reviewed and primary-source research beneath the MMODAW's core bets. Two threads: (1) the music-theory and math that make **harmony a navigable space** — the bedrock under Scale Navigator's 57-scale network; and (2) the HCI/NIME and learning-science research validating that **constraint frees novices, play beats theory instruction, and shared harmonic state is a sound networked-music architecture** — the bedrock under Ensemble Jammer.

Every specific mechanical bet the MMODAW makes has direct academic precedent. No prior project combines all of them.

---

## Part 1 — Harmony as a navigable space (voice-leading geometry)

The claim under Scale Navigator: harmony can be modeled as a network of "places" (scales, chords) connected by "roads" (voice leadings), through which a player moves smoothly by changing one note at a time. This is not a metaphor invented for a game — it is a decades-deep, mainstream research program.

### Tymoczko — geometric voice-leading spaces (the direct ancestor)

**"The Geometry of Musical Chords"** (*Science*, 2006) is the founding result: a chord of *n* notes is a single point in an *n*-dimensional geometric space (an orbifold), and a voice leading is a line segment whose length measures how "smooth" the motion is ([DOI: 10.1126/science.1126287](https://doi.org/10.1126/science.1126287); [open PDF](https://www.brainmusic.org/EducationalActivities/Tymoczko_chords2006.pdf)). It was the first music-theory paper *Science* ever published.

- **"Generalized Voice-Leading Spaces"** (Callender, Quinn & Tymoczko, *Science* 2008) generalized this via the **OPTIC** symmetry framework, unifying chord-spaces, scale-spaces, and whole progressions in one construction ([DOI: 10.1126/science.1153021](https://www.science.org/doi/10.1126/science.1153021)).
- **A Geometry of Music** (Oxford, 2011) is the book-length synthesis, with "hundreds of figures" mapping chord relationships as literal geometric diagrams a reader "rotates in three dimensions" ([Julian Hook's review, MTO 17.3](https://mtosmt.org/issues/mto.11.17.3/mto.11.17.3.hook.html)).
- **ChordGeometries** is Tymoczko's own free 3D software that renders chords as points and voice leadings as paths through the orbifold — shipping prior art for "software whose entire interface is a navigable map of harmony."

**What to take from it:** This is the mathematical root of the whole MMODAW premise — the first rigorous proof that "distance between chords" is a well-defined geometric quantity, not a figure of speech. It licenses treating harmony literally as terrain: places you can be, and paths of measurable length between them. That is exactly what Scale Navigator turns into a UI.

### The 57-scale network — the actual source

The 57 scales are **not arbitrary**. Tymoczko's **"Scale Networks and Debussy"** (*Journal of Music Theory* 48.2, 2004) defines the **seven "Pressing scales"** — the maximal set of scales with no consecutive semitones that preserve diatonic thirds: diatonic, acoustic, harmonic minor, harmonic major, octatonic, hexatonic, and whole-tone ([full PDF, UC Santa Cruz](https://people.ucsc.edu/~dej/migrated/Ewha%20Materials/Modes/Modes-reading/Tymoczko.Scale%20Networks%20and%20Debussy.pdf)). He credits jazz theorist **Jeff Pressing** (1978) as first discoverer.

Counting all transpositions gives exactly **57**: diatonic (12) + acoustic (12) + harmonic minor (12) + harmonic major (12) + octatonic (3) + hexatonic (4) + whole-tone (2) = **57 scales**, all connected in one network where two scales are adjacent when they share all but one pitch and that one differing note moves by a single semitone — **the exact "differ by one note" adjacency rule the MMODAW uses.**

**What to take from it:** This is a peer-reviewed map of harmonic places (57 scales) and roads (single-note voice-leading edges) — a navigable-harmony graph, decades before any game used it. It is the single most direct theoretical source for Scale Navigator's node set and adjacency rule.

### Close prior art to flag: "The Scale Navigator" (CalArts, NIME 2019)

A shipped, peer-reviewed, web-based tool — **literally called "The Scale Navigator"** — built directly on Tymoczko's scale-network concept (Turczan, Kapur, Ho, Honigman & Shepherd, [NIME 2019](https://www.nime.org/proceedings/2019/nime2019_paper020.pdf)). The selected scale sits at the center, radially surrounded by its voice-leading neighbors as clickable nodes; it broadcasts control data, MIDI, and real-time notation to an ensemble of performers and generative algorithms. It implements a 48-scale subset (the four asymmetric scale types).

**What to take from it:** A directly named, functioning precedent for both the tech name *and* Ensemble Jammer's shared-state, ensemble-synchronization use case — it validates that a visual scale-network navigator can drive a live multi-performer harmonic state. The gap it leaves is exactly where the MMODAW goes further: it is a laptop-orchestra tool for trained performers, uses the **48-scale** subset (omitting the three symmetric scales the MMODAW's **57** includes), and has no world, no collections, and no artifact-export loop.

### The deeper lineage: Tonnetz, neo-Riemannian theory, and Lewin

The "harmony as a place you travel" idea is centuries old:

- **Euler's Tonnetz (1739)**, developed by Riemann, is arguably the original "harmony as a map" diagram — Gollin documents that treating it as "a metaphorical map or landscape" is a "familiar trope" in the literature ([Oxford Handbook of Neo-Riemannian Theories](https://academic.oup.com/edited-volume/27965/chapter/211576585)).
- **Neo-Riemannian PLR transformations** (formalized by **Richard Cohn**, *JMT* 1997; synthesized in *Audacious Euphony*, Oxford 2012) are the smallest clean example of "voice leading as travel" — each of P, L, R preserves two notes of a triad and moves the third by a semitone, prefiguring the "differ by one note" rule at the triad level ([Cohn 1997 PDF](https://music.arts.uci.edu/abauer/3.1/notes/Cohn_Neo-Riemannian%20Operations97.pdf)).
- **Douthett & Steinbach's "Cube Dance"** (*JMT* 1998) is a second, independently-derived instance of the exact MMODAW structure — a graph whose nodes are chords and whose edges are single-semitone voice leadings, where **path length equals total voice-leading distance** ([JSTOR](http://www.jstor.org/stable/843877)). Douthett's later **filtered point-symmetry** explains *why* symmetric scales (octatonic, hexatonic, whole-tone) sit at hub-like junctions with many neighbors.
- **David Lewin's** *Generalized Musical Intervals and Transformations* (Yale, 1987) is the deepest root — reframing an interval as an *action/arrow* carrying one object to another, i.e. "relationship-as-motion," the most abstract version of "harmony as a place you travel and a chord change as the road you take" ([Wikipedia](https://en.wikipedia.org/wiki/Transformational_theory)).

**What to take from it:** "Harmony as navigable terrain with real distance" is a mainstream, decades-deep research program — not a novel conceit. That gives the MMODAW's core mechanic serious theoretical legitimacy and a rich literature to draw UI ideas from (hubs, distance metrics, adjacency).

### The smoothness slider is a solved optimization problem

Once chords/scales are points in a metric space, finding the smoothest move between two is a **minimum-cost matching / assignment problem** under a taxicab (L1) semitone-distance metric — the same family as the Hungarian algorithm and discrete optimal transport. Tymoczko proved a minimal crossing-free voice leading always exists and gave a **polynomial-time algorithm** ([2006 supplement](http://canonsrythmiques.free.fr/gueststars/voiceleading.pdf)); production-grade open-source implementations exist ([Harrison's `minVL`](https://github.com/pmcharrison/minVL)).

**What to take from it:** Any UI control that dials "how much voice-leading motion is allowed" between harmonic states is mathematically well-founded and efficiently computable — the MMODAW can lean on decades of established, open-source algorithms rather than inventing new math.

### Physical precedents: isomorphic keyboards & the hexany

**Isomorphic keyboards** (Wicki–Hayden, 1896; the **Harmonic Table** layout, topologically identical to the Tonnetz, shipped as the AXiS-49/64 and Lumatone) make "the shape of a musical relationship" into "a shape you move your hand through" ([Harmonic table note layout](https://en.wikipedia.org/wiki/Harmonic_table_note_layout)). Erv Wilson's **hexany** represents an entire scale as a 3D octahedron you can rotate ([Hexany](https://en.wikipedia.org/wiki/Hexany)).

**What to take from it:** These are the haptic/physical analogue of the scale network — direct precedent for "moving through harmonic space" as a bodily action, and the strongest conceptual bridge to the AR "grab and manipulate harmonic objects" endpoint (Pillar 10).

---

## Part 2 — Why the design bets work (NIME, HCI & learning science)

### Constraint frees novices: "can't hit a wrong note" is validated

The most load-bearing research for Ensemble Jammer:

- **Blaine & Fels, "Contexts of Collaborative Musical Experiences"** (NIME 2003) — the foundational study of walk-up-and-play interfaces. Its central finding: **the most common technique for an easily-learned interface is to limit the range of notes/scales any action creates**, a "proven method" for interfaces that stay "satisfying and fun." Critically, when mappings prevent wrong notes, this **"helps to minimize chaotic musical interaction" in group settings** — constraint is what makes *multiplayer* music non-cacophonous ([PDF](https://www.nime.org/proceedings/2003/nime2003_129.pdf)).
- **Chui et al., "Automated Note Selector"** (NIME 2013) — a touch instrument that removes dissonant intervals, using the pentatonic scale so "any pitch may be played in any order... without resulting in excessive dissonance," letting novices improvise "without being discouraged" ([PDF](https://www.nime.org/proceedings/2013/nime2013_130.pdf)).
- NIME 2011 work shows constraint **channels and reveals** creativity rather than suppressing it — even a single-button interface produced a wide variety of individual performance styles.

**What to take from it:** Direct, peer-reviewed validation of the exact MMODAW thesis — "constrain to scale so you can't hit a wrong note." Blaine & Fels specifically validate it for the *multiplayer* case (Pillar 9's strangers-jamming), which is the highest-risk claim.

### Play beats theory instruction: stealth learning is validated

A growing empirical literature tests gamified vs. traditional music-theory teaching:

- An Arkansas State controlled study found gamified music-theory instruction **significantly improved self-regulated motivation and competence** vs. non-gamified controls ([PDF](https://arch.astate.edu/cgi/viewcontent.cgi?article=1105&context=all-etd)).
- A Game-Based Learning piano study **"significantly improved pupils' music knowledge, overcoming baseline disparities"** vs. rote instruction ([PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC12865349/)).
- **Sonic Pi** (Sam Aaron, Cambridge) is the strongest curriculum-scale precedent — an abstract rule-based domain (programming) taught *through* musical play, now in the UK national KS3 computing curriculum, with peer-reviewed evidence it improves beginner attitudes ([FARM 2014 PDF](https://www.cs.kent.ac.uk/people/staff/dao7/publ/farm14-sonicpi.pdf); [Computers & Education 2022](https://ouci.dntb.gov.ua/en/works/408RwJp4/)).
- **Csikszentmihalyi's flow theory** applied to music warns explicitly against performance-outcome-focused teaching as "a source of psychic disorder," favoring the experiential act — and flow requires a continuously-recalibrating challenge/skill balance ([ERIC](https://eric.ed.gov/?id=EJ1277872); [Oxford Academic](https://academic.oup.com/book/12594/chapter/162457092)).

**What to take from it:** Direct empirical support for Pillar 1 (harmony discovered through play, theory framing removed) and Pillar 3 (friction only in discovery, never in creation) — flow research says *any* friction in the creative act itself breaks flow by definition.

### Shared harmonic STATE is a sound architecture (not just cheaper)

The strongest engineering validation of Pillar 8:

- **PLOrk / SLOrk** (Princeton/Stanford laptop orchestras, from 2006) built sound to render **locally, near each performer**, synchronized by **networked OSC control messages, not shared audio** — e.g. a networked conductor process emits OSC pulses so each machine synchronizes timing locally ([PLOrk ICMC 2006 PDF](https://soundlab.cs.princeton.edu/publications/plork_icmc2006.pdf); [NIME 2007](https://mcd.stanford.edu/publish/files/2007-nime-smelt.pdf)). This is the direct architectural ancestor of "exchange musical intent, render locally."
- **Chafe / CCRMA SoundWIRE** research (the JackTrip project) established the **~25ms "ensemble performance threshold"** — beyond ~25ms of raw-audio delay, musicians can't stay synchronized — achievable only with dedicated low-latency protocols and fragile over consumer internet ([Stanford News 2020](https://news.stanford.edu/stories/2020/09/jacktrip-software-allows-musicians-sync-performances-online); [arXiv QoS study](https://arxiv.org/pdf/1808.09399.pdf)).

**What to take from it:** The entire networked-music-performance field exists *because* synchronized raw audio is latency-constrained to ~25ms. Broadcasting compact harmonic-state messages (`Scale: C Lydian · Chord: IVmaj7 · Tempo: 92`) and rendering locally **sidesteps that hard ceiling entirely** — state-sync tolerances are far looser than audio-sync tolerances. PLOrk/SLOrk is a working existence-proof that state/control-message sync produces coherent live ensemble music; the MMODAW generalizes it from a research lab to a consumer product.

### The AR endpoint: Lanier's "improvising reality," now with supporting research

The MMODAW's Pillar 10 cites **Jaron Lanier's** "improvising reality" / "post-symbolic communication." His primary sources are explicit and span three decades — the interface for shared improvised reality would be **modeled on musical instruments**: "you'd play virtual musical instruments... and play the world into existence... a shared intentional waking-state dream" ([jaronlanier.com](https://www.jaronlanier.com/vrint.html); [Voices of VR #600](https://voicesofvr.com/600-jaron-laniers-journey-into-vr-dawn-of-the-new-everything/)). His cognitive rationale: improvising musicians solve harmonic/voice-leading problems "faster than conscious symbolic reasoning allows."

Contemporary AR research now supports the mechanism:

- **AudioMiXR** (2025) — a controlled study of 27 sound designers found 6DoF AR manipulation of virtual audio objects **"significantly improved usability... reduced frustration and mental workload... and enhanced creativity"** vs. a 2D baseline ([arXiv:2502.02929](https://arxiv.org/html/2502.02929v4)).
- **ARLooper**, **"Music Everywhere"** (AR improvisation learning), and NIME 2023/2025 AR-instrument studies all confirm the space is active **but explicitly not yet mainstream/solved** ([NIME 2023](https://nime.org/proceedings/2023/nime2023_17.pdf); [ARLooper NIME 2020](https://www.nime.org/proceedings/2020/nime2020_paper37.pdf)).

**What to take from it:** Primary-source grounding for Pillar 10 plus fresh evidence that (a) spatial manipulation of harmonic objects measurably beats flat interfaces, and (b) the space is genuine whitespace. The MMODAW's constrained-harmonic-state, collaboratively-improvised design is the closest realized approximation of Lanier's thought experiment that could exist today — and *more* tractable than his open-ended version, because harmony is a bounded, satisfying-by-construction (consonant) state space.

---

## Summary: foundation → MMODAW mechanic

| Academic foundation | Core contribution | MMODAW connection |
|---|---|---|
| Tymoczko, *Science* 2006 / 2008 / *A Geometry of Music* 2011 | Chords/scales as points; voice leadings as measurable segments; OPTIC unifies them | Mathematical basis for "distance between harmonic states" + the smoothness slider |
| Tymoczko, "Scale Networks and Debussy" 2004 + Pressing 1978 | The seven Pressing scales → the **57-scale** single-semitone network | Direct source of the node set and "differ by one note" adjacency rule |
| CalArts "The Scale Navigator," NIME 2019 | Shipped 48-scale visual navigator broadcasting harmony to an ensemble | Closest named precedent for the tool *and* Ensemble Jammer's shared-state model |
| Tonnetz / Cohn PLR / Douthett–Steinbach Cube Dance / Lewin GMIT | "Harmony as a navigable map" at triad level; relationship-as-motion | Historical/theoretical depth behind the core mechanic |
| Voice-leading optimization (Tymoczko; `minVL`) | Polynomial-time minimal voice leading = assignment/optimal-transport | The literal algorithm class powering the smoothness slider |
| Isomorphic keyboards / hexany | Harmonic relationships as physical shapes/solids | Haptic precedent for the AR "manipulate harmony" endpoint |
| Blaine & Fels 2003; Chui et al. 2013 | Restricting notes lowers barrier and prevents multiplayer chaos | Validates "can't hit a wrong note," including for strangers jamming |
| Sonic Pi; gamification-of-theory studies; flow theory | Play/discovery beats explicit instruction; friction breaks flow | Validates Pillar 1 (play not theory) and Pillar 3 (no friction in creation) |
| PLOrk/SLOrk; Chafe/CCRMA ~25ms EPT | State/control-message sync works; raw-audio sync is latency-bound | Validates Pillar 8 as the *only* architecture that sidesteps the latency ceiling |
| Jaron Lanier (primary sources); AudioMiXR & AR-NIME research | "Improvising reality" via instrument-like interfaces; spatial > flat for creativity | Grounds Pillar 10 and confirms it as whitespace |

**Overall:** Every specific mechanical bet has direct, peer-reviewed or primary-source precedent — scale-constraint (NIME), state-synchronized ensembles (PLOrk/SLOrk), play-before-theory (Sonic Pi), and the navigable-harmony network (Tymoczko). But no prior project combines all of them, and Lanier's instrument-as-world-generator remains, by his own repeated admission, unrealized. That combination — plus the AR endpoint — is the MMODAW's whitespace.
