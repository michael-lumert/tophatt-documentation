I would **not** start with a self-test mode as the gate. That feels too heavy for the kind of app you’re building.

I’d use a hybrid model:

> The app recommends when to move on, but the learner can always decide.

The key distinction is this:

> A deck is not “mastered.”
> A deck is “ready to move past.”

That phrasing matters a lot for your app philosophy. These early decks are exposure/familiarity decks, not certification exams.

## My recommendation

For now, define a deck as **ready** when the learner has reached the end of it at least once in either Practice or Listen.

Then show a gentle prompt:

```txt
You reached the end of this deck.

Move to the next deck?
[Keep practicing]   [Mark ready]
```

If they tap **Mark ready**, the Path highlight moves down.

If they tap **Keep practicing**, it stays where it is.

That gives you useful structure without pretending the app knows whether they have truly learned `é`, `è`, `ç`, etc.

## I would avoid “Done”

I’d avoid labeling decks as:

```txt
Done
Mastered
Completed
Passed
```

Those words create pressure and invite arguments with reality. A learner can finish A0.3.1 and still forget `é` tomorrow. That’s normal.

Better labels:

```txt
Started
In progress
Ready
Review anytime
```

Or:

```txt
Not started
Current
Ready to continue
Reviewed
```

On the Path page, the current highlighted card could say:

```txt
NEXT UP
```

After reaching the end, it could say:

```txt
READY
```

or:

```txt
READY TO CONTINUE
```

Then the next deck becomes `NEXT UP`.

## Suggested Path behavior

I’d make all decks tappable and available. Do **not** lock the path.

The Path is guidance, not a prison.

### State 1: not started

```txt
A0.2: Sound Gaps
79 cards
Practice   Listen
```

### State 2: current / next up

```txt
NEXT UP
A0.1: Cognates
Card 14 of 122
Practice   Listen
```

### State 3: reached end but not marked ready

```txt
READY?
A0.1: Cognates
You reached the end.
Keep practicing   Mark ready
```

### State 4: ready / moved past

```txt
✓
A0.1: Cognates
Reviewed once
Practice   Listen
```

That is enough to move the highlight without making the learner feel tested.

## What counts as “reached the end”?

For your app, I’d count any of these:

```txt
Practice reaches final card
Listen reaches final card
Full Review reaches final card
```

If the learner jumps around manually, don’t overthink it yet. A simple version is fine:

> If the current card index reaches the last card, the deck becomes “reached end.”

Later, you can track more precisely:

```txt
cardsSeenCount
cardsHeardCount
practiceCompletedOnce
listenCompletedOnce
fullReviewCompletedOnce
manuallyMarkedReady
```

But for now, “reached final card” is probably enough.

## Should there be a self-test mode?

Eventually, maybe. But I would not make it part of A0 path advancement yet.

A self-test mode makes more sense later for things like:

* Can I recognize the phrase from audio?
* Can I recall the meaning?
* Can I choose the right article?
* Can I distinguish `é` vs `è`?

But for your current A0 foundations, testing could easily become counterproductive. The goal is to build familiarity, not create failure moments.

If you do add one later, I’d call it something gentle:

```txt
Check Yourself
Quick Check
Try Recall
```

Not:

```txt
Test
Exam
Pass
Fail
```

And it should never be required to move on.

## The important product rule

I’d make Path advancement work like this:

> TopHatt suggests the next deck based on progress, but the learner controls readiness.

That gives the app enough intelligence to be helpful, while avoiding the arrogance of “you are done now.”

## Minimal implementation version

For a first implementation, I’d add only three per-deck fields:

```txt
lastCardIndex
reachedEndOnce
markedReady
```

Then:

* `NEXT UP` = first deck where `markedReady == false`
* When user reaches final card, set `reachedEndOnce = true`
* If `reachedEndOnce == true`, show a gentle “Mark ready” option
* When user marks ready, set `markedReady = true`
* Path highlight moves to the next unready deck

That is simple, understandable, and easy to test.

## My ideal wording

When a learner finishes a deck:

```txt
Nice work — you reached the end of this deck.

You do not need to master everything before moving on. You can continue to the next deck and come back anytime.

[Keep practicing]   [Move to next deck]
```

That fits TopHatt very well: calm, honest, and learner-controlled.

So my answer is: **do not gate progress with a self-test right now.** Let the app detect exposure, then ask the learner whether they feel ready to continue.
