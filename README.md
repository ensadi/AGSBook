# AGSBook
Game Design with AGS

This repository contains an `mdBook` project for the online book "Game Design with AGS".

## Structure

- `book.toml` — `mdBook` configuration and output settings.
- `src/` — source Markdown files for the book content.
- `docs/` — generated HTML output from the book build.

## Build

### Prerequisites

Install `mdbook` if it is not already available:

```bash
cargo install mdbook
```

### Generate the book

```bash
mdbook build
```

The built site will be written to the `docs/` directory.

### Preview locally

```bash
mdbook serve
```

Then open `http://localhost:3000` in your browser.

## Notes

- The `docs/` directory is the output folder configured in `book.toml`.
- Use `mdbook build` after editing files under `src/` to regenerate the site.

## Read online

https://ensadi.github.io/AGSBook/

Copyright ©2021-2026 Ensadi LLC

