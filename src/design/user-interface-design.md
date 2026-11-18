# User interface design

## Sample

- **Location:** the profile screen (on my `profile-screen` branch, not yet pushed): `lib/profile/profile_screen.dart` (favorite slots, lines 255–316; expandable history with sort chips, lines 337–401) and `lib/profile/rating_histogram.dart`.
- **My contribution:** I designed the screen (Letterboxd-style top four, rating distribution, expandable history with sorting), and Claude Code (AI) wrote the code from that design. _(Adjust as needed.)_

## Discussion

- **Platform guidelines:** it uses Material 3 components throughout (cards, choice chips, bottom sheets, snackbars) with the app's existing green and orange colors.
- **Domain conventions:** it follows Letterboxd, which users already know: four poster-shaped favorites, a ½–5 star histogram, and a diary-style rating list.
- **Feedback:** pinning a favorite updates instantly, and if saving fails it reverts and shows a snackbar. Tapping a histogram bar shows its count.
- **Progressive disclosure:** only the four newest ratings show at first; "See all" expands the full history and its sort options in place.
- **Alternative considered:** a separate full-history page. Expanding in place won because it keeps context and doesn't need extra navigation.
