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
- `for`: `general` (everyone), or a Maa Family profile: `homemaker`, `student`, `farmer`, `business`, `driver`, `teacher`, `officeIt`, `dailyWorker`, `retired`. Deen Saathi uses `general` only.
- `te`, `en`: plain text only, no links or HTML, at most 200 characters each. Both are required; an item missing either is skipped.
- `source`: `own`, or the author / reference (Deen Saathi: the Quran or hadith reference; every line scholar-reviewed before it is added).
- Keep the last 5 weeks in the file (so a new phone also gets last month), plus up to a month ahead. Remove older items.

## How the apps use it

- With the switch on, the app checks the file once a day (downloads only when it changed) and keeps the lines on the phone: always the coming week, and the whole file when it is under 100 KB (normally a month or more).
- For each day, the app shows: today's line from the feed; if there is none, the line from the same date last month (from what it kept); if there is none, its built-in lines.
- The app keeps the last 2 months on the phone for that fallback. Switch off deletes everything it downloaded.

## Rules

Nothing about loans, interest, betting, crypto, medicines or politics. Health lines stay general (water, walking, sleep).
