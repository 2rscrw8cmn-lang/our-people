# Build Plan

Build in vertical slices. Do not complete whole technical layers in isolation.

## Phase 0 — Foundation

- repository documentation
- TypeScript / React project scaffold
- Cloudflare project
- D1 database and migration setup
- local development workflow
- preview deployment workflow
- basic CI: typecheck, lint, tests, build

**Exit:** a blank mobile-first app deploys successfully to a non-production Cloudflare environment from GitHub.

## Phase 1 — Interaction prototype

Resolve the core physical model before visual polish.

Wireframe / prototype:

1. deck — browsing
2. card — pulled forward
3. card — memory/back
4. search
5. add people
6. add note
7. notebook
8. empty/new household
9. shared household/settings shell

Focus on touch behavior, card depth, section movement, and A–Z rifling. Use restrained temporary styling.

**Exit:** core interactions make sense on an actual phone without relying on conventional bottom navigation or profile pages.

## Phase 2 — Vertical Slice 01

Build the smallest complete real-data loop:

`Deck → Add people → New card → Jot note → Note on card → Note in notebook`

Include:

- D1 persistence
- one shared/demo household
- add one or more people
- derived card display name
- section assignment
- alphabetical insertion
- pulled-forward card state
- note creation
- card pre-tagging
- notebook readout

**Exit:** the full loop works after refresh on a Cloudflare preview.

## Phase 3 — Deck navigation

- relationship divider behavior
- A–Z index
- smooth card browsing
- section transitions
- search across cards, people, location, notes
- selecting a search result returns to the correct card

**Exit:** finding a person is fast whether browsing or searching.

## Phase 4 — Card memory

- card back / memory state
- birthdays
- important dates
- children/people editing
- location
- full note history
- edit display-name override
- move card between sections

**Exit:** a card can accumulate useful memory without becoming a conventional profile page.

## Phase 5 — Shared household

- production authentication
- household creation
- invite/join flow
- shared cards and notes
- quiet authorship attribution
- household-scoped authorization tests

**Exit:** two users can safely share one Rolodex without duplicate data or collaboration-dashboard UI.

## Phase 6 — Visual and motion system

Apply the polished visual direction after the core interactions are stable.

- typography
- card surfaces
- divider colors
- spacing
- depth / shadows
- card pull-forward motion
- section rifling
- card flip transition
- insertion of a new card
- reduced-motion behavior

**Exit:** the product feels like modern software behaving like a familiar physical object.

## Phase 7 — Gentle surfacing research

Do not implement automatically until there is real usage data.

Test simple concepts such as:

- recent/old last-seen information
- upcoming birthday
- get-to-know section weighting
- manual “bring them back to mind” intent

The output should affect card position or subtle presentation, not create tasks or scores.

## Issue / PR workflow

For each meaningful change:

1. create or reference a GitHub issue
2. branch from current `main`
3. implement the narrow acceptance criteria
4. deploy a Cloudflare preview
5. review on phone for UI/interaction work
6. update docs if behavior changed
7. open PR with preview and screenshots
8. merge only when checks pass and approved behavior is preserved

Suggested branch names:

- `feat/deck-prototype`
- `feat/add-people`
- `feat/notes`
- `feat/alphabet-index`
- `fix/card-stack-motion`

## PR template expectations

Every product/UI PR should answer:

### What changed

Short description of the behavior implemented.

### Acceptance criteria

Checklist tied to the issue.

### Preview

Cloudflare preview URL for any user-facing change.

### Evidence

Screenshots or short capture when visual/touch behavior changed.

### Deferred

Anything intentionally not handled in this PR.

### Product guardrails

Confirm the change does not introduce a dashboard, scoring, AI, task mechanics, bottom navigation, or CRM-style behavior unless an approved decision explicitly changes those rules.
