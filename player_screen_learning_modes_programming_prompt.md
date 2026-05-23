# Player Screen Learning Modes — Programming Prompt

## Context

This app is a sentence-first, audio-first language learning app. The main study interface is currently called the **player screen**. It resembles an early iPod in vertical orientation: a rectangular viewscreen with a circular controller below it. In horizontal orientation, it may eventually resemble an old handheld game console, with controls split to the sides.

The current player screen is flexible but too easy to misuse. A combined **next/show** button was added for convenience, but in real study this encouraged passive consumption: the learner could advance while immediately revealing the answer, skipping the active recall or output step.

The goal of this redesign is not to remove flexibility. The goal is to make the intended learning task visible and to guide the learner toward the best next action.

The app should not be “language police.” Discouraged controls may be muted/greyed out, but they should not be disabled.

---

# Core Design Principle

Every learning mode should answer one question:

> What should the learner do before pressing Next?

The app should distinguish between:

1. **Interactive practice modes**  
   The learner is looking at the screen and pressing buttons.

2. **Hands-free playback modes**  
   The learner may have the phone in a pocket, screen off/dim, while walking, driving, or doing chores.

---

# Terminology

Avoid age-based labels like “baby mode,” “infant mode,” “teenager mode,” etc. They are useful as internal metaphors but may feel patronizing to adult learners.

Use task-based names:

- **Browse**
- **Echo**
- **Recall**
- **Listen**
- **Produce**
- **Shadow**
- **Hands-free French**
- **Hands-free Review**

Optional playful icons may still be used, but the visible names should communicate the task.

---

# Mode Architecture

The player should use a single top-level setting:

```text
Practice Mode
```

Each practice mode is a preset that configures lower-level settings automatically:

- which language appears first
- whether target/native text is hidden or shown
- whether audio autoplay is off or on
- which buttons are highlighted
- which buttons are muted
- whether the session is interactive or hands-free
- whether the screen should stay visually active or become minimal/dim

An optional **Advanced Settings** area may expose the lower-level mechanics:

- prompt side: native / target / hidden
- reveal behavior
- playback sequence
- audio speed
- shuffle/sequential
- theme
- autoplay delay
- screen wake/dim behavior

Most users should choose a practice mode, not manually combine all settings.

---

# Control Guidance Rules

Controls should have three possible visual states:

## 1. Suggested

The button is highlighted, preferably green.

Use for the next recommended action in the current mode.

## 2. Neutral

Normal visual treatment.

Use for allowed controls that are neither especially encouraged nor discouraged.

## 3. Discouraged but Available

Muted/greyed out, but still tappable.

Use for shortcuts that undermine the current learning task, especially **next/show** outside Browse mode.

Do not disable controls unless technically necessary.

---

# Core Controls

The player currently includes:

- **Hide** — hides the bottom/revealed portion of the viewscreen
- **Show** — reveals the hidden portion
- **Back** — previous card
- **Next** — next card without automatically revealing
- **Audio / Replay** — plays target audio
- **First** — go to first card
- **Next/Show** — advance to next card and reveal target/native pairing immediately

Recommended default behavior:

- **Back** and **First** should usually remain neutral.
- **Audio**, **Show**, and **Next** are highlighted depending on mode.
- **Next/Show** is strongly highlighted only in Browse mode.
- In all active recall/output modes, **Next/Show** should be muted but still available.

---

# Interactive Practice Modes

## 1. Browse

### Purpose

Low-pressure introduction to new material. The learner sees meaning and target language together, hears the target audio, and builds initial familiarity.

### Best for

- first pass through a deck
- A0/A1 new material
- tired learners
- previewing a deck
- sound/meaning orientation

### Display

- Native language visible first.
- Target language may be revealed automatically or via next/show.
- Target audio should play when the target is shown if deck settings allow.

### Learner task

- Notice the meaning.
- Listen to the target audio.
- Replay audio as needed.
- Move quickly when the card feels easy.

### Highlighted controls

- Audio / Replay
- Next/Show

### Muted controls

- None required, though Show may be less important if Next/Show is the primary flow.

### Notes

This is the only interactive mode where **Next/Show** should feel like the primary button.

---

## 2. Echo

### Purpose

Train pronunciation, sound/spelling association, and meaning recall from target text.

### Best for

- second pass through new material
- pronunciation practice
- cards where the learner can read French but needs audio confirmation

### Display

- Target language visible first.
- Native language hidden initially.

### Learner task

1. Read the target sentence aloud.
2. Press Audio to compare pronunciation.
3. Think or say the native meaning.
4. Press Show to confirm.
5. Press Next.

### Highlighted controls

Initial state:

- Audio / Replay
- Next

After audio is pressed at least once, optionally highlight:

- Show

### Muted controls

- Next/Show should be muted, because it skips the echo-and-check routine.

### Notes

The app cannot know whether the learner spoke aloud, but the UI should gently suggest the intended order.

---

## 3. Recall

### Purpose

Train active target-language production from native-language meaning.

### Best for

- strengthening known material
- A1 sentence-loop practice
- producing useful personal sentences

### Display

- Native language visible first.
- Target language hidden initially.

