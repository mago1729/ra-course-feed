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

## jobs.json

Written daily by a second routine. Same append-only rule: items are never removed, the history is the duplicate check. The app hides items older than 45 days or past their deadline.

```json
{
  "updated": "2026-10-23",
  "items": [
    {
      "id": "boehringer-senior-ra-manager-vet-2026-10",
      "title": "Senior Regulatory Affairs Manager, Veterinary Medicines",
      "company": "Boehringer Ingelheim Vetmedica",
      "location": "Ingelheim, Germany",
      "remote": false,
      "level": "senior",
      "lang": "English, German",
      "posted": "2026-10-20",
      "deadline": "",
      "url": "https://...",
      "source": "company careers page",
      "why": "Senior EU vet medicines role at a target employer, hybrid in Germany.",
      "added": "2026-10-23"
    }
  ]
}
```

Rules the routine follows:

- `id` is stable: company slug, role slug and year-month. The same posting seen again on another site is the same `id`.
- `level` is one of senior, lead, manager, specialist, head.
- `posted` is the date on the posting when shown, otherwise an empty string. `deadline` is the application deadline when shown.
- `url` must be the posting itself (company page or job board), verified to load.
- `why` is one sentence written to the reader, plain words, no dashes.
