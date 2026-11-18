# CSC 324 Portfolio

My portfolio for CSC 324, built with [mdBook](https://rust-lang.github.io/mdBook/).
Each competency has its own page under `src/`, and `src/SUMMARY.md` sets the sidebar order.

## Publishing

`.github/workflows/deploy.yml` builds the site and publishes it to GitHub Pages
on every push to `main`. In the repo's **Settings > Pages**, set **Source** to
**GitHub Actions** once.

## Previewing locally (optional)

Install mdBook (`cargo install mdbook`, or download a release from
https://github.com/rust-lang/mdBook/releases), then run `mdbook serve --open`.
