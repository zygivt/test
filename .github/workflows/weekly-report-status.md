---
name: Weekly Report Status
on:
  schedule: weekly on monday
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
engine: copilot
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

Create one concise weekly activity report for this repository covering the previous 7 days.

## Scope

- Commits merged or pushed in the last 7 days.
- Issues opened and issues closed in the last 7 days.
- Pull requests opened, merged, and closed in the last 7 days.

## Report requirements

- Keep the report brief, factual, and scannable.
- Include key counts for commits, issues, and pull requests.
- Mention a few notable items only when they are materially relevant.
- If there was no activity in any category, explicitly state: "No activity in the previous 7 days" for that category.

## Output

Publish the report as a new issue using the `create_issue` safe output.
Use a short, descriptive title and include the full report in the issue body.
