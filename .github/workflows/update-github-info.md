---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[Mona] "
---

# Update Mona's GitHub Info Website

Keep `site/content/github-info.md` current with concise, practical guidance for GitHub developers.

## Sources

1. Read `notes/mona-notes.md` and `site/content/github-info.md` through GitHub repository API tools. Do not use terminal, CLI, shell, or sandboxed commands to read repository files or guidance.
2. Use `web-fetch` to read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. Select only recent, relevant items that support practical guidance for Mona's audience. Verify details and dates against the official pages; do not invent or infer unsupported claims.

## Update

Use the edit tool to update `site/content/github-info.md`. Preserve its existing structure and editorial themes, keep summaries short and practical, and include the source link whenever information comes from the GitHub Blog or Changelog. If there is no meaningful update, leave the file unchanged and do not open a pull request.

## Review

Review the resulting diff to confirm it only changes `site/content/github-info.md`, that each new claim is supported by a cited official source, and that the content follows `notes/mona-notes.md`. When there is a meaningful update, request a pull request with a clear summary for Mona to review. Do not write directly to `main`; use the configured `create-pull-request` safe output.