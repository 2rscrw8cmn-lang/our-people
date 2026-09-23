# Architecture

## Goal

Keep the first architecture boring, relational, and easy to preview. The product is small and does not need distributed systems or a large service layer.

## Proposed stack

### Application

- TypeScript
- React
- responsive mobile-first web app / PWA
- deployed on Cloudflare

### Backend

- Cloudflare Workers for server/API logic
- Cloudflare D1 for relational storage
- Cloudflare preview deployments for pull requests or branches

### Repository

- GitHub is the source of truth
- `main` should remain deployable
- feature work should be issue-driven and reviewed in preview before merge

## Initial shape

```text
Browser / PWA
    |
    v
Cloudflare app / Worker
    |
    v
Cloudflare D1
```

Keep the frontend and backend in one repository unless a clear need to split appears.

## Do not add yet

Avoid these until a real requirement appears:

- R2
- Durable Objects
- Queues
- KV as a primary data store
- microservices
- separate search infrastructure
- background relationship-scoring jobs
- AI services

## API boundary

The UI should not directly own persistence rules. Centralize mutations for:

- cards
- people
- notes
- note tags
- household membership

Display-name derivation should live in a tested shared/domain layer rather than being duplicated in components.

## Shared household security

Every user-owned query must be scoped by household membership. A user must never be able to read or mutate a card or note simply by knowing its ID.

Server-side authorization rule:

1. authenticate user
2. resolve household membership
3. scope reads/writes to that household
4. reject cross-household access

## Auth

Authentication provider is intentionally not locked yet. The data model should depend on a stable external auth subject, not provider-specific user tables.

Choose auth before implementing shared invitations. Do not let auth work block the first local/preview interaction slice if mock authentication can be isolated cleanly.

## Environments

Plan for:

- local development
- branch/PR preview
- production

Each environment should use isolated data where practical. Preview environments must never point at production D1 data.

## Migrations

All D1 schema changes must be migration-backed and committed to the repository.

No manual production-only schema edits.

## Testing priorities

Unit tests:

- card display-name derivation
- surname pluralization
- sorting / leading `The` handling
- note-to-multiple-card behavior
- household authorization helpers

Interaction tests:

- add people → card appears in correct section/order
- add note from card → auto-tagged
- add global note → tagged to one or more cards
- notebook reflects notes chronologically

## Preview-first rule

Any meaningful visual or interaction change should be reviewed on a Cloudflare preview before merge. This product depends heavily on touch, spacing, card movement, and motion; static code review is not enough.
