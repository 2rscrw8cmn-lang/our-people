# Clickable lo-fi prototype

This prototype exists to validate the interaction model before Cloudflare/D1 implementation or final visual polish.

## Review path

Open `index.html` in a browser and test this loop:

1. Browse the deck.
2. Tap a card to pull it forward.
3. Tap `+` → `Add people`.
4. Add one person or multiple people and confirm the suggested card name.
5. Add the card to a relationship section.
6. Jot a note from the pulled-forward card.
7. Open the card overflow → `All notes`.
8. Search for a person or note.
9. Use the A–Z rail and relationship dividers.
10. Flip the card from the overflow menu to review deeper memory.

## Important

- Prototype data is in-memory only and resets on refresh.
- This is not the production architecture.
- No backend, auth, Cloudflare, or D1 is connected yet.
- The prototype intentionally avoids bottom navigation, dashboards, tasks, scores, and AI.
