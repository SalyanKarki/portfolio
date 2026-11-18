# Testing strategies

## Sample

- **Location:** the profile feature I added (on my `profile-screen` branch, not yet pushed): `lib/profile/profile_data.dart` (178 lines), `lib/profile/profile_screen.dart` (504 lines) and `lib/profile/rating_histogram.dart` (108 lines).
- **My contribution:** I specified the profile feature and directed its implementation, which Claude Code (AI) generated. _(Adjust to describe exactly what you wrote, tested or reviewed.)_

## Discussion

- **Coverage today:** `flutter test --coverage` reports about 1 of 343 profile lines covered (`profile_data.dart` 0/81, `profile_screen.dart` 1/218, `rating_histogram.dart` 0/44), so this component is effectively untested so far.
- **Designed for testing:** the sorting and histogram logic (`sortReviews`, `starDistribution`, `starText`) are pure functions, which suits plain unit tests.
- **Planned widget tests:** `ProfileScreen` takes its loaders and savers as constructor parameters (lines 12–28), so widget tests can pass fakes instead of Supabase.
- **Not covered, and why:** the Supabase query functions (`fetchMyReviews`, `setTopFood`, ...) need a live database, so I'd rely on manual testing or a local Supabase instance for them.
- **Next step:** add unit tests for sorting and the histogram, and widget tests for expanding the history and pinning favorites.
