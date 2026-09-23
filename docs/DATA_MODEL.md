# Data Model

This is the initial relational model for Cloudflare D1. Keep it small and explicit. The UI may say “card,” “people,” or “our people”; internal table names should avoid assuming every card is a family.

## households

Shared ownership boundary for one Rolodex.

- id
- name nullable
- created_at
- updated_at

## users

Application users.

- id
- auth_subject
- display_name
- created_at
- updated_at

## household_members

Joins users to a shared household.

- household_id
- user_id
- role
- joined_at

## cards

Primary Rolodex object. A card may represent one person or multiple people.

- id
- household_id
- display_name_override nullable
- derived_display_name
- section (`our_people`, `close`, `get_to_know`)
- location nullable
- last_seen_at nullable
- last_seen_note nullable
- created_at
- updated_at

`derived_display_name` is regenerated from the people on the card unless an override exists.

## people

Individuals attached to a card.

- id
- card_id
- first_name
- last_name nullable
- birthday nullable
- phone nullable
- email nullable
- sort_order
- created_at
- updated_at

A single card may contain one or many people.

## notes

A jot written by a household member.

- id
- household_id
- body
- author_user_id
- created_at
- updated_at
- deleted_at nullable

## note_cards

Many-to-many join so one note can be attached to multiple cards without duplication.

- note_id
- card_id

Unique constraint on `(note_id, card_id)`.

## important_dates

Optional dates beyond individual birthdays.

- id
- card_id
- label
- month
- day
- year nullable
- created_at

## interactions — deferred but reserved

Do not build until needed. If implemented, keep it separate from notes.

- id
- card_id
- author_user_id
- type (`saw`, `talked`, `messaged`)
- occurred_at
- note nullable
- created_at

## Display-name derivation

The app should derive titles rather than requiring users to type household formatting.

Rules for MVP:

1. one person → first + last name when available
2. multiple people sharing a surname → plural household form, e.g. `The Harrisons`
3. multiple adults with different surnames → first names joined naturally, e.g. `Matt + Sarah`
4. if derivation is awkward or ambiguous, use first names rather than inventing a household surname
5. `display_name_override` always wins

Pluralization should be covered by tests, especially surnames ending in `s`, `x`, `z`, `ch`, and `sh`.

## Sorting

Cards are alphabetical by their effective display name, ignoring a leading `The ` for sort purposes.

Example:

- `The Harrisons` sorts under H
- `Daniel Ortiz` sorts under O or D depending on final UX decision; default MVP recommendation is by displayed title after stripping `The `, which places Daniel under D

The interaction spec should remain the source of truth if this rule changes after wireframe testing.

## Deletion

Prefer soft-delete for notes initially. Card/person deletion behavior should be confirmed before implementation because shared household data can be difficult to recover.

## Indexes

At minimum:

- cards.household_id
- cards.section
- people.card_id
- notes.household_id + created_at
- note_cards.card_id
- note_cards.note_id

Search strategy can begin with normal SQL matching and evolve later. Do not add a separate search service in the MVP.
