# TopHatt Touch Target Implementation Prompt

## Purpose

Implement reusable UI and touch-target primitives for the TopHatt Flutter app before doing more UI work.

The goal is to enforce the app’s UI standards through shared constants and reusable widgets instead of relying on every screen to remember touch target, spacing, and accessibility rules manually.

This should improve player controls, hands-free playback controls, settings controls, and future UI work.

---

# Copilot Prompt

I want to implement reusable UI/touch-target primitives for the TopHatt Flutter app before doing more UI work.

## Context

We added UI standards requiring concrete tap target sizes and player-control ergonomics. Now I want the codebase to enforce these standards through shared constants and reusable widgets instead of relying on every screen to remember them manually.

Please inspect the existing Flutter project structure, especially:

- `theme.dart`
- `TopHattTheme`
- `AppText` helpers
- existing shared widgets
- existing player screen controls
- existing settings modal controls

Then implement this in the most idiomatic way for the current codebase.

---

# Goals

## 1. Add shared UI sizing constants

Create or update a shared constants file for UI/touch-target standards.

Suggested constants:

```dart
const double kMinTapTarget = 48.0;
const double kPlayerTapTarget = 56.0;
const double kCriticalTapTarget = 64.0;
const double kMinControlGap = 8.0;
```

Use project naming conventions if better names already exist.

Meaning:

- `kMinTapTarget`: minimum for all tappable controls.
- `kPlayerTapTarget`: preferred minimum for common player controls.
- `kCriticalTapTarget`: minimum/preferred size for pause, stop, cancel playback, or other safety-critical controls.
- `kMinControlGap`: preferred spacing between adjacent touch targets.

---

## 2. Create reusable touch-target wrappers/widgets

Create shared widgets or helpers so small icons can have large reliable hit areas.

Possible components:

```text
TopHattIconButton
TopHattPlayerControl
TopHattCriticalPlaybackButton
TopHattModeChip
```

Do not create unnecessary widgets if similar ones already exist. Prefer extending or reusing existing shared components.

Requirements:

- Visual icon may be smaller than the hit area.
- Tappable area must meet the relevant minimum size.
- Components should support semantic labels and/or tooltips.
- Components should use TopHatt theme tokens and existing typography helpers.
- Avoid hardcoded colors if theme tokens exist.
- Keep selected/highlighted states calm and accent-driven.
- Do not introduce one-off styling patterns.

---

## 3. Apply the wrappers selectively

Do not refactor the entire app blindly.

Start by applying these shared wrappers to high-impact controls:

- Player screen directional controls:
  - show
  - hide
  - next
  - previous
- Center audio/playback control.
- First-card button.
- Next/show button.
- Hands-free play/pause/stop controls if they exist.
- Player settings mode chips if they currently have small hit areas.

Make sure the actual hit area is at least:

- `48×48` for normal controls.
- `56×56` for player controls.
- `64×64` or larger for hands-free pause/stop.

---

## 4. Prepare for hands-free safety controls

Even if the full hands-free redesign comes later, make sure the new shared components can support:

- large Pause button
- Resume button
- Stop hands-free button
- icon + text if needed
- semantic labels

Hands-free playback must never depend on tiny icon-only controls.

---

## 5. Accessibility requirements

For icon-only actions:

- Add `Tooltip`, `semanticLabel`, or equivalent.
- Do not rely on color alone for state.
- Use shape, border, opacity, fill, or label changes in addition to color where practical.
- Respect text scaling where possible.
- Avoid fixed-height layouts that clip at larger accessibility font sizes.

---

## 6. Engineering requirements

Follow the project’s UI standards:

- Keep UI files focused on rendering/interactions.
- Do not add side effects inside build methods.
- Use providers/services for business logic where applicable.
- Use `theme.dart` / `TopHattTheme` extension values.
- Reuse `AppText` styles.
- Break large widgets into smaller private widgets/helpers if complexity grows.
- Preserve existing behavior unless explicitly improving touch target size or semantics.

---

# Acceptance Criteria

- Shared constants exist for minimum tap target sizes and spacing.
- At least the main player controls use shared touch-target wrappers or equivalent constraints.
- Small icons now have large enough tappable areas.
- Hands-free playback controls are prepared to use large critical controls.
- Code compiles.
- Existing player behavior remains intact.
- UI appearance remains close to current design, but touch ergonomics are improved.
- No hardcoded colors are introduced where theme tokens exist.

---

# Notes for Future UI Work

Once these primitives exist, future changes should use them instead of creating custom tap targets directly.

The next likely UI tasks are:

1. Hands-free playback safety redesign.
2. Control emphasis refactor:
   - `primary`
   - `suggested`
   - `neutral`
   - `discouraged`
3. Player controller touch-area cleanup.
4. Larger, clearer Show/Hide/Next/Previous affordances.
5. Hands-free mode turning the center control into Pause/Resume.
