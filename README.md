# nibble

A task and event planner. Three files. No build step. No node_modules.

**[Try it →](https://snackdriven.github.io/nibble/)**

---

It started as a fix for the thing where you open your task manager and immediately close it because it has too much going on. nibble has tasks and events. That's it.

The ADHD design is intentional. "Blocked" isn't a status you set manually — it's derived from unfinished dependencies, so the app figures out what you can actually work on right now instead of showing you everything you can't touch yet. Activation dates let you hide tasks until they're actually relevant. The Active view only surfaces due-by tasks in the next 10 days, not your entire backlog forever.

If that sounds like exactly what you needed, hi.

## Tasks

Three time states:

- **due-by** — has a deadline. Surfaces 10 days out with a countdown so it doesn't ambush you.
- **open** — no deadline. Gets a stale badge after 14 days untouched, because if you haven't looked at it in two weeks, something's up.
- **recurring** — completes and immediately queues the next instance. No manual rescheduling.

Status goes `active → waiting → done`. Blocked is derived, not set.

Tasks can have subtasks, dependencies, and labels. The only labels are `15min` (do it now, it's short) and `browse` (needs a screen and low commitment). Execution hints, not categories. An optional activation date controls when a task first becomes visible.

## Events

Date with optional time, location, and notes. Show up on the calendar alongside tasks due that day. No recurring events — use a calendar app for that.

## Views

| View | What it shows |
|------|---------------|
| Calendar | Week strip + everything on the selected day. Agenda mode groups upcoming events by date. |
| Active | Due-by tasks in the next 10 days (toggle to see the full backlog). Overdue and due-today get their own sections so they don't hide. |
| Anytime | Open tasks plus anything labeled `browse` or `15min`. Good for low-energy windows. Sortable. |
| Recurring | Recurring tasks due today or earlier — the ones you've been putting off. |
| Done | Last 50 completed items, reopenable. Auto-purges after 90 days. |
| All | Everything. Title search, type filter, sort. Read-only — it's an archive, not a workspace. |

## The small stuff

- Ctrl+Z / Cmd+Z undoes the last action, up to 20 levels
- `?` opens this repo
- Dark mode only, no apologies
- Mobile-first, 44px touch targets, safe-area support
- View transitions (Chrome, Edge, Firefox)

## Sync

Sign in with a magic link to sync across devices. Data lives in `localStorage` first — Supabase is the async remote copy, not the source of truth. Works fully offline; it'll catch up when you're back.

Dot in the header: yellow = syncing, green = synced, peach = queued, red = something went wrong (it'll retry).

Sign-in is optional. "Use without sync" skips it entirely, and you can always sign in later from the header if you change your mind.

## Run locally

```sh
open index.html
```

Or with hot reload:

```sh
npx serve .
```

## License

MIT
