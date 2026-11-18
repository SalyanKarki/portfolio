# Self-learning

## Sample

- **Location:** my Supabase tutorial, [`docs/supabase-setup.md`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/docs/supabase-setup.md) (setup, lines 1–71; rules for changing the database, lines 72–91; menu sync, lines 92–101; troubleshooting, lines 102 onward).
- **My contribution:** I wrote the guide (commits `c09fb8e` and `d2cb503`) while learning Supabase myself. _(Note any AI help here.)_

## Discussion

- **The technology:** Supabase is a hosted Postgres database with authentication, auto-generated APIs and serverless Edge Functions. It is our entire backend.
- **Strengths:** we got auth, a REST API and row level security without writing a server, and the CLI keeps the schema in git.
- **Weaknesses:** security lives in SQL policies that are easy to get wrong, Edge Functions use Deno rather than Node, and a shared remote database means one teammate's bad migration affects everyone.
- **Compared with other tools:** _(compare with Firebase or another backend you've used.)_
- **Sticking point:** editing tables in the dashboard instead of through migrations makes the repo and database drift apart. The guide's "Rules for changing the database" section is my fix.
