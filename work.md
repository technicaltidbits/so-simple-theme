---
layout: post
title: "Work"
---

Since becoming a technical writer, I've worked on a number of projects, including [style guide development](#style-guide-management) and implementing [docs-as-code methodologies](#implementing-linters-for-documentation) to help developers write quality documentation.

keywords: internal process improvement

Here's the problem
How I fixed it
This is my role

## [Tech Elevator's Student Book](https://book.techelevator.com)

visual???

I edited the company's reference material for our students. The textbook covers Java and C#, SQL, client and server-side APIs, and front-end web development. This project took four months to complete.

Results: a more consistent writing style, significant reduction in typos and other errors in the book, reduced bug reports from instructors

## Style guide management

We adopted the Google Developer Documentation Style Guide (GDDSG) as our default style guide in 2018. It served our needs for the most part, but over time, I noticed that it lacked guidance in several areas.

Because the GDDSG didn't provide us with the guidance we needed, our documentation remained inconsistent at times. We'd also make documentation decisions during our team meetings, but we had nowhere to document these decisions.

The solution was to create a customized style guide for my team, but one that only covered what we needed it to.

If you'd like to learn more about how I built a customized style guide for my team, you can watch my presentation at Write the Docs Portland 2021: "[Building a style guide from the ground up: lessons learned from a lone writer](https://www.youtube.com/watch?v=PkK1lowfeFU)."


## Testing tutorials

As a technical writer, one of my 

* making assumptions
* not clear when you're supposed to do something
* testing for technical accuracy, instructions are easy to follow, no gaps in material, do the instructions work, audience-appropriate writing
* reported failing instructions, noted steps to reproduce issue
* quality assurance methodology -> test case template, bug reporting

## User guides ???

* wrote two user guides for two different audiences for one of our B2B clients
* minimum viable documentation
* what was that process like?
* site design and content structure (why did I choose VuePress over any other site)?
  * there were no conversations around site design, tool, how it's organized
  * site design and tool decision first, then content structure, then drafting, then SMEs reviews, then edits, then delivery


## Implementing linters for documentation

Our documentation didn't have a consistent writing style, voice, or tone, mostly because multiple people contributed to the documentation. We needed some way to ensure that all writers wrote documentation in the same writing style, adhered to spelling conventions, and used the same terminology. Essentially, we needed to implement some automated way of checking prose.

I implemented [Vale](https://errata.ai), an open-source grammar and style linter, for our two documentation repositories. Vale is highly customizable and supports creating custom tests that you can run against your writing.

Implementing the linter involved adding it to our repositories, running it against existing content, and then editing that content so it adhered to our style guide conventions.

When I ran Vale against our content for the first time, it reported:

* Repository 1: 409 errors, 5225 warnings and 4756 suggestions in 413 files.
* Repository 2: 336 errors, 2576 warnings, and 3241 suggestions in 55 files.

After two months of work, I reduced the amount of errors by 56% and the amount of warnings 50% for repository 1. Errors in repository 2 decreased 86% and warnings 36%. If I had a chance to redo the project, I'd have more success with a longer timeline.

As our team grew, I eventually moved us from using the command-line tool to [Vale Server](https://docs.errata.ai/vale-server/install/), a desktop application with functionality similar to the CLI, but with features that help you manage multiple projects and configurations.