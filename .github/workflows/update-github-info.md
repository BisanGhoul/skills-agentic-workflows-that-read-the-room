---
name: update-github-info
engine:
  id: codex
  model: gpt-5-mini
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
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
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` before making changes.

Web-fetch all three sources:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Identify recent updates that are useful to developers and fit the site's practical GitHub guidance. Update only `site/content/github-info.md`, keeping summaries short and preserving its existing editorial direction. Include a source link for every item drawn from any of the listed sources. Do not invent details.

Open a pull request for Mona to review using the `create-pull-request` safe output. Use a pull request title that mentions Mona or GitHub Info. Keep the pull request focused, describe the sources and changes, and state that it is for Mona to review. Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request`. Do not merge the pull request or modify any other files.