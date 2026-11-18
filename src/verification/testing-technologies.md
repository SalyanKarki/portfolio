# Testing technologies

## Sample

- **Location:** _(choose a test file that uses an advanced tool. My current code has no tests of its own; see the plan below.)_
- **My contribution:** _(describe.)_

## Discussion

- **Planned, fixture-based tests:** `nutrislice.ts` is pure functions on purpose ("so they can be tested against saved JSON"), so Deno's test runner could check parsing against saved real Nutrislice responses.
- **Planned, dependency injection with fakes:** `ProfileScreen` accepts its data functions as parameters, so widget tests can run without a network.
- **Planned, coverage tooling:** `flutter test --coverage` measures what the tests reach. My profile code is currently near 0%.
- **Future use:** _(where you'd use these techniques again.)_
