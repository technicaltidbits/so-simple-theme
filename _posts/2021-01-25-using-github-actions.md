---
layout: post
title: "On using GitHub actions"
excerpt: "My thoughts around using GitHub workflows for testing prose."
tags: [github, github actions, documentation, testing]
---

I mentioned in my previous post that I wanted to focus on learning more about CI/CD this year. One way to do that, I figured, was to set up CI/CD for this site.

I initially wanted to use Travis CI because I was familiar with it, but after a conversation with other technical writers in the Write the Docs slack channel, some folks suggested that I use GitHub Actions since my source code is hosted there.

> GitHub Actions allows you to create custom software development workflows for your repository. For example, you can create a workflow that runs anytime someone opens a pull request in your repository. A workflow consists of a series of **jobs**, like building your repository or scanning your code for any bugs or vulnerabilities. And those jobs consist of several **steps**.

It took me a while to get through the documentation and fix a few bugs, but I got a few workflows set up over the weekend. Here's what I learned.

## Setting up workflows

All of your GitHub workflows belong in the `.github/workflows` directory in your repository. Each workflow is its own `.yml` file. Here's my directory structure:

```
.
├── build-directory-test.yml
├── link-checker.yml
└── vale.yml
```

Just three workflows right now: one that makes sure my site builds, another to check all links in my Markdown files, and another to check spelling, grammar, and style. At some point, I'll probably combine these all into one file called `doc_tests.yml`.

### Workflow structure

Each workflow generally follows the same structure. Here's my Vale workflow:

```
name: linting
on: push
jobs:
  build:
    if: "!contains(github.event.commits[0].message, '[skip ci]')"
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Get Changed Files
        id: get_changed_files
        uses: jitterbit/get-changed-files@v1
        with:
          format: 'json'
      - name: Vale
        uses: errata-ai/vale-action@v1.3.0
        with:
          files: '${{ steps.get_changed_files.outputs.added_modified }}'
        env:
          GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
```