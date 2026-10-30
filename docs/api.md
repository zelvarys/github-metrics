# API reference

The card is a single SVG served by `GET /api`.

```text
https://<your-host>/api?username=YOUR_USERNAME
```

Example:

```markdown
<div align="center">
  <img src="https://<your-host>/api?username=torvalds&theme=github_dark" alt="GitHub Metrics" />
</div>
```

## Query parameters

| Parameter   | Default       | Description |
| ----------- | ------------- | ----------- |
| `username`  | required      | GitHub username. A `400` is returned if missing. |
| `theme`     | `github_dark` | Card theme. See [themes](themes.md). Unknown names fall back to `github_dark`. |
| `profile`   | `true`        | Show the developer name block. Set `false` to hide. |
| `devscore`  | `true`        | Show the developer score block. Set `false` to hide. |
| `header`    | `true`        | Show the monthly chart block. Set `false` to hide. |
| `stats`     | `true`        | Show the general stats block. Set `false` to hide. |
| `languages` | `true`        | Show the core languages block. Set `false` to hide. |
| `graph`     | `true`        | Show the contribution activity block. Set `false` to hide. |
| `hide_langs`| empty         | Comma-separated language names to exclude, e.g. `Jupyter%20Notebook,TeX`. |

Booleans are disabled with the literal string `false`; any other value keeps the block enabled.

`HTML` and `CSS` are always hidden from the language breakdown.

## Response

- Success: `200` with `Content-Type: image/svg+xml`.
- Missing username: `400` with a plain-text message.
- GitHub or generation error: `500` with a plain-text message.

Successful responses are cached for one hour with `stale-while-revalidate`:

```text
Cache-Control: public, max-age=3600, stale-while-revalidate=600
```

Append a changing query value (for example `&_t=123`) to bypass the cache while previewing.

## Data source

Stats come from the GitHub GraphQL API using the `GITHUB_TOKEN` set on the server. Only public, non-fork repositories owned by the user are counted for stars and languages.
