# Themes

Select a theme with the `theme` query parameter:

```text
https://<your-host>/api?username=YOUR_USERNAME&theme=github_light
```

Unknown theme names silently fall back to `github_dark`.

## Available themes

| Name           | Description |
| -------------- | ----------- |
| `github_dark`  | Dark card matching GitHub's dark theme (default). |
| `github_light` | Light card matching GitHub's light theme. |

## Adding a theme

1. Open `src/lib/themes.ts`.
2. Add an entry to the `themes` object. Every field in `ThemeColors` is required:

   ```ts
   my_theme: {
     background: '#ffffff',
     cardBackground: '#f6f8fa',
     border: '#d0d7de',
     title: '#0a3069',
     text: '#24292f',
     textSecondary: '#57606a',
     accent: '#0a3069',
     accentSecondary: '#1a7f37',
     iconColor: '#57606a',
     contributionLevels: ['#ebedf0', '#9be9a8', '#40c463', '#30a14e', '#216e39'],
   },
   ```

3. Add a row to the table above.
4. Verify the card renders correctly in the web UI and through the API.

`contributionLevels` is an ordered list of five colours from least to most active, used for the contribution graph.
