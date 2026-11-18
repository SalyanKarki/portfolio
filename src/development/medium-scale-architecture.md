# Medium-scale architecture

## Sample

- **Location:** the backend in [`supabase/`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/tree/main/supabase): schema in [`migrations/20261012000000_menu_schema.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261012000000_menu_schema.sql) and [`20261013000000_user_schema.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261013000000_user_schema.sql), the menu sync in [`functions/sync-menu/`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/tree/main/supabase/functions/sync-menu), and the schedule in [`20261022000000_menu_sync.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261022000000_menu_sync.sql).
- **My contribution:** I designed and wrote the database schema (`63c3dd8`), set up the Supabase project (`c09fb8e`), and built the sync job (`d2cb503`). Teammates built the Flutter front-end that reads from it. _(Note any AI help here.)_

## Discussion

- **Pattern:** client–server using a backend-as-a-service: a thin Flutter client talks directly to Supabase, and security rules live in the database rather than in a custom API server.
- **Components:** the Flutter app (UI and local cache), Postgres (tables, views and row level security), Supabase Auth (accounts), and an Edge Function plus scheduled job that keep the menu filled.
- **Technologies:** Flutter/Dart with `supabase_flutter` and `shared_preferences` on the client; Postgres, Supabase Auth, Deno Edge Functions, `pg_cron` and `pg_net` on the server.
- **Data flow:** Nutrislice → sync function → menu tables → `daily_menu` view → app; user ratings flow the other way, from the app into `ratings`.
