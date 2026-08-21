---
name: New Day
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
engine: copilot
tools:
  edit:
safe-outputs:
  create-pull-request:
    allowed-files:
      - index.html
    max: 1
---

# New Day

Use the workflow run's UTC date as the source of truth.

Update only `index.html` and do not modify `styles.css`.

## Required update behavior

1. Read `index.html` and follow the existing Daily Updates HTML structure exactly.
2. Follow existing ID conventions and wording patterns for date labels and dialog header text.
3. Add a new Daily Updates navigation control for the workflow run date in UTC.
4. Add a matching accessible `<dialog>` for that same date.
5. The dialog must clearly confirm the daily update ran.
6. Preserve every existing daily update and dialog.
7. Do not duplicate anything:
   - If the UTC date is already present in Daily Updates navigation and has a matching dialog, make no change.
   - Never add a second copy of an existing date, navigation control, or dialog.

## Accessibility and consistency requirements

- Keep `aria-haspopup="dialog"`, `aria-controls`, and `data-dialog-trigger` on the new navigation button.
- Keep dialog `id`, `aria-labelledby`, and `aria-describedby` consistent with existing conventions.
- Ensure dialog heading and description IDs match the new date-based naming convention used in the file.
- Keep the close control pattern identical to existing dialogs.

## Change boundaries

- Allowed file changes: `index.html` only.
- Do not remove or rewrite existing daily updates.
- Make the smallest possible edit when adding a new date.
- If no change is needed because the UTC date already exists, leave the repository unchanged.
