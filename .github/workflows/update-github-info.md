---
name: update-github-info
description: Keep the GitHub Info website current with practical updates from the GitHub Blog and Changelog.
on:
  schedule:
    - cron: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona] "
    reviewers:
      - monalisa
---

# Update GitHub Info

Keep `site/content/github-info.md` current with concise, useful information for developers learning GitHub.

## Instructions

1. Read `notes/mona-notes.md` and follow its guidance for tone, sourcing, and review.
2. Use the web-fetch tool to fetch `https://github.blog/latest/`, `https://github.blog/changelog/`, and `https://awesome-copilot.github.com/workflows/`.
3. Review the current `site/content/github-info.md`. Add or update only timely, practical information supported by those sources. Keep summaries short, avoid duplicate items, and identify whether each update came from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.
4. Use the edit tool to update `site/content/github-info.md` only when there is a useful change to make.
5. If you made a change, propose it with the create-pull-request safe output and request Mona (`monalisa`) as the reviewer. Do not write directly to the default branch or merge the pull request.
6. If none of the sources contain a useful update, leave the file unchanged and do not open an empty pull request.