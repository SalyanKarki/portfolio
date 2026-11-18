# Infrastructure

## Sample

- **Location:** [`supabase/config.toml`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/config.toml), [`supabase/migrations/`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/tree/main/supabase/migrations), [`.env.example`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/.env.example) and [`.gitignore`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/.gitignore) (commit `c09fb8e`), plus the CI workflow fix (`3337462`).
- **My contribution:** I set up the Supabase CLI project, the migrations workflow and the environment-file setup. _(Note any AI help here.)_

## Discussion

- **Tools:** VS Code, the Flutter SDK, the Supabase CLI (`link`, `migration new`, `db push`, `functions deploy`), Git/GitHub and GitHub Actions.
- **Schema as code:** every database change is a migration file in git, so the shared database can be rebuilt and reviewed like code.
- **Secrets:** keys live in an ignored `.env` file, with a committed `.env.example` template, so no keys end up in the repo.
- **Specific problem:** `supabase migration list` showed local migrations that were never applied to the remote database, including a duplicate menu schema, so `db push` would fail. The CLI made the drift visible but couldn't fix it automatically.
- **Another snag:** the team's `pubspec.yaml` required a newer Dart SDK than mine, so nothing built until I ran `flutter upgrade`.
