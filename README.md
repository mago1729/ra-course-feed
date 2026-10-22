# ra-course-feed

Machine-written feed of training suggestions for a veterinary regulatory-affairs career plan.
A scheduled Claude routine updates `suggestions.json` once a week; a phone app reads it.
This repository holds suggestions only. It contains no personal data.

## suggestions.json

```json
{
  "updated": "2026-10-27",
  "items": [
    {
      "id": "ipi-17193-2027",
      "title": "Veterinary Pharmaceutical Submissions in the EU",
      "provider": "IPI",
      "type": "course",
      "start": "2027-05-17",
      "end": "2027-05-18",
      "format": "online",
      "location": "",
      "price": "GBP 1,299 early-bird until 22 Feb 2027",
      "url": "https://www.ipi.academy/...",
      "why": "Core EU vet submissions training; maps to Phase 2 of the plan.",
      "goal": "ra",
      "added": "2026-10-27"
    }
  ]
}
```

Rules the routine follows:

- `id` is stable and unique (provider + course code or slug + year). Items are never removed, so the history doubles as the duplicate check.
- `type` is one of course, webinar, conference, module, exam, language.
- `goal` is one of ra (EU vet regulatory affairs), pv (pharmacovigilance), german (German C1), network (TOPRA, events), tools (RA automation / coding).
- `start` and `end` are ISO dates when known, otherwise empty strings.
- Keep `why` to one sentence, written for the reader of the app.
- `updated` is the ISO date of the last run.
