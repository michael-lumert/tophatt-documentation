I would be very skeptical of “50–90 onboarding pages” as a general rule. That can work for some apps, but usually those are not 90 “look how cool we are” slides. They are often **one-question-per-screen personalization flows**: goal, level, time per day, topics, motivation, experience, reminders, etc. That can feel customized, but it can also become a tax before the user has received any value.

The better principle is:

> Don’t make onboarding long. Make it **progressive**.

NN/g’s guidance is relevant here: progressive disclosure keeps advanced or less-needed features out of the way until they matter, and long upfront tutorials can interrupt users and be forgotten. ([Nielsen Norman Group][1])

## My take for TopHatt

For your app, I would **not** build a 60-page onboarding. It clashes with the calm, practical nature of TopHatt.

I’d use a three-layer approach:

```txt
1. First-run onboarding: 5–8 screens
2. Personalization setup: 4–7 lightweight questions
3. Progressive in-app guidance: shown only when relevant
```

That gives you the benefit of “this app is adapting to me” without burying the learner before they hear their first French sentence.

There is evidence that onboarding campaigns can improve early app retention — for example, Airship data reported by EMARKETER showed higher next-day return for apps with onboarding campaigns than apps overall — but that does **not** prove that longer onboarding is automatically better. The safer reading is: onboarding helps when it gets people to value, personalization, or activation faster. ([EMARKETER][2])

## What I’d onboard in TopHatt

Your first-run flow should answer only a few questions:

```txt
What is this app?
Why sentence-first?
What is A0?
How do I practice?
What should I do first?
```

And ask only a few inputs:

```txt
Which language are you learning?
How familiar are you?
How do you usually practice?
Do you want guided path or custom decks?
Audio speed preference?
```

Then get them into the first card.

The goal should be:

> within two minutes, the learner hears useful audio and understands what to do next.

## I would delay email capture

Unless accounts are essential, I would not ask “gimme your email!” at the beginning.

Better timing:

```txt
After first deck started
After progress exists
Before syncing/backing up custom decks
Before reminders
Before switching devices
```

Copy might be:

> Save your progress and custom decks.

That is much better than:

> Create an account to continue.

For TopHatt, “custom decks” gives you a natural reason for account creation later.

## How to manage many onboarding pages

Yes, people often use configuration files — but usually in a **hybrid** way.

I would not put every screen entirely in code, and I would not make every screen pure JSON. I’d do this:

```txt
Simple explain/choice screens: JSON/config driven
Complex input screens: Flutter widgets
Flow order/branching: config driven
State/actions: typed Dart code
```

That gives you reorderability without making Flutter fight a giant dynamic form engine.

## Recommended architecture

Think in terms of **step types**, not pages.

Example step types:

```txt
info
choice
multiChoice
slider
audioSpeed
permissionPrompt
accountPrompt
deckRecommendation
firstPractice
```

A config file might describe the flow:

```json
{
  "id": "why_a0",
  "type": "info",
  "title": "Start before A1",
  "body": "A0 helps you get used to French sounds, spelling patterns, and first useful phrases.",
  "primaryAction": "Continue"
}
```

Another step:

```json
{
  "id": "practice_context",
  "type": "choice",
  "title": "How will you usually practice?",
  "options": [
    { "id": "screen_on", "label": "With the screen on" },
    { "id": "hands_free", "label": "Walking or driving" },
    { "id": "both", "label": "Both" }
  ]
}
```

Then Flutter maps `type: "choice"` to a `ChoiceStepWidget`, `type: "info"` to an `InfoStepWidget`, and so on.

## What should live in JSON/config

Good candidates:

```txt
titles
body copy
button labels
screen order
option labels
branching rules
image/animation asset references
analytics event names
skip/required flags
```

Bad candidates:

```txt
audio playback logic
account creation logic
permission handling
deck download logic
complex form validation
business rules that affect app safety
```

The config should describe the experience. Dart should own the behavior.

## Version the onboarding

This matters more than it seems.

Use something like:

```txt
onboarding_flow_version: 1
```

Then store:

```txt
completed_onboarding_version
completed_step_ids
answers
```

That lets you later add:

```txt
v2: new A0 explanation
v3: new account prompt
v4: changed practice-style selector
```

without trapping existing beta testers in repeated onboarding.

## I’d avoid one giant PageView of 90 hardcoded widgets

That will become painful fast.

Better:

```txt
OnboardingFlow
  OnboardingStep model
  OnboardingController
  OnboardingStepRenderer
  Step widgets by type
```

Conceptually:

```txt
OnboardingStepRenderer(step):
  if step.type == info -> InfoStep
  if step.type == choice -> ChoiceStep
  if step.type == audioSpeed -> AudioSpeedStep
  if step.type == firstPractice -> FirstPracticeStep
```

Later, you can reorder the flow by editing config rather than rearranging widget files.

## For TopHatt, I’d start with this onboarding

### First-run onboarding

1. **Build an ear for French**
   Short brand promise.

2. **Why sentences?**
   “Words are easier to remember when you hear them in useful phrases.”

3. **What is A0?**
   “Before A1, get comfortable with sounds, accents, articles, and first phrases.”

4. **Choose your practice style**
   Reuse your new Settings idea: See & Hear, Listen, Full Review, etc.

5. **Pick your starting path**
   Recommended: French Foundations.

6. **Try one card**
   Actually play audio.

7. **You’re ready**
   Continue to A0.1 or A0.3.1 depending on setup.

### Optional personalization

Ask these, but keep them skippable:

```txt
How much French do you know?
When will you practice?
Do you prefer guided decks or your own topics?
What topics would you like later?
```

## The “long onboarding improves retention” thing

I’d phrase it more carefully:

> Longer onboarding can improve retention when each step increases commitment, personalization, or time-to-value.
> Longer onboarding hurts when it delays the first useful experience.

Modern onboarding advice tends to emphasize personalization, progressive feature introduction, analytics, and A/B testing rather than one universal page count. ([Appcues][3])

For TopHatt, the first useful experience is probably:

> “I heard a French phrase, understood it, replayed it, and the app made sense.”

Everything before that should be minimal.

## My recommendation

Build the system as if it *could* support 50 steps, but only ship maybe **8–12 total first-run steps**, with most of the teaching moved into progressive guidance.

So the architecture is scalable, but the user experience stays calm.

That fits TopHatt much better than a giant 90-page funnel.

[1]: https://www.nngroup.com/articles/progressive-disclosure/?utm_source=chatgpt.com "Progressive Disclosure"
[2]: https://www.emarketer.com/content/mobile-app-onboarding-boosts-user-retention?utm_source=chatgpt.com "Mobile app onboarding boosts user retention"
[3]: https://www.appcues.com/blog/in-app-onboarding?utm_source=chatgpt.com "Master In-App Onboarding: Key Steps & Strategies in 2025"
