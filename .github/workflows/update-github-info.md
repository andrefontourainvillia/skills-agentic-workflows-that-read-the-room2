---
name: update-github-info
description: Refreshes the GitHub Info website content from the GitHub Blog, Changelog, and Awesome Copilot workflows
on:
  schedule:
    - cron: "0 8 * * *"
  workflow_dispatch:

permissions:
  contents: read

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

tools:
  edit:
  web-fetch:

safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    labels: [automation, github-info]
    draft: false
---

# Update GitHub Info

Keep the GitHub Info website up to date with the latest news from GitHub.

## Steps

1. Read [notes/mona-notes.md](../../notes/mona-notes.md) for Mona's guidance on tone, style, and
   what to prioritize when drafting updates.
2. Fetch `https://github.blog/latest/` to find recent GitHub Blog posts.
3. Fetch `https://github.blog/changelog/` to find recent GitHub Changelog entries.
4. Fetch `https://awesome-copilot.github.com/workflows/` to find notable Awesome Copilot workflows.
5. Update [site/content/github-info.md](../../site/content/github-info.md) with a short,
   practical summary of the most relevant updates from the blog, changelog, and Awesome
   Copilot workflows. Follow Mona's notes: keep summaries short and practical, focus on what
   helps developers learn GitHub faster, and mention the source (GitHub Blog, GitHub
   Changelog, or Awesome Copilot) for each item.
6. Open a pull request with the updated content so Mona can review the changes before they go
   live. Do not push directly to the default branch.

If there is nothing new to report from either source, do not open a pull request.
