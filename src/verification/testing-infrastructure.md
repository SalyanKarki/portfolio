# Testing infrastructure

## Sample

- **Location:** [`.github/workflows/ci.yml`](https://github.com/grinnell-csc324-fall-2026/fakeletterboxd/blob/main/.github/workflows/ci.yml); my fix is commit `3337462` on the `fix-ci` branch (not yet merged).
- **My contribution:** Lui-Lop added the original CI workflow (PR #18) and miaphoebe adjusted it (PR #36). I wrote the fix that makes CI work on every branch, with help from Claude Code (AI), as noted in the commit's co-author line.

```yaml
# Branches without the Flutter app (docs, database) skip the Flutter steps.
- id: app
  run: echo "flutter=$([ -f pubspec.yaml ] && echo true || echo false)" >> "$GITHUB_OUTPUT"
# pubspec.yaml lists .env as an asset, so it must exist.
- if: steps.app.outputs.flutter == 'true'
  run: if [ -f .env.example ]; then cp .env.example .env; else touch .env; fi
```

## Discussion

- **One click:** `flutter test` (or the VS Code Testing panel) runs the whole suite, and `flutter analyze` checks the code statically.
- **Automatic:** GitHub Actions runs analyze and test on every push and pull request.
- **The problem I hit:** CI failed on branches that had no Flutter app yet (like my database branches) and on branches missing `.env`, which `pubspec.yaml` requires as an asset.
- **How my fix helps:** CI now detects whether the branch contains the app and creates a placeholder `.env`, so failures mean real problems instead of noise.
- **Saved work:** _(describe a specific time CI or the test suite caught a bug for you or the team.)_
