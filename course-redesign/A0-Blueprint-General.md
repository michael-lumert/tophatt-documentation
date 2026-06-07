# A0 Blueprint — General

_Status: reorganized June 2026_  
_Scope: BasicA0 rules that should apply across languages._

This document owns the universal A0 design. It should not contain French-only or Norwegian-only implementation details except as brief examples. Language-specific decisions belong in adapter documents.

---

# Big Idea

A0 is not where the learner starts “speaking the language.”

A0 is where the language stops feeling completely strange.

The goal is to make the sound system, writing behavior, high-frequency chunks, and basic app habits feel familiar before the main sentence-building course begins.

A0 should feel like this:

> “I do not speak the language yet, but it no longer looks or sounds random.”

A0 is an orientation layer. A1 is the first true sentence-building level.

---

# What BasicA0 Is For

By the end of BasicA0, learners should:

- recognize common sounds and rhythm
- recognize important writing-system behaviors
- understand a small set of high-frequency words and chunks
- hear familiar words inside short phrases
- understand that words may behave differently when placed together
- know how to use slow audio, replay, and passive listening
- feel ready to begin sentence-building in A1

A0 should build comfort, not fluency.

---

# What BasicA0 Is Not For

A0 should not try to teach full sentence-building.

Avoid making A0 responsible for:

- full conversation practice
- role-play dialogues
- broad grammar coverage
- tense systems
- long explanations
- learner production
- memorizing tables
- mastering pronunciation rules
- completing a miniature version of the whole course

The learner may see short phrases and occasional tiny sentences, but only when they support the A0 goals.

---

# A0 Deck Size Rules

The old “minimum 40-card deck” rule does not work for sound and symbol learning. Some sounds are easy and some are hard. A large mixed deck can make the hard sound harder to isolate.

Use these ranges as design guidance, not hard rules:

| Deck Type | Working Range | Notes |
|---|---:|---|
| Micro sound/symbol deck | 12–20 cards | For one small writing or sound issue |
| Focused sound/symbol deck | 20–40 cards | For a family of closely related issues |
| Normal focused foundation deck | 40–70 cards | Standard A0 foundation topic |
| Standard foundation deck | 70–90 cards | Broader but still controlled |
| Large bootstrapping deck | 90–125 cards | Allowed for broad confidence or high-value article/gender repetition |

A0 may contain several small decks instead of fewer large decks. This is especially useful when the learner needs to repeat one difficult sound or symbol without dragging easier material along.

---

# Card Construction Rules

## 1. Prefer short phrases over isolated words

Single-word cards are allowed for sound bootstrapping, but most new memorable words should quickly appear in a tiny phrase.

Good phrase types:

```text
hot coffee
blue sky
Mother’s Day
my phone
this year
here and there
```

Language-specific examples:

```text
un café
bonne idée
le bébé
en bil
et hus
den blå bilen
```

Single words are often harder to remember because they float without context. Tiny phrases give the learner a sound, a meaning, and a retrieval hook.

## 2. Reuse earlier words when the learner has a new job

Reusing earlier words is encouraged when the learner is noticing something new.

Good reuse:

- same word in a new sound context
- same word with an article
- same word inside an elision/linking pattern
- same word inside a tiny phrase
- same word used to contrast two similar spellings or sounds

Bad reuse:

- same word repeated in the same role with no new learning job
- repeated anchor words that crowd out more useful material

Soft cap: ordinary anchor words should usually stay around 6–8 appearances. A teaching workhorse may appear more often if every appearance has a distinct purpose.

## 3. Keep grammar load low

A0 cards should not combine several new burdens at once.

Avoid cards that introduce:

- a new word
- a new sound/spelling issue
- a new grammar pattern
- an idiom
- a long sentence

all at the same time.

## 4. Use familiar material to teach unfamiliar behavior

When introducing a new feature, use familiar words whenever possible.

Example:

```text
café → un café → le café
```

This lets the learner focus on the new job instead of decoding everything from scratch.

---

# Repetition Rule

A0 depends on repetition, but repetition should be purposeful.

Guideline:

> Reusing an earlier word is encouraged when the learner has a new job to do with it. Avoid repeating the same word in the same role.

When reviewing duplicates, ask:

1. What new job does this repeat perform?
2. Is the learner hearing or noticing something different?
3. Could a new word do the same job without adding too much burden?
4. Has this anchor word become useful familiarity or distracting clutter?

---

# Language-Specific Module Model

BasicA0 should not force every language into the same deck pattern. Instead, each language gets a small adapter that selects from possible modules.

Possible A0 modules:

- familiar words / cognates
- sound gaps
- special letters or symbols
- spelling-sound orientation
- stress and rhythm
- silent letters
- elision or contraction
- word linking
- articles/gender
- case exposure
- definite/indefinite forms
- word-order preview
- politeness/formality
- high-frequency function words
- app usage through hints

French does not define A0 for every language. French is one implementation of BasicA0.

---

# Quick Tip Rules

Quick Tips should be:

- short
- reassuring
- directly connected to the current card
- audio-focused when possible
- not grammar-heavy
- easy to ignore if the learner already understands

Good:

```text
The apostrophe is normal. French often drops a vowel before another vowel.
```

Good:

```text
You should recall this word from an earlier deck.
```

Avoid:

```text
This reuses `restaurant` from the cognates deck.
```

The learner does not need to know internal deck names. Reference earlier material generically.

---

# App Usage Inside A0

A0 should teach the app through lightweight hints, not a large app manual.

Useful hint topics:

- replay the target audio
- slow the audio to `0.75x` or `0.50x`
- try normal speed after slow speed
- use passive listening after first exposure
- double-tap for definitions/examples if the app supports it
- set up a keyboard for special characters when needed

A0 should normalize replay. Repeating one clear sound several times is useful.

---

# Word Count and Sentence Count

`word_count` and `sentence_count` are useful but crude.

They can show:

- whether a deck has drifted too large
- whether A0 is becoming A1
- whether one word is doing too much work
- whether too many items appear only once
- whether a deck has enough repetition to teach a sound

They should not be treated as strict pass/fail metrics.

A0 may intentionally have:

- repeated anchor words
- single-word cards
- tiny phrases that are not full sentences
- short microdecks

---

# BasicA0 Exit Criteria

A learner is ready for A1 when the language no longer feels random.

They do not need to:

- produce original sentences
- hold a conversation
- explain grammar
- master pronunciation
- know every rule behind what they heard

They should be ready to begin sentence-building with less friction.

A language adapter should define concrete exit criteria for that language.

---

# Authoring Checklist

Before finalizing an A0 deck, check:

- Is the deck’s purpose clear?
- Is the deck small enough for its sound/symbol job?
- Are single words followed by tiny phrases when memory would benefit?
- Are repeated words doing new work?
- Are hints learner-facing rather than internal-author notes?
- Are long cards formulaic enough to justify staying in A0?
- Are difficult cards pushed to A1 when they become sentence-building practice?
- Does the deck make the language feel less random?
