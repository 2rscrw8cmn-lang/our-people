# Interaction Model

This document defines how Our People should behave before visual polish. When interaction behavior and conventional app patterns conflict, preserve the deck/card metaphor unless there is a clear usability reason not to.

## Home: the deck

The app opens directly into the deck. There is no dashboard and no bottom navigation.

Persistent controls are intentionally limited to:

- Search
- Add
- A–Z index on the right edge

Relationship sections appear as divider tabs within the deck. They are not filters floating above unrelated content.

## Relationship sections

Current working sections:

- Our People
- Close
- Get to Know

Behavior:

- tapping a divider moves to that section of the deck
- cards are alphabetical within the active section
- moving through cards updates the visible section naturally
- the A–Z index operates within the current section
- section tabs should feel physically embedded in the deck

## Card states

### 1. Browsing

Purpose: fast recognition and movement through the deck.

Show only enough information to recognize the people:

- generated/display title
- first names when useful
- location when useful
- one small current detail at most

Multiple neighboring cards should remain visible so the deck feels tangible.

### 2. Pulled forward

A tap on a browsing card brings that same card forward rather than navigating to a conventional profile screen.

The pulled-forward card may show:

- display title
- names
- location
- children
- last-seen note/date if available
- a small number of recent jots
- subtle affordance to jot a note
- overflow/edit affordance

The card should still feel like the same object from the deck.

### 3. Memory/back

A flip or equivalent physical interaction reveals deeper memory:

- birthdays
- important dates
- accumulated notes
- how we know them
- contact details if stored
- other secondary information

The back may scroll when history grows. Avoid turning it into a tabbed profile page.

## A–Z index

A slim alphabetical index lives on the right edge.

Behavior:

- visually quiet until touched
- dragging through letters rifles through cards
- tapping a letter jumps to the first matching card in the current relationship section
- movement should feel continuous rather than like loading a new page

## Search

Search is for direct retrieval and can temporarily prioritize utility over the physical metaphor.

Search across:

- generated/display card title
- individual names
- children
- location
- note text

Selecting a result returns the user to that card in the deck and pulls it forward.

## Add

The global Add control exposes two actions:

- Add people
- Add note

Do not call the first action “Add family.” A card may represent one person, a couple, or a household.

## Add people

Adding people must be intentionally lightweight. It should not feel like filling out a contact form.

Minimum information:

1. one or more people
2. relationship section

The app derives the card title automatically.

Examples:

- `Daniel Ortiz` → `Daniel Ortiz`
- `Mike Harrison` + `Lauren Harrison` → `The Harrisons`
- `Matt Johnson` + `Sarah Williams` → `Matt + Sarah`

The user may override the title.

The app should handle household pluralization intelligently where practical, including surnames such as Smith, Jones, Garcia, etc. Users should never need to type boilerplate such as “The”.

After save, the new card is inserted into the correct alphabetical position in the selected section and pulled forward.

Details such as birthdays, children, phone numbers, and notes should be optional and added later from the card.

## Add note

There are two entry points to the same note object.

### From a card

`Jot something down`

- card is pre-tagged
- user writes the note
- save returns to the card

### Global

`Add → Add note`

- user writes the note
- user tags one or more cards
- save makes the note available on every tagged card and in the notebook

A note can belong to multiple cards. Do not duplicate the underlying note to achieve this.

## Notebook

The notebook is a chronological view of all notes.

It should feel like reviewing accumulated jots, not consuming an activity feed.

Show:

- note body
- date
- tagged card(s)
- quiet author attribution when useful in a shared household

Avoid:

- engagement UI
- read/unread states
- priority queues
- badges
- task states

The notebook can initially be accessed from a restrained overflow/menu rather than permanent bottom navigation.

## Shared household behavior

The Rolodex belongs to the household, not to an individual user.

- both household members see the same cards
- both see the same notes
- edits update the shared object
- note authorship may be shown subtly when useful
- there is no collaboration dashboard or activity center

## Surfacing people

Surfacing should eventually change deck position or prominence rather than generate tasks.

Potential future inputs:

- time since last seen
- approaching birthday
- relationship section
- explicit desire to get to know someone better

Do not implement a scoring system in the MVP. The correct behavior should be learned from real use first.

## MVP wireframe states

Before visual implementation, resolve these states:

1. deck — browsing
2. card — pulled forward
3. card — memory/back
4. search
5. add people
6. add note
7. notebook
8. empty/new household
9. basic shared-household/settings state

## Primary vertical slice

The first production-quality interaction loop is:

`Deck → Add people → New card → Jot note → Note on card → Note in notebook`

Build and review this loop on an actual phone before expanding the application.
