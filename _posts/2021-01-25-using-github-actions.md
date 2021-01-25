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

