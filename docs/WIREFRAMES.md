# MVP Wireframes

These are low-fidelity interaction wireframes for the first build. They describe behavior and hierarchy, not final visual styling.

The source of truth for product behavior remains `PRODUCT.md`, `INTERACTIONS.md`, and `DECISIONS.md`.

## Core flow

`Deck → Add people → New card → Pull forward → Jot note → Updated card → Notebook`

The user should be able to complete this full loop without encountering a dashboard, bottom navigation, task state, or profile-style contact screen.

---

## 1. Deck — browsing

```text
┌──────────────────────────────┐
│ our people          🔎    ＋ │
│                              │
│   OUR PEOPLE  CLOSE  GET TO  │
│                    KNOW      │
│ ┌─────────────────────────┐ A│
│ │ The Millers             │ B│
│ ├─────────────────────────┤ C│
│ │ The Parkers             │ D│
│ ├─────────────────────────┤ E│
│ │ THE HARRISONS           │ F│
│ │ Mike + Lauren           │ G│
│ │ College Park            │ H│
│ ├─────────────────────────┤ I│
│ │ The Johnsons            │ J│
│ ├─────────────────────────┤ K│
│ │ The Reeds               │…│
│ └─────────────────────────┘ Z│
└──────────────────────────────┘
```

### Behavior

- Deck is the home state.
- Search and Add are the only persistent controls.
- Relationship sections are physical dividers in the deck.
- The A–Z rail is visually quiet until touched.
- Cards are alphabetical within the active relationship section.
- Browsing cards stay compact enough that several neighboring cards remain visible.
- Tapping a card pulls that same object forward; it does not navigate to a separate profile page.

---

## 2. Add people

Adding people should feel like putting a new card into the Rolodex, not completing a contact form.

```text
┌──────────────────────────────┐
│ Add people                ×  │
│                              │
│ PEOPLE                       │
│ [ Mike Harrison        × ]   │
│ [ Lauren Harrison      × ]   │
│ + Add another person          │
│                              │
│ SUGGESTED CARD NAME          │
│ The Harrisons                │
│ You can change this.         │
│                              │
│ WHERE DO THEY BELONG?        │
│ [Our People] [Close] [Get to │
│                         Know]│
│                              │
│        Add to Rolodex        │
└──────────────────────────────┘
```

### Rules

- Language is **Add people**, never **Add family**.
- One person is valid.
- A couple is valid.
- A household is valid.
- Minimum input is one or more people plus a relationship section.
- The app generates the card title as the user types.
- Users do not type boilerplate such as `The`.
- Suggested title is editable before or after save.
- Birthdays, children, phone numbers, location, notes, and other metadata are not required here.

### Title examples

- `Daniel Ortiz` → `Daniel Ortiz`
- `Mike Harrison` + `Lauren Harrison` → `The Harrisons`
- `Matt Johnson` + `Sarah Williams` → `Matt + Sarah`

---

## 3. New card inserted

Saving should return directly to the deck.

```text
┌──────────────────────────────┐
│ our people          🔎    ＋ │
│                              │
│   OUR PEOPLE  CLOSE  GET TO  │
│                    KNOW      │
│ ┌─────────────────────────┐  │
│ │ The Garcias             │  │
│ ├─────────────────────────┤  │
│ │ THE HARRISONS           │◀ │
│ │ Mike + Lauren           │  │
│ ├─────────────────────────┤  │
│ │ The Millers             │  │
│ └─────────────────────────┘  │
└──────────────────────────────┘
```

### Behavior

- New card is inserted in its alphabetical position within the selected section.
- New card becomes the active card.
- Avoid a separate success screen.
- A tiny transient confirmation is acceptable if needed, but the deck itself should communicate success.

---

## 4. Card — pulled forward

```text
┌──────────────────────────────┐
│ our people          🔎    ＋ │
│                              │
│      cards remain behind     │
│   ┌──────────────────────┐   │
│   │ The Harrisons    ••• │   │
│   │ Mike + Lauren        │   │
│   │ College Park         │   │
│   │──────────────────────│   │
│   │ Jack · 6    Annie · 3│   │
│   │                      │   │
│   │ LAST SAW             │   │
│   │ Dinner at our house  │   │
│   │ June 14              │   │
│   │──────────────────────│   │
│   │ Lauren started at…   │   │
│   │ Jack loves dinosaurs │   │
│   │                      │   │
│   │ + Jot something down │   │
│   └──────────────────────┘   │
│      cards remain below      │
└──────────────────────────────┘
```

### Behavior

- The card enlarges but remains visibly part of the deck.
- Keep surrounding cards visible enough to preserve spatial context.
- Show only a few recent/current jots.
- No tab bar inside the card.
- Overflow handles edit/move/delete-type utilities.

---

## 5. Card — memory/back

The back is the same card, not a new profile screen.

