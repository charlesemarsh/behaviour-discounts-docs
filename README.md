# Behaviour Discounts Docs

Documentation site for Behaviour Discounts, intended to be published with GitHub Pages using the `just-the-docs` theme.

## Structure

- `_config.yml` — Jekyll configuration and theme settings.
- `index.md` — landing page with quick-start guidance.
- `guides/` — step-by-step setup, configuration, and rollout guides.

## Running locally (optional)

1. Install Ruby and Bundler if you want to preview locally.
2. Add the GitHub Pages gems locally (not required for GitHub-hosted builds):
   ```sh
   bundle add github-pages
   bundle exec jekyll serve
   ```
3. Open the served URL (usually `http://localhost:4000`) to preview changes.

GitHub Pages will build the site automatically; local preview is optional.

## Publishing on GitHub Pages

1. Push this repository to GitHub.
2. In **Settings → Pages**, set **Source** to `Deploy from a branch`, choose the default branch (e.g., `main`), and select the root (`/`) or `/docs` if you move the site there.
3. Save; GitHub will build with the provided `_config.yml` and publish to `https://<your-org>.github.io/<repo-name>/`.

## Contributing

- Edit Markdown files and open pull requests.
- Keep examples realistic and scoped to common journeys (first purchase, abandoned cart, retention).
- Add diagrams or screenshots to an `assets/` folder and reference them with relative paths.
