# Contributing

Thanks for taking the time to contribute. This project is small, so the process is simple.

## Getting started

1. Fork the repository and clone your fork.
2. Install dependencies:

   ```bash
   npm install
   ```

3. Create `.env.local` from the example and add a GitHub token:

   ```bash
   cp .env.example .env.local
   ```

   `GITHUB_TOKEN` is required. A classic personal access token with `read:user` scope is enough. Without it the app starts but GitHub requests fail.

4. Start the dev server:

   ```bash
   npm run dev
   ```

5. Open <http://localhost:3000>.

## Making changes

- Create a branch from `main` with a descriptive name, e.g. `feat/streak-card` or `fix/light-theme-border`.
- Keep pull requests focused. One feature or fix per PR is easier to review than a bundle of unrelated changes.
- Match the existing code style: TypeScript, functional React components, no comments unless they explain something non-obvious.
- Do not commit secrets. `.env.local`, `.env`, and `.vercel` are gitignored.

## Pull requests

Before opening a PR:

- Run `npm run build` and make sure it succeeds.
- Describe what changed and why.
- Link the related issue, if there is one.
- Include a screenshot or sample card URL for visual changes.

Small fixes (typos, docs, obvious bugs) can go straight to a PR. For larger features, open an issue first so we can agree on the approach.

## Adding a theme

Themes live in `src/lib/themes.ts`. To add one, follow the `ThemeColors` shape in `src/types/index.ts` and register it in the `themes` object. Update `docs/themes.md` with the new name so users can find it.

## Reporting bugs

Open an issue with:

- The username or URL that reproduces the problem.
- What you expected and what actually happened.
- Browser/OS if the issue is in the web UI.

## Documentation

Docs are in `docs/`. If you change the API or add a parameter, update `docs/api.md` in the same PR.