```text
┌──────────────────────────────┐
│      cards remain behind     │
│   ┌──────────────────────┐   │
│   │ ← The Harrisons      │   │
│   │                      │   │
│   │ PEOPLE               │   │
│   │ Mike Harrison        │   │
│   │ Lauren Harrison      │   │
│   │ Jack · 6   Annie · 3 │   │
│   │                      │   │
│   │ DATES                │   │
│   │ Mike · Nov 2         │   │
│   │ Lauren · Mar 18      │   │
│   │                      │   │
│   │ NOTES                │   │
│   │ Sep 21  Great dinner │   │
│   │ Aug 03  New job…     │   │
│   │ Jun 14  Dinner…      │   │
│   │                      │   │
│   │ More ↓               │   │
│   └──────────────────────┘   │
└──────────────────────────────┘
```

### Behavior

- This state may scroll vertically as memory grows.
- It should visually preserve the card edges/background deck.
- Avoid conventional profile-page patterns such as `About / Notes / Dates / History` tabs.

---

## 6. Add note

From a card, the current card is already tagged.

```text
┌──────────────────────────────┐
│ New note                  ×  │
│                              │
│ Great dinner last night.     │
│ Jack showed us his new LEGO  │
│ set. Lauren mentioned a      │
│ beach trip in January.       │
│                              │
│                              │
│ LINKED TO                    │
│ [ The Harrisons × ]          │
│ + Add another                │
│                              │
│           Save               │
└──────────────────────────────┘
```

### Behavior

- Text entry is the dominant element.
- Card-originated notes are pre-linked.
- Global Add Note starts unlinked and requires at least one card tag.
- One note may link to multiple cards.
- Saving returns to the prior context.
- No category, priority, reminder, status, or task fields in MVP.

---

## 7. Updated card

After save, the new jot simply becomes part of the card.

```text
┌──────────────────────────────┐
│   ┌──────────────────────┐   │
│   │ The Harrisons        │   │
│   │                      │   │
│   │ Great dinner last    │   │
│   │ night. Jack showed   │   │
│   │ us his new LEGO set. │   │
│   │                      │   │
│   │ Lauren started at…   │   │
│   │                      │   │
│   │ + Jot something down │   │
│   └──────────────────────┘   │
└──────────────────────────────┘
```

No completion state is needed. The changed object is the confirmation.

---

## 8. Notebook — all notes

```text
┌──────────────────────────────┐
│ ←  all notes             🔎  │
│                              │
│ SEP 21                       │
│ Great dinner last night.     │
│ The Harrisons                │
│                              │
│ AUG 03                       │
│ Lauren started her new job.  │
│ The Harrisons                │
│                              │
│ JUN 14                       │
│ Dinner at our house.         │
│ The Harrisons                │
│                              │
│ MAY 02                       │
│ New baby is due in October.  │
│ The Parkers                  │
└──────────────────────────────┘
```

### Behavior

- Chronological notebook, newest first.
- No `All / Recent / Mine` tab system in MVP.
- No read/unread state.
- No badges.
- No task completion.
- Tagged cards are visible but secondary to note text.
- Search may filter notebook content.

---

## 9. Search

Search is the one place where utility can temporarily override the physical metaphor.

```text
┌──────────────────────────────┐
│ [ Harrison____________ ]  ×  │
│                              │
│ PEOPLE                       │
│ The Harrisons                │
│ Mike + Lauren · College Park │
│                              │
│ NOTES                        │
│ Lauren started at Advent…    │
│ The Harrisons                │
│                              │
│ Dinner at our house.         │
│ The Harrisons · Jun 14       │
└──────────────────────────────┘
```

Selecting a person/card result returns to that card in the deck and pulls it forward. Selecting a note opens it in its card context where practical.

---

## 10. Empty/new household

The empty state should teach the object model, not explain features.

```text
┌──────────────────────────────┐
│ our people          🔎    ＋ │
│                              │
│        ┌────────────┐        │
│        │            │        │
│        │ Your people│        │
│        │ will live  │        │
│        │ here.      │        │
│        │            │        │
│        └────────────┘        │
│                              │
│        + Add people          │
└──────────────────────────────┘
```

Avoid onboarding carousels unless later testing shows they are necessary.

---

## 11. Shared household/settings

This state exists for utility but should remain visually subordinate to the Rolodex.

Minimum MVP needs:

- household name if used
- current members
- invite spouse/partner
- leave household / account utilities

Do not add collaboration analytics, change history dashboards, or activity feeds.

---

## Interaction review checklist

Before implementation, verify:

- [ ] Deck remains home in every normal return path.
- [ ] Cards visibly remain cards when expanded or flipped.
- [ ] Add people can be completed with names + section only.
- [ ] One-person cards work naturally.
- [ ] Household names are inferred rather than manually prefixed with `The`.
- [ ] Notes can tag multiple cards.
- [ ] Notebook reads as accumulated memory, not a feed.
- [ ] No bottom nav is required to complete the primary flow.
- [ ] Search, Add, and A–Z are sufficient for direct navigation.
- [ ] No AI, score, streak, task, reminder queue, or CRM language appears.
