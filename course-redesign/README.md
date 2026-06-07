# Blueprint Reorganization README

This package reorganizes the uploaded blueprint drafts into a clearer ownership model.

## New files

```text
Course-Blueprint-General.md
A0-Blueprint-General.md
A0-Adapter-French.md
A0-Adapter-Norwegian.md
```

## Old → new mapping

```text
Course-Blueprint-General.md      → Course-Blueprint-General.md
A0-Blueprint--General.md         → A0-Blueprint-General.md
A0-Blueprint-French.md           → A0-Adapter-French.md
A0-Blueprint-Norwegian.md        → A0-Adapter-Norwegian.md
```

## Ownership rule

One rule, one home.

- Course-wide philosophy lives in `Course-Blueprint-General.md`.
- Universal BasicA0 rules live in `A0-Blueprint-General.md`.
- French-specific implementation lives in `A0-Adapter-French.md`.
- Norwegian-specific implementation lives in `A0-Adapter-Norwegian.md`.

Adapters should stay thinner than blueprints. They should not restate the whole course philosophy.
