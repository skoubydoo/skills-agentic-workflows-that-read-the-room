---
emoji: "📰"
name: Update GitHub Info
description: Refresh site/content/github-info.md from Mona notes and latest GitHub Blog posts.
on:
  schedule: daily on weekdays
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
strict: true
tools:
  github:
    mode: gh-proxy
    toolsets: [default]
  edit: true
  web-fetch: {}
safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
    reviewers:
      - mona
    draft: false
---

# Update GitHub Info for Mona

## Task

Refresh the GitHub info page with current information and propose changes using a pull request.

1. Read notes/mona-notes.md for voice, framing, and priorities.
2. Fetch and review https://github.blog/latest/.
3. Fetch and review https://github.blog/changelog/.
4. Update only site/content/github-info.md with a concise, well-structured summary of notable updates.
5. Create a pull request using the create-pull-request safe output so changes are proposed on a branch and never written directly to main.
6. In the PR title or body, clearly indicate this update is for Mona to review and include the two source URLs.
7. If there are no meaningful updates, call noop with a brief reason.

## Constraints

- Do not edit any files other than site/content/github-info.md.
- Use only the configured safe output for write operations.