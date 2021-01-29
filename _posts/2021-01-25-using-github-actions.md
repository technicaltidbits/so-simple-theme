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

Each workflow generally follows the same structure. Here's my Vale workflow. I'll break down all the important parts below the code sample.

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

So first, you see the `name` property. This sets the name of the workflow (in this case, "linting").

Next is the `on` property. It defines the GitHub event that triggers the workflow. In this example, a `push` to my blog's repository (on any branch) triggers the "linting" workflow.

If I wanted this workflow to run on every push and pull request, I could change it to:

```
on: [push, pull_request]
```

Next is the main part of the workflow: the `jobs` section.

#### Jobs

In the `jobs` section, there's a job called `build`. Below that is an if statement:

```
if: "!contains(github.event.commits[0].message, '[skip ci]')"
```

This line of code says, "if the comment message does *not* contain the phrase [skip ci], run this job."

Sometimes you may not want a certain workflow to run. For example, if I'm editing a `.yml` file or an `.html` file, I don't want my linting workflow to run, so I'll add "[skip ci]" to the commit message.

Inside the `build` job is the required `runs-on` property, which defines the machine to run the job on:

```bash
runs-on: ubuntu-latest # options include windows-latest or macos-11.0
```

And below that are the `steps` for the `build` job.

#### Steps

You can have any many steps as you want in a workflow; however, the more steps you have, the longer it will take for the workflow to run.

This particular workflow has three steps: "Checkout", "Get Changed Files", and "Vale."

The "Checkout" step essentially checks out the repo.

The "Get Changed File" step
