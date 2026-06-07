# A0 Adapter — French

_Status: reorganized June 2026_  
_Scope: how BasicA0 becomes FrenchA0._

FrenchA0 is mostly complete. This document is intentionally compact: it records the design decisions, current deck family, and review rules so future cleanup or new French work stays consistent.

---

# FrenchA0 Big Idea

FrenchA0 is not where the learner starts speaking French.

FrenchA0 is where French stops looking and sounding random.

By the end of FrenchA0, the learner should be comfortable seeing and hearing:

```text
é, è, à, ù, ê, â, ô, ç, œ
j’ai, l’eau, c’est
les amis, vous avez
le, la, l’, un, une
silent final letters
familiar-looking words pronounced the French way
```

A1 is where true sentence-building begins.

---

# French-Specific Learner Problems

FrenchA0 exists because French has several early obstacles that can make even simple material feel confusing:

- familiar-looking words that sound different from English
- silent final letters
- nasal vowels and unfamiliar vowel sounds
- accents and special characters
- apostrophes/elision
- liaison/linking between words
- `l’` hiding whether a noun is masculine or feminine
- gender/article pairing
- spelling that does not map cleanly to English expectations

FrenchA0 should not make learners master these systems. It should make them unsurprising.

---

# Current FrenchA0 Deck Family

The current FrenchA0 structure is the recommended model.

```text
A0.1 — Cognates: Familiar Words, French Sounds
A0.2 — Sound Gaps
A0.3.1 — é / e acute
A0.3.2 — è and ê / open e sounds
A0.3.3 — tiny accent words: a/à, ou/où, etc.
A0.3.4 — circumflex vowels
A0.3.5 — ç / cedilla
A0.3.6 — œ / joined letters
A0.4 — Elision: Apostrophes Are Normal
A0.5 — Liaison: French Links Words
A0.6 — Gender and Articles: Little Partner
```

The A0.3 split is intentional. Special sounds and symbols work better as small decks than as one large mixed accent deck.

---

# Deck Purposes

## A0.1 — Cognates

Purpose: make French feel immediately less alien.

Use familiar-looking words so the learner can focus on French sound and rhythm.

Rules:

- no article burden yet
- no gender explanation yet
- choose useful or recognizable cognates
- avoid obscure words even if they illustrate a sound
- use audio heavily
- introduce French pronunciation expectations gently

Good anchor words:

```text
action
restaurant
café
téléphone
hôtel
musique
important
simple
chocolat
```

## A0.2 — Sound Gaps

Purpose: fill important French sounds that cognates do not cover well.

Topics may include:

- `u`
- `ou`
- `oi`
- nasal vowels
- French `r`
- `j` / soft `g`
- `ch`
- silent final letters
- `eu` / `œu`
- `œ`

Include common words that will be useful again later.

## A0.3 — Accents and French Characters

Purpose: make French marks familiar, not scary.

The learner does not need to memorize every accent name. They should recognize the marks and hear examples.

Recommended microdeck pattern:

- introduce the symbol/sound
- use a few single words
- reinforce with tiny phrases
- reuse earlier words when helpful
- keep each subdeck focused

Good tiny phrase pattern:

```text
café → un café
idée → bonne idée
vérité → la vérité
œuf → un œuf
```

## A0.4 — Elision

Purpose: show that apostrophes are normal in French.

Core idea:

> French often drops a vowel before another vowel. The apostrophe shows where that happened.

Good examples:

```text
j’ai
l’eau
l’ami
c’est
n’est pas
```

Do not turn this into a full grammar lesson.

## A0.5 — Liaison

Purpose: show that French words often link in speech.

Core idea:

> Sometimes a silent final letter wakes up when the next word begins with a vowel.

Use common, high-value chunks only.

Good examples:

```text
les amis
vous avez
nous avons
deux ans
mon ami
un petit enfant
```

Avoid rare, optional, literary, or unnatural liaisons.

## A0.6 — Gender and Articles

Purpose: show that French nouns often come with a little partner word.

Learner-facing idea:

> Do not try to guess gender from English. Learn the article with the French word.

This deck may deliberately use noun/article triplets when the triplet reveals information the learner cannot see from `l’` alone.

Good pattern:

```text
idée
l’idée
une idée
```

```text
restaurant
le restaurant
un restaurant
```

```text
œuf
l’œuf
un œuf
```

Gender/article repetition is allowed when it teaches the partner-word behavior.

---

# Repetition Policy for FrenchA0

FrenchA0 uses repeated anchor words on purpose.

Examples of useful repeated anchors:

```text
café
hôtel
idée
œuf
téléphone
restaurant
```

These are not automatic bloat. They can support different jobs:

- cognate recognition
- accent/symbol learning
- silent letters
- elision
- liaison
- gender/articles
- article+noun memory

Use the BasicA0 rule:

> Reuse is encouraged when the learner has a new job to do with the word. Avoid repeating the same word in the same role.

---

# French Quick Tip Topics

Useful Quick Tip topics:

- familiar-looking words may sound different in French
- silent final letters
- `é` often has a clear “ay”-like sound
- `è` / `ê` can mark a more open e sound
- accents are not decoration
- `ç` keeps `c` soft
- `œ` appears in common words like `œuf`, `sœur`, and `cœur`
- apostrophes are normal
- French words often connect in speech
- `le` and `la` can become `l’` before vowels
- learn the article with the noun
- do not try to guess gender from English

Hint wording should be learner-facing:

Good:

```text
You should recall `restaurant` from an earlier deck.
```

Avoid:

```text
This reuses `restaurant` from the cognates deck.
```

---

# Things to Keep Out of FrenchA0

Move to A1 or later:

- full sentence-building patterns
- mini conversations
- role-play dialogues
- “I want...” practice unless formulaic and very short
- past tense practice
- conditional forms such as `je voudrais` unless used only as an isolated preview
- complex negation
- long explanation of liaison rules
- full gender rules
- accent-name memorization

A0 can contain short formulaic phrases, but it should not become A1.

---

# FrenchA0 Review Notes

The most recent FrenchA0 review found:

- total card count around 550
- no malformed rows
- no non-empty `tts_target` fields
- A0.3 microdecks ranging from 15 to 36 cards
- A0.6 gender/articles around 80+ cards with intentional repetition
- source-specific hints replaced by generic recall hints

Important decision: FrenchA0 is larger than the older target, but the size is defensible because the material is split by job and includes several microdecks.

The main remaining polish rule is not “make it smaller at all costs.” The rule is:

> Keep repetitions that create a new noticing job; remove repetitions that only repeat the same job.
