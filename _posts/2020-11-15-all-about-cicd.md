---
layout: post
title: "Learning about docs and CI/CD"
image:
   path: /images/cicd.png
   caption: "[The CI/CD process](https://www.axonactive.com/blog/why-ci-cd-improve-our-efficiency/)"
excerpt: "There's one thing I've been focused on learning lately: continuous integration (CI) and continuous deployment (CD)."
tags: [continuous deployment, continuous integration, sdlc, testing, bitbucket pipelines]
---

Lately, I've been focused on learning about continuous integration (CI) and continuous deployment (CD). The main reason I'm interested in it is because I want to find some way to automate testing our documentation. Using a CI service might be the way to go.

Naturally, one of the best ways to learn something is to write about it. So, here I go.

# Continuous integration

From what I understand, continuous integration is essentially building and testing code. Teams of developers push code changes to a repository throughout the day, and a CI service—like Travis CI or Bitbucket pipelines—builds the code and runs tests. If the build succeeds (meaning all tests pass), the changes can be deployed to production.

One of the biggest benefits of continuous integration is that it helps to reduce production bugs. No one likes to see bug reports come in immediately after a release. For one, it's just not a good feeling.

But more importantly, production bugs are costly. Developers have to spend time debugging and fixing errors instead of working on a new feature. Also consider that someone has to reach out to the users to let them know they're working on the issue, constant status updates, writing release notes...at the end of the day, it's lost time.

> Okay, what about documentation?

If your documentation is in the same repository as your code, your CI service can also build your documentation upon each push to your repository.

You can also run linters in continuous integration. Teams might use linters like Vale or write-good to check their documentation for grammar, style, and readability. They can also use the [markdown-link-check](https://github.com/tcort/markdown-link-check) tool to make sure that there are no broken links in their documentation.

# Continuous deployment

Continuous deployment means...well..continuously deploying code to production.

Unlike continuous delivery, this process is completely automated. With continuous delivery, someone has to manually trigger a new release to production. With continuous deployment, once a build succeeds, the changes are immediately deployed to production.

# CI/CD pipelines

One term I encountered when researching CI/CD is *pipeline*. In CI/CD, a pipeline does the work of building code, running tests, and deploying the changes.

Here's how Buildkite defines pipelines:

>"A pipeline is a template of the steps you want to run. There are many types of steps, some run scripts, some define conditional logic, and others wait for user input."

A pipeline tends to have a `build` stage, a `test` stage, and a `deploy` stage. In the `build` stage, you can add steps that install any dependencies and build your application. In the `test` stage, you'd add steps that runs tests against your code. In the `deploy` stage, you'd add steps that deploy your application to production, assuming your build succeeds.

You usually define your pipeline steps in a `.yaml` file that's stored in the root of your repository. If you're using Bitbucket, for example, your pipeline file is usually called `.bitbucket-pipelines.yml`.

The structure of a pipeline file tends to vary from service to service, but generally, building, testing, and deploying are the three major stages.

> What about documentation?

In the `build` stage, you'll probably want to include steps that build your documentation. For example, if you use [Vuepress](https://vuepress.vuejs.org/) for your documentation, you'll want into include a step that runs `vuepress build` to build the documentation files.

You might also add steps that install linters, like Vale, or tools like HTMLProofer that validate your HTML output.

In the `test` stage, you'd add steps that actually runs these tools against your documentation. If there are any grammar errors, faulty links, or even finds errors in sample code, the build fails.

# Reflection

What I'd like to do, I think, is use Vale with Bitbucket pipelines. The developers I work with are the ones who write first drafts of our documentation; perhaps upon each push to our shared repository, Bitbucket pipelines can run Vale and a Markdown link checker to look for any grammar, syntax, or style errors, and then deliver a report to let them know what errors (if any) were found.

There's so much to learn here. Like I said, I'll probably revisit this post as I gain a greater understanding of CI/CI and pipelines.

## Sources

Here's a list of all the various sources I used to help me write this post:

* [CI/CD: Continuous Integration & Delivery Explained](https://semaphoreci.com/cicd)
* [What’s the Difference Between Continuous Integration, Continuous Deployment and Continuous Delivery?](https://semaphoreci.com/blog/2017/07/27/what-is-the-difference-between-continuous-integration-continuous-deployment-and-continuous-delivery.html)
* [Job Lifecycle](https://docs.travis-ci.com/user/job-lifecycle/)
* [Continuous integration](https://www.thoughtworks.com/continuous-integration)
* [Continuous Integration Essentials](https://codeship.com/continuous-integration-essentials#:~:text=Continuous%20Integration%20(CI)%20is%20a,CI%20it%20is%20typically%20implied.)