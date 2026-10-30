# Self-hosting

GitHub Metrics is a Next.js app. It renders cards on demand and needs a GitHub token to do so.

## Requirements

- Node.js 18 or newer
- A GitHub token (classic PAT with `read:user` is enough)

## Local

```bash
npm install
cp .env.example .env.local
# edit .env.local and set GITHUB_TOKEN
npm run dev
```

The dev server runs at <http://localhost:3000>. Request a card at `/api?username=YOUR_USERNAME`.

## Production

```bash
npm install
npm run build
npm start
```

Set `GITHUB_TOKEN` in the environment before starting. Do not commit it.

## Environment variables

| Variable       | Required | Description |
| -------------- | -------- | ----------- |
| `GITHUB_TOKEN` | yes      | Token used for GitHub GraphQL requests. |

## Vercel

1. Import the repository into Vercel.
2. Add `GITHUB_TOKEN` under Project Settings → Environment Variables.
3. Deploy. The default build command and Next.js preset work without changes.

## Notes

- Cards are cached for one hour, which keeps API usage low. Raise or lower it in `src/app/api/route.ts` if needed.
- Analytics are enabled via `@vercel/analytics`. Remove the `<Analytics />` component in `src/app/layout.tsx` if you do not want them.
