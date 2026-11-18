# Medium-scale abstraction

## Sample

- **Location:** [fakeletterboxd](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd), [`supabase/functions/sync-menu/nutrislice.ts`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/functions/sync-menu/nutrislice.ts) (the `MenuBatch` class, lines 29–97, and the fetch helpers, lines 99–128), used by [`index.ts`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/supabase/functions/sync-menu/index.ts) lines 30–43.
- **My contribution:** I wrote both files in commit `d2cb503`, merged through PR #37. _(Note any AI help here.)_

```ts
// Everything scraped in one run, deduplicated by id so each upsert touches a
// row at most once.
export class MenuBatch {
  meals = new Map<number, MealRow>();
  foods = new Map<number, FoodRow>();
  menuItems = new Map<number, MenuItemRow>();
  ...
  addWeek(meal: MealRow, week: any) { ... }
}
```

## Discussion

- **What it abstracts:** Nutrislice's deeply nested JSON (days → menu items → foods → allergen icons) becomes flat rows that match our tables one-to-one.
- **How:** `MenuBatch.addWeek` collects rows into maps keyed by Nutrislice id, so duplicates collapse automatically, and the module exposes only typed row interfaces (`FoodRow`, `MenuItemRow`, ...).
- **Separation of concerns:** `nutrislice.ts` is pure parsing with no database access, while `index.ts` only fetches and upserts, so either side can change without touching the other.
- **Purpose in the program:** the rest of the app never sees Nutrislice's format; the Flutter app just reads the `daily_menu` view.
