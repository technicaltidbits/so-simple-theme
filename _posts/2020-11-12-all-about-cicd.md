---
layout: post
title: "About docs and CI/CD"
image:
   path: /images/cicd.png
   caption: "[The CI/CD process](https://www.axonactive.com/blog/why-ci-cd-improve-our-efficiency/)"
---
There's one thing I've been focused on learning lately: continuous integration (CI) and continuous deployment (CD). Out of all the things I've learned about software development, CI/CD is the one thing I don't know very well. The main reason I'm interested in it is because I want to find some way to test my team's docs using Vale, and it seems that continuous integration is the way to go.

Naturally, one of the best ways to learn something is to write about it. So here I go.

# Continuous integration

From what I understand, continuous integration is building and testing code. You push small snippets of code to your codebase, and a pipeline (containing several scripts) builds and tests your code. Your code needs to pass all tests and conform to whatever code standards your team has to pass the tests.

One of the benefits of continuous integration is that code is continuously checked, all day, every day. That way, when it comes time to release software, you're not shipping broken code because it's been thoroughly tested.

Okay, so that's code: what about docs? How does it apply here?

For docs, continuous integration means that written content is constantly tested, too. Teams might use linters, like Vale or write-good, to check their docs for grammar, style, and readability. They might use the [markdown-link-check](https://github.com/tcort/markdown-link-check) tool to make sure that there are no broken links in their documentation (because broken links can ruin a user's experience with your docs).

The pipeline can also build your docs upon each push to the repository. It might fail to build because of grammar or style errors, or there might be bad syntax in your `config.js` file. Again, the benefit of continuous integration is that you're catching these errors early before the docs are published.

# Continuous deployment

Continuous deployment means...well..continuously deploying code to production.

Unlike continuous delivery, this process is completely automated. With continuous delivery, someone has to manually trigger a new release to production. With continuous deployment, as soon as a pull request is merged, the CI/CD process does the rest of the work.

In your pipeline, you can configure how and where to deploy your code and doc files.

# Using pipelines

Pipelines are how you can build, test, and deploy code and doc files to production. 
