# Accessible design

## Sample

- **Location:** `lib/profile/rating_histogram.dart` (on my `profile-screen` branch, not yet pushed): each bar is wrapped in `Semantics` (lines 40–46), and the caption under the chart repeats the data as text.
- **My contribution:** I designed the profile screen, and Claude Code (AI) wrote the code. _(Adjust as needed.)_

```dart
child: Semantics(
  button: true,
  label: '${starText((bucket + 1) / 2)}: $count',
  ...
```

## Discussion

- **Screen readers:** each histogram bar is announced as a button with its star level and count, so the chart isn't visual-only.
- **Not color alone:** the selected bar changes color, and the count also appears as text below the chart.
- **Contrast:** white text on the dark green favorite tiles keeps contrast high.
- **Validation:** none yet. _(Plan: Flutter's accessibility guideline tests, `meetsGuideline(textContrastGuideline)` and `androidTapTargetGuideline`, plus a TalkBack/VoiceOver pass.)_
