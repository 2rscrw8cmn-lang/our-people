# Product Decisions

This file records approved decisions so future implementation does not quietly drift back toward conventional app patterns.

Use these statuses:

- **LOCKED** — do not change without an explicit product decision
- **WORKING** — current direction, open to revision during wireframing/testing
- **DEFERRED** — intentionally postponed

---

## 2026-09-22 — The product is a modern Rolodex

**Status: LOCKED**

Our People should feel like a familiar household object translated into modern software, not like a CRM, task manager, or social app.

The physical metaphor should influence behavior more than decorative styling.

---

## 2026-09-22 — The deck is home

**Status: LOCKED**

The app opens directly into the deck. There is no dashboard as the primary home experience.

---

## 2026-09-22 — The card is the primary product object

**Status: LOCKED**

People are represented through cards. Avoid converting the card into a conventional multi-tab profile page.

---

## 2026-09-22 — No bottom navigation

**Status: LOCKED**

Primary navigation is the deck itself. Search and Add are globally available. Secondary destinations such as the notebook can live behind restrained secondary navigation.

---

## 2026-09-22 — No AI

**Status: LOCKED**

Do not introduce AI for note summarization, relationship analysis, prompts, recommendations, or conversational interfaces.

The product should help people remember; it should not analyze their relationships for them.

---

## 2026-09-22 — No scoring, dashboards, streaks, or task mechanics

**Status: LOCKED**

Do not add:

- relationship health scores
- completion percentages
- streaks
- overdue states
- red-warning attention systems
- relationship tasks
- productivity dashboards
- gamification

Surfacing should be subtle and expressed through the deck itself.

---

## 2026-09-22 — Cards may represent one or many people

**Status: LOCKED**

A card is not synonymous with a family.

Valid examples:

- `Daniel Ortiz`
- `Matt + Sarah`
- `The Harrisons`

Product language should prefer **Add people**, not **Add family**.

---

## 2026-09-22 — Display titles are inferred

**Status: LOCKED**

Users should not need to type presentation boilerplate such as `The`.

The application derives card titles from the people on the card and supports an explicit override.

Examples:

- one person → `Daniel Ortiz`
- shared surname → `The Harrisons`
- different surnames → `Matt + Sarah`

Pluralization and sorting behavior must be tested.

---

## 2026-09-22 — Three relationship sections

**Status: WORKING**

The product uses three relationship layers represented as physical dividers in the deck.

Current labels:

- Our People
- Close
- Get to Know

The three-layer concept is intentional. Exact labels may change.

---

## 2026-09-22 — Cards are alphabetical within a section

**Status: WORKING**

Each relationship section is alphabetized. A slim A–Z index on the right edge allows fast rifling through the current section.

Exact sorting rules for individuals may be adjusted after wireframe testing.

---

## 2026-09-22 — Search and Add are the persistent controls

**Status: LOCKED**

Keep persistent app chrome extremely limited. Search and Add remain globally available; avoid expanding the header into a conventional toolbar.

---

## 2026-09-22 — Add exposes Add people and Add note

**Status: LOCKED**

Global Add should support:

- Add people
- Add note

Adding people must be fast and should ask for only what is necessary to create the card.

---

## 2026-09-22 — Notes are shared jots

**Status: LOCKED**

Notes are lightweight pieces of memory, not structured activity records.

A note can tag one or multiple cards. A note created from a card automatically tags that card.

---

## 2026-09-22 — A chronological notebook exists

**Status: LOCKED**

There should be one place to review accumulated notes chronologically.

It should not behave like an inbox, notification center, social feed, or task queue.

---

## 2026-09-22 — Shared ownership is household-based

**Status: LOCKED**

Two household members share one Rolodex. Cards and notes are shared objects rather than duplicated per user.

Collaboration UI should remain minimal.

---

## 2026-09-22 — Photos are not core to the card

**Status: WORKING**

Current direction is text-first cards without family photos. Photos may be reconsidered later, but the product should not depend on them for recognition or identity.

---

## 2026-09-22 — Gentle surfacing is deferred

**Status: DEFERRED**

The product may eventually bring certain cards nearer the front based on time, birthdays, or relationship intent, but the algorithm and behavior should not be implemented until the base product is used in practice.

Do not create a hidden relationship score as a shortcut.

---

## 2026-09-22 — Cloudflare + GitHub

**Status: WORKING**

Current infrastructure direction:

- GitHub source repository
- Cloudflare deployment
- Cloudflare Workers/server logic
- Cloudflare D1 relational database
- branch/PR previews before user-facing merges

Architecture may evolve if a concrete constraint requires it.
