# A0 Adapter — Norwegian

_Status: planning draft, June 2026_  
_Scope: how BasicA0 should become NorwegianA0._

NorwegianA0 should not be a translation of FrenchA0. It should use the same BasicA0 method while solving Norwegian-specific beginner problems.

---

# NorwegianA0 Big Idea

NorwegianA0 is not where the learner starts speaking Norwegian fluently.

NorwegianA0 is where Norwegian stops feeling slippery.

By the end of NorwegianA0, the learner should feel comfortable seeing and hearing:

```text
å, ø, æ
jeg, ikke, og, det
common friendly words
short article+noun phrases
definite endings like bilen and huset
tiny chunks like jeg er, det er, jeg har, har du
simple Norwegian rhythm
```

A1 is where real sentence-building begins.

---

# Norwegian-Specific Learner Problems

Norwegian has different A0 problems from French.

Likely early obstacles:

- the letters `å`, `ø`, and `æ`
- vowel length and vowel quality
- familiar Germanic-looking words that still sound Norwegian
- common words whose pronunciation surprises English speakers: `jeg`, `det`, `og`, `ikke`
- article/gender exposure: `en`, `ei`, `et`
- definite suffixes: `en bil` → `bilen`, `et hus` → `huset`
- word order/rhythm, especially tiny V2 exposure
- dialect variation and TTS expectations

NorwegianA0 should make these features familiar without turning them into grammar lessons.

---

# Recommended NorwegianA0 Deck Family

This is a draft sequence, not final content.

```text
A0.1 — Friendly Words, Norwegian Sounds
A0.2 — Norwegian Letters: å, ø, æ
A0.3 — Sound Gaps and Listening Anchors
A0.4 — Articles and Definite Endings
A0.5 — Tiny Useful Chunks
A0.6 — Norwegian Rhythm Preview
```

The sequence may change after one or two decks are written and tested.

---

# Deck Purposes

## A0.1 — Friendly Words, Norwegian Sounds

Purpose: build confidence through familiar or semi-familiar words while teaching Norwegian sound.

Possible anchor words:

```text
bank
film
problem
hotell
kaffe
telefon
musikk
restaurant
student
familie
```

Rules:

- focus on sound and recognition
- use visually familiar words when possible
- avoid heavy grammar
- follow single words with tiny phrases when useful
- do not over-promise that Norwegian pronunciation is obvious from spelling

Possible phrase pattern:

```text
kaffe → varm kaffe
hotell → et hotell
telefon → min telefon
```

## A0.2 — Norwegian Letters: å, ø, æ

Purpose: make the three visually distinctive letters normal.

Possible examples:

```text
år
nå
blå
brød
søster
øl
vær
her
lærer
```

Rules:

- split into microdecks if one letter needs more work
- use short phrases quickly
- focus on hearing and recognition
- avoid a long phonetics explanation

## A0.3 — Sound Gaps and Listening Anchors

Purpose: introduce common Norwegian words and sounds that an English speaker may mishear or misread.

Possible anchors:

```text
jeg
det
og
ikke
hva
hvor
her
der
ja
nei
takk
```

Possible sound topics:

- `jeg`
- `ikke`
- `og`
- `kj` / `skj` if appropriate for the chosen standard
- vowel length
- unstressed words in common chunks

This deck should stay practical. Do not over-teach dialect variation.

## A0.4 — Articles and Definite Endings

Purpose: introduce the idea that Norwegian nouns have article words and definite endings.

Learner-facing idea:

> In Norwegian, “the” often appears as a small ending on the noun.

Possible patterns:

```text
bil
en bil
bilen

hus
et hus
huset

bok
ei bok
boka
```

For a broad learner course, decide whether to teach `ei` actively at A0 or mention that many speakers use `en` for feminine nouns. Keep the first implementation consistent.

## A0.5 — Tiny Useful Chunks

Purpose: give learners useful, memorable micro-phrases before sentence-building begins.

Possible chunks:

```text
jeg er
det er
jeg har
har du
jeg vil
kan jeg
her er
takk skal du ha
ha det
```

These are not grammar drills. They are listening and recognition anchors.

## A0.6 — Norwegian Rhythm Preview

Purpose: give a small preview of Norwegian sentence rhythm and word order without teaching a word-order lesson.

Possible examples:

```text
I dag er jeg hjemme.
Nå har jeg tid.
Her er boka.
Der er bilen.
```

This deck should be short and cautious. If it starts becoming sentence-building practice, move that material to A1.

---

# Norwegian Repetition Policy

Use familiar words repeatedly when they serve different jobs.

Example with `bil`:

```text
bil
en bil
bilen
her er bilen
```

That is useful repetition because each card adds a new noticing job.

Avoid repeating the same noun in the same phrase pattern too many times when another high-value noun could do the same work.

---

# Norwegian Quick Tip Topics

Likely Quick Tip topics:

- `å`, `ø`, and `æ` are separate letters, not decorated versions of English letters
- Norwegian has short and long vowel contrasts
- some very common words do not sound how English speakers expect
- `en`, `ei`, and `et` are small article words
- “the” can appear as an ending: `bil` → `bilen`
- word order may look surprising after time words like `i dag` and `nå`
- dialects vary; copy the course audio for now

Keep these as noticing tips, not grammar lessons.

---

# Things to Keep Out of NorwegianA0

Move to A1 or later:

- full V2 word-order instruction
- broad verb conjugation explanations
- tense practice
- long dialogues
- dialect comparisons beyond a brief reassurance
- full gender system explanation
- complex noun phrase rules
- long sentence-building drills

NorwegianA0 should orient the learner. A1 should build sentences.

---

# Open Decisions Before Writing NorwegianA0

These should be decided during the first deck-writing pass:

1. Which written standard is the course using? Bokmål is the likely default.
2. How much `ei` should appear at A0?
3. Which TTS voice/accent will define the course audio model?
4. Should `å`, `ø`, and `æ` be one deck or separate microdecks?
5. How early should tiny V2 examples appear?
6. Which English-friendly words are useful enough to become Norwegian anchor words?

Do not resolve every theoretical question before writing. Write one or two small decks, test them, and update this adapter based on what breaks.
