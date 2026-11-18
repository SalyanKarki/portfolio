# Security

## Sample

- **Location:** [`20261013000000_user_schema.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261013000000_user_schema.sql) (Grinnell-only sign-up, lines 37–58; row level security, lines 151–189; username-only updates, lines 167–168), the sync secret check in [`sync-menu/index.ts`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/functions/sync-menu/index.ts) (lines 18–21), and secrets in [`20261022000000_menu_sync.sql`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/migrations/20261022000000_menu_sync.sql) (lines 6–7 and 31–32).
- **My contribution:** I wrote these migrations and the sync function. _(Note any AI help here.)_

## Discussion

- **Surface area:** the login and sign-up form, rating and profile actions, the public Supabase REST API (anyone with the publishable key can call it), and the sync function's URL.
- **Threat, impersonation:** a user edits or deletes someone else's ratings. **Handled:** row level security only lets users change their own rows.
- **Threat, outsiders:** non-students create accounts. **Handled:** a sign-up trigger rejects any email that isn't @grinnell.edu.
- **Threat, sync abuse:** an attacker triggers the menu sync repeatedly. **Handled:** the function requires a secret header, and the secret is stored in Vault.
- **Threat, leaked keys:** the service-role key bypasses all security. **Handled:** it exists only server-side, and `.env` is git-ignored.
- **Open risk:** anonymous ratings could be spammed to skew averages. _(Triage: rate limiting or requiring sign-in.)_
