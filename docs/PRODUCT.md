# Product

## One sentence

Our People is a shared modern Rolodex: a quiet place for a household to keep the people they care about, remember small things about their lives, and gently rediscover relationships that might otherwise drift out of attention.

## Product premise

Life naturally concentrates attention on the people already in front of us. Close friends stay close because the relationship is effortless; other people we care about can disappear from view simply because life is busy. Our People should help with that without turning friendship into work.

The product should feel more like a familiar household object than a conventional application. The interaction model borrows from a Rolodex or address book, while the visual design remains modern and restrained.

## Core principles

1. **The card is the product.** A person or group is understood through a card, not a profile page full of modules.
2. **The deck is the navigation.** Browsing should feel like moving through a set of cards, not navigating an information architecture.
3. **Surfacing is subtle, not task-based.** A person may move nearer the front of the deck, but there are no overdue states, red warnings, or completion mechanics.
4. **Adding people is intentional and easy.** Putting someone in the deck should take seconds. Details can accumulate later.
5. **Notes feel like jots, not records.** They are short pieces of memory, not CRM activity logs.
6. **Shared ownership, not collaboration tooling.** A household shares one Rolodex. Attribution can exist quietly when useful.
7. **The app should infer obvious presentation details.** Users should not type boilerplate such as “The” for a household title. Display names are derived intelligently and can be overridden.
8. **If a feature makes this feel more like software, question whether it belongs.**

## What it is not

Our People is not:

- a CRM
- a task manager
- a contact-sync replacement
- a social network
- a relationship scorecard
- a streak or habit app
- a dashboard
- an AI assistant
- a productivity system

Do not introduce AI, scores, health percentages, streaks, gamification, inboxes, task completion, or productivity language.

## Core objects

### Deck

The home experience. Cards are grouped into relationship sections and alphabetized within each section.

### Card

Represents one person or more than one person. A card may represent:

- one person: `Daniel Ortiz`
- a couple: `Matt + Sarah`
- a household: `The Harrisons`

The display title is derived from the people on the card where possible. The user may override it.

### Note

A quick jot attached to one or more cards. Notes can be added from a card or globally.

### Notebook

A chronological view of all notes for review. It is secondary to the deck and should not become a feed or dashboard.

### Relationship section

A divider in the deck, not a filter control. Current working sections:

- Our People
- Close
- Get to Know

Names may change later, but the three-layer model is intentional.

## MVP

The first usable product should support:

- shared household account model
- deck with relationship sections
- alphabetical cards within sections
- A–Z edge index
- search
- add people
- generated card titles
- card browse and pulled-forward states
- quick notes
- notes tagged to one or more cards
- chronological notebook
- basic editing of people and cards

## Explicitly deferred

Do not build these until the core loop has been used and validated:

- automatic relationship cadence scoring
- aggressive reminders or notifications
- calendar/contact ingestion beyond a deliberate picker
- rich interaction-history taxonomy
- complex settings
- photos as a core card element
- analytics
- AI

## First product test

The product succeeds at the first stage if a household can:

1. open the deck,
2. add people in seconds,
3. find them naturally later,
4. jot something worth remembering,
5. see that memory on the card and in the notebook,
6. enjoy browsing enough that the Rolodex feels worth returning to.