### Learner task

1. Read the native prompt.
2. Try to say the target sentence before revealing it.
3. Press Show.
4. Listen to target audio.
5. Press Next.

### Highlighted controls

- Show
- Audio / Replay after reveal
- Next after reveal

### Muted controls

- Next/Show should be muted because it skips recall.

### Notes

This is the main anti-passive-consumption mode.

---

## 4. Listen

### Purpose

Train listening comprehension from target audio before seeing text.

### Best for

- learners who have already seen the deck
- listening-first review
- short sentence decks
- conversation decks

### Display

- Both native and target text hidden initially, or the viewscreen shows a minimal listening prompt.
- Target audio plays on card entry or when Audio is pressed.

### Learner task

1. Hear the target audio.
2. Try to understand the meaning.
3. Optionally replay at slower speed.
4. Press Show to reveal target/native text.
5. Press Next.

### Highlighted controls

Initial state:

- Audio / Replay
- Show

After reveal:

- Audio / Replay
- Next

### Muted controls

- Next/Show should be muted because it skips the listening attempt.

### Notes

This is interactive listening practice, not hands-free playback.

---

## 5. Produce

### Purpose

Train target-language production from a meaning prompt without seeing the target text first.

### Best for

- late A1 / A2 review
- graduation tests
- personal routine decks
- high-confidence material

### Display

- Native prompt visible first, or optionally an image prompt if the deck supports images.
- Target text hidden initially.

### Learner task

1. See the meaning prompt.
2. Say the target sentence aloud.
3. Press Show.
4. Compare with target text and audio.
5. Replay audio if needed.
6. Press Next.

### Highlighted controls

- Show
- Audio / Replay after reveal
- Next after reveal

### Muted controls

- Next/Show should be muted.

### Notes

Produce and Recall are similar. The distinction is that Recall may still be a normal practice mode, while Produce is a stricter output/test mode.

---

## 6. Shadow

### Purpose

Train pronunciation, rhythm, and mouth movement by repeating along with or immediately after target audio.

### Best for

- pronunciation practice
- short sentence decks
- conversation decks
- slow-to-normal audio progression

### Display

- Target text visible.
- Native text may be hidden or available after Show.
- Audio controls should be prominent.

### Learner task

1. Listen to target audio.
2. Repeat aloud.
3. Replay at 0.50x or 0.75x if needed.
4. Replay at 1.0x.
5. Optionally reveal/check meaning.
6. Press Next.

### Highlighted controls

- Audio / Replay
- Speed controls
- Next

### Muted controls

- Next/Show may be muted unless the deck is being used as a first exposure.

### Notes

Shadow is distinct from Echo. Echo is “read then compare.” Shadow is “listen and speak with the audio.”

---

# Hands-Free Playback Modes

Hands-free modes are not normal study modes. They are automated playback sessions.

Assume:

- screen may be dark
- phone may be in pocket
- learner may be walking, driving, or doing chores
- no button interaction is expected

Consider using a simplified “Now Playing” screen rather than the full player controller.

---

## 7. Hands-free French

Formerly similar to “Listen” autoplay.

### Purpose

Continuous target-language listening.

### Best for

- repeated exposure
- conversation decks with multiple voices
- walking/driving review
- learners who want an audiobook-like experience

### Playback sequence

```text
target → target → target → ...
```

Each card plays target audio, then advances automatically.

### Display

- Screen may dim or show minimal card info.
- Full viewscreen is not essential.

### Controls

If visible:

- Pause / Play
- Replay current card
- Skip
- Speed

### Notes

This should not be confused with interactive Listen mode.

---

## 8. Hands-free Review

Formerly “Full Review.”

### Purpose

Hands-free meaning reinforcement.

### Best for

- review while walking/driving
- reinforcing target audio with native-language meaning
- learners who benefit from hearing the target again after meaning is activated

### Playback sequence

```text
target → source/native → target → delimiter → next card
```

The delimiter sound should separate cards gently.

### Display

- Screen may dim or show minimal card info.
- Full viewscreen is not essential.

### Controls

If visible:

- Pause / Play
- Replay current card
- Skip
- Speed

### Notes

This mode is genuinely useful even though it is passive. It should not be framed as inferior. It trains listening and meaning association, but not active output.

---

# Naming Changes

Replace current autoplay labels:

| Current Label | Recommended Label |
|---|---|
| Study | Manual |
| Listen | Hands-free French |
| Full Review | Hands-free Review |
| Passive Mode | Hands-free Mode |

Avoid the word “passive” in the UI. It can sound like the learner is doing something lazy or wrong.

---

# Suggested Practice Mode List

The main selector may show:

```text
Browse
Echo
Recall
Listen
Produce
Shadow
Hands-free French
Hands-free Review
```

Possible grouping:

```text
Interactive
- Browse
- Echo
- Recall
- Listen
- Produce
- Shadow

Hands-free
- French only
- Full review
```

---

# Example Preset Table

