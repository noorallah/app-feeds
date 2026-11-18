# app-feeds

Daily lines for our offline Android apps. The apps read these files only when the
user turns on the optional online switch (off by default). The apps send nothing;
GitHub only sees the phone's IP address when the file is downloaded.

| App | File | Address |
|---|---|---|
| Maa Family | `maa-family/messages.json` | https://noorallah.github.io/app-feeds/maa-family/messages.json |
| Deen Saathi | `deen-saathi/lines.json` | https://noorallah.github.io/app-feeds/deen-saathi/lines.json |

## Format

```json
{
  "version": 1,
  "items": [
    { "date": "2026-12-01", "for": "all",
      "te": "చిన్న పొదుపు, పెద్ద భరోసా.",
      "en": "Small savings, big security.",
      "source": "own" }
  ]
}
```

- `date`: `YYYY-MM-DD`, one item per day per `for`. Post up to a month ahead.
- `for`: `all`, or a profile (Maa Family: `homemaker`, `student`, `farmer`, `worker`, `business`, `retired`).
- `te`, `en`: plain text only, no links or HTML, at most 200 characters each. Both are required; an item missing either is skipped.
- `source`: `own`, or the author / reference (Deen Saathi: the Quran or hadith reference; every line scholar-reviewed before it is added).
- A day with no item: the app uses its built-in lines.
- Keep the file small: remove items older than 30 days.

## Rules

Nothing about loans, interest, betting, crypto, medicines or politics. Health lines stay general (water, walking, sleep).
