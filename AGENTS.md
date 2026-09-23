# Agent Guidance

Read these before changing user-facing behavior:

1. `docs/PRODUCT.md`
2. `docs/INTERACTIONS.md`
3. `docs/DECISIONS.md`
4. `docs/DATA_MODEL.md` when changing persistence
5. `docs/ARCHITECTURE.md` when changing infrastructure

## Product guardrails

Our People is a modern shared Rolodex. Preserve that premise.

Do not introduce these unless an explicit issue changes a locked decision:

- AI features
- relationship scores or health percentages
- dashboards
- streaks or gamification
- task/completion mechanics
- bottom navigation
- CRM terminology or activity-pipeline patterns
- aggressive alerts or overdue states
- family-only assumptions in the data model
- large forms for adding people

## Interaction guardrails

- The deck is home.
- The card is the primary object.
- Relationship sections behave like dividers in the deck.
- Search and Add are the only persistent top-level controls currently approved.
- The A–Z index is part of direct deck navigation.
- A card may represent one person or several people.
- Product language should use “Add people,” not “Add family.”
- Card display titles are inferred and may be overridden.
- Notes are short jots and may tag multiple cards.
- A note created from a card should automatically tag that card.
- The notebook is chronological review, not an inbox or feed.

## Design behavior

Prefer modern software that behaves like a familiar physical object. Do not solve the metaphor with fake wood, leather, heavy skeuomorphism, or decorative nostalgia.

When a standard application pattern would make the product feel more conventional, first look for a simpler interaction that preserves the deck/card model.

Do not redesign approved interaction models as part of unrelated implementation work.

## Engineering behavior

- Keep `main` deployable.
- Use issue-scoped branches.
- Keep changes narrow.
- Add migrations for D1 schema changes.
- Scope household data on the server, never only in the UI.
- Add tests for domain rules such as display-name derivation and sorting.
- Do not add infrastructure without a concrete requirement.
- User-facing PRs should include a Cloudflare preview before merge once previews are configured.

## Definition of done for UI work

A user-facing change is not done solely because it compiles.

Verify:

- behavior on a phone-sized viewport
- touch targets
- deck/card hierarchy
- neighboring cards remain understandable
- no accidental conventional-app chrome was introduced
- reduced-motion behavior when motion is involved
- preview deployment works

## Documentation rule

If a PR changes an approved product behavior, update the relevant document and `docs/DECISIONS.md` in the same PR.
