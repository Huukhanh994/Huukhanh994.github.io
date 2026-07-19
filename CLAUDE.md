# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal resume / CV / portfolio site for Ho Huu Khanh (Senior Fullstack Developer), served via **GitHub Pages** at `Huukhanh994.github.io`. Built on the third-party **BreezyCV** template (lmpixels) — jQuery-based, no build step, no framework.

## Running / deploying

- No build, bundler, or package manager. Static HTML/CSS/JS served as-is.
- Local preview: open `index.html` directly, or run any static server (e.g. `python3 -m http.server 8000`) from repo root so relative asset paths resolve.
- Deploy: push to `master`. GitHub Pages publishes the branch root automatically. No CI.

## Architecture

- **`index.html`** is the whole single-page app. All primary sections live inside it as anchor targets: `#home`, `#about-me`, `#resume`, `#portfolio`, `#blog`, `#contact`. Navigation is in-page scroll; editing content = editing `index.html`.
- **`blog-*.html`**, **`portfolio-*.html`** are standalone detail pages linked from the SPA, opened in the portfolio/blog lightbox (magnific-popup).
- **`js/main.js`** is the single custom script wiring the vendored jQuery plugins: `owlCarousel` (carousels), `magnificPopup` (portfolio/blog popups), `shuffle` (portfolio filtering), perfect-scrollbar, googlemap. Everything else in `js/` is a vendored library — do not edit those.
- **`css/main.css`** holds all custom styling; the rest of `css/` is vendored (bootstrap-grid, reset, plugin CSS). Load order matters and is fixed in `index.html`'s `<head>`.
- Assets split across `img/` and `images/` (both used — check both when wiring an image).

## Contact form

`contact_form/contact_form.php` handles the contact section via AJAX POST from `main.js`. **This requires PHP + mail() and will NOT run on GitHub Pages** (static-only host) — the form is effectively inert in production. The PHP still contains template-default placeholders (`$from`, `$sendTo`) and a hardcoded reCAPTCHA secret; treat that secret as burned and rotate/replace before any real deployment on a PHP host.

## Conventions

- Content edits are hand-edited HTML — match the existing BreezyCV class names and markup structure rather than restructuring.
- CV/resume links point to external Google Drive; the PDF `SeniorFullstackDeveloper_HoHuuKhanh.pdf` in root is a committed copy.
- `user-api.html` / `user-api` artifacts are leftover branch scratch files, not real pages.