| Mode | First prompt | Audio behavior | Reveal behavior | Primary controls |
|---|---|---|---|---|
| Browse | Native text | Target audio on reveal | Target shown quickly | Audio, Next/Show |
| Echo | Target text | Manual target replay | Native hidden until Show | Audio, Show, Next |
| Recall | Native text | Audio after reveal | Target hidden until Show | Show, Audio, Next |
| Listen | Target audio | Manual or on entry | Text hidden until Show | Audio, Show, Next |
| Produce | Native text or image | Audio after reveal | Target hidden until Show | Show, Audio, Next |
| Shadow | Target text | Replay-focused | Native optional | Audio, Speed, Next |
| Hands-free French | None / minimal | Target autoplay | No interaction expected | Pause, Replay, Skip |
| Hands-free Review | None / minimal | Target → Native → Target | No interaction expected | Pause, Replay, Skip |

---

# Recommended State Fields

A possible state model:

```dart
enum PracticeMode {
  browse,
  echo,
  recall,
  listen,
  produce,
  shadow,
  handsFreeFrench,
  handsFreeReview,
}

enum PromptType {
  nativeText,
  targetText,
  targetAudio,
  nativeAudio,
  image,
  hidden,
}

enum PlaybackMode {
  manual,
  targetOnlyAuto,
  targetNativeTargetAuto,
}

enum ControlEmphasis {
  suggested,
  neutral,
  discouraged,
}
```

A mode preset could define:

```dart
class PracticeModePreset {
  final PracticeMode mode;
  final String label;
  final String shortInstruction;
  final PromptType initialPrompt;
  final PlaybackMode playbackMode;
  final bool autoReveal;
  final bool showNativeFirst;
  final bool showTargetFirst;
  final bool hideBothInitially;
  final bool isHandsFree;
  final Map<PlayerControl, ControlEmphasis> initialControlEmphasis;
}
```

This is only a conceptual model. Adapt it to the existing Flutter architecture.

---

# Suggested Mode Instructions

Use short persistent instructions on the player screen.

## Browse

```text
Look, listen, and move quickly.
```

## Echo

```text
Read the French aloud. Press audio. Then check the meaning.
```

## Recall

```text
Say the French before you reveal it.
```

## Listen

```text
Listen first. Try to understand before showing the text.
```

## Produce

```text
Make the French sentence before you reveal it.
```

## Shadow

```text
Repeat with the audio. Slow it down if needed.
```

## Hands-free French

```text
French audio will play continuously.
```

## Hands-free Review

```text
French, English, then French again.
```

---

# UI Design Direction

Prefer a restrained, Dieter Rams-like approach:

- fewer visible explanations
- one clear task sentence
- one highlighted next action
- quiet secondary controls
- discouraged shortcuts muted but available
- mode badge or mode strip instead of large tutorials

A possible mode strip:

```text
Recall · Say the French before you reveal it.
```

A possible deck-start coaching card:

```text
This pass: Echo
Read the French aloud, press audio, then show the meaning.
```

After a few cards, reduce the coaching to a small badge.

---

# Recommended Visual Elements

## Mode Badge

Persistent but small:

```text
Echo
Read French aloud → Audio → Show
```

## Control Highlighting

Use green/highlight color for the suggested next action.

Examples:

- Browse: highlight Next/Show and Audio.
- Echo: highlight Audio first, then Show.
- Recall: highlight Show, then Audio after reveal.
- Listen: highlight Audio, then Show.
- Hands-free modes: show play/pause and minimal transport controls.

## Muted Shortcut

In all active modes except Browse, mute Next/Show.

The button remains tappable, but visually communicates:

> This is available, but it skips the intended practice.

---

# Deck-Level Recommendations

A deck may recommend a sequence of modes:

```text
First pass: Browse
Second pass: Echo
Third pass: Recall
Optional: Listen or Shadow
Later review: Hands-free Review
```

The app can suggest mode progression without forcing it.

Examples:

## New beginner deck

```text
Browse → Echo → Recall
```

## Pronunciation-heavy deck

```text
Browse → Shadow → Echo
```

## Conversation deck

```text
Browse → Listen → Shadow → Hands-free French
```

## Personal routine deck

```text
Browse → Recall → Produce → Hands-free Review
```

---

# Custom Deck Builder Connection

For user-created personal decks, the app should encourage useful daily sentences:

```text
I don’t want to get up.
I’m going to make coffee.
I’m taking the dogs for a walk.
I need to work.
I’m tired.
I’m going home.
```

These decks should work especially well with:

- Browse
- Echo
- Recall
- Produce
- Hands-free Review

The app may guide users to create 5–10 sentences they could actually say today.

---

# Implementation Priorities

## Phase 1

Implement the mode selector and control highlighting.

Required modes:

- Browse
- Echo
- Recall
- Hands-free French
- Hands-free Review

## Phase 2

Add additional interactive modes:

- Listen
- Shadow
- Produce

## Phase 3

Add deck-level recommendations:

- suggested first pass
- suggested second pass
- suggested review mode

## Phase 4

Add coaching:

- short mode instructions
- first-three-card guidance
- optional advanced settings drawer

---

# Most Important Requirement

The app should not merely show what buttons can be pressed.

It should clearly show what kind of learning is supposed to happen.

Every mode must make the learner’s task obvious before they press Next.
