# Quality

## Sample

- **Location:** my parts of [fakeletterboxd](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd): [`supabase/migrations/`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/tree/main/supabase/migrations), [`supabase/functions/sync-menu/`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/tree/main/supabase/functions/sync-menu), [`docs/supabase-setup.md`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/docs/supabase-setup.md), and `lib/profile/` (on my `profile-screen` branch, not yet pushed).
- **My contribution:** I wrote the backend and setup docs, and designed the profile feature, which Claude Code (AI) helped implement.

## Discussion

**Strengths**

- **Schema as code:** every table, policy and job lives in reviewed migrations with comments explaining why.
- **Security by default:** row level security on every table, a Grinnell-only sign-up check, and server-only secrets.
- **Idempotent sync:** re-running the scraper is always safe, and it cleans up removed menu items and tags.
- **Separation of concerns:** parsing is separate from database writes, and the UI is separate from data access.
- **Documentation:** a teammate can set up the backend from the guide alone.

**Shortcomings, and fixes with more time**

- **Testing:** my code is almost untested. I'd add Deno tests for parsing and Flutter tests for the profile.
- **Migration drift:** the remote database is out of sync with the repo. I'd reconcile it and enforce migration-only changes.
- **Unmerged work:** the CI fix and profile screen aren't on `main` yet. I'd open PRs for both.
- **Debug output:** some error messages print raw debug text. I'd replace them with user-friendly messages.
