# Domain-specific architecture

## Sample

- **Location:** [`supabase/migrations/20261012000000_menu_schema.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261012000000_menu_schema.sql) (the `foods` table, lines 27–39; `menu_items`, lines 59–71), [`sync-menu/index.ts`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/functions/sync-menu/index.ts) (lines 48–79) and the cron job in [`20261022000000_menu_sync.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261022000000_menu_sync.sql) (lines 35–50).
- **My contribution:** I designed the schema and wrote the sync function and schedule. _(Note any AI help here.)_

## Discussion

- **Domain quirk:** dining-hall dishes repeat across days, so I split them like Letterboxd's films and showings: `foods` is what gets rated, and `menu_items` records when each dish is served.
- **External data:** the menu comes from Grinnell's public Nutrislice API, so Nutrislice's own ids are our primary keys, which makes every sync an idempotent upsert.
- **Changing menus:** the sync deletes items the dining hall removed from a day (`index.ts` lines 66–75) and replaces allergen tags, so stale data disappears.
- **Timing:** a weekly `pg_cron` job fetches this week and next, using dates in Grinnell's time zone (`todayInGrinnell`), so the app always has upcoming menus.
