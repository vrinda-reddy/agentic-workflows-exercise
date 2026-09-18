---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Information

Refresh `site/content/github-info.md` for Mona and propose the changes in a pull request.

## Sources and repository guidance

1. Read `notes/mona-notes.md`.
2. Use the `web-fetch` tool to read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
    - https://awesome-copilot.github.com/workflows/
3. Use GitHub repository API tools to read repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for that repository guidance.

## Update and review

1. Update `site/content/github-info.md` with accurate, concise information based on the notes and fetched sources.
2. Preserve the existing file format and avoid unrelated changes.
3. Review the resulting diff for correctness and completeness.
4. Use the `create-pull-request` safe output to open a pull request for Mona to review. Do not write directly to `main`.