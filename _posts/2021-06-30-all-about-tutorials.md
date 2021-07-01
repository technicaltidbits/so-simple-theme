---
layout: post
title: "Templates, templates, and more templates"
excerpt: "About flexing my template writing skills through the Good Docs project"
tags: [templates, writing, the good docs project]
---

Several awesome things happened after I gave my talk at WTD 2021:

1. I met a lot of great people on Twitter.
2. My confidence as a technical writer went 📈
3. I learned more about [The Good Docs Project](https://thegooddocsproject.dev/).

I learned about The Good Docs Project for the first time at last year's Write the Docs conference. The Good Docs Project is all about providing templates and writing instructions for documenting open source software. I actually used their style guide template as the basis for the style guide at my job.

After attending The Good Docs Project's unconference session at WTD 2021, I decided that I wanted to learn more about how to develop documentation templates. I was particularly interested in learning how to develop tutorial templates. I spend a lot of my time testing our tutorials at work.

So far it's been a great experience *and* I've started working on a few tutorial templates. I'm just coming out of the research phase of developing the templates.

## The three tutorial types

So I initially thought about just developing one tutorial template. But as I thought about it some more, and after talking with other folks, I wasn't sure if just *one* template would suffice because there are so many different types of tutorials.

For example, there are "quickstart" or "hello world" tutorials: these tutorials are shorter, usually meant to help users get started. They may be installation-focused, and they're task-based. A good example is immuneML's [quickstart tutorials](https://docs.immuneml.uio.no/latest/quickstart.html).

Then, there are what I'm calling "modular" tutorials. They're task-based, but not installation-focused. Instead, they're focused teaching users about some particular feature of a product or about some coding concept, like lists. They can stand alone *or* be part of what I'm calling "deep dive tutorials." Users should have completed the "hello world" tutorial before starting these.

"Deep dive" tutorials are usually longer, project-based, and feature-focused. Deep dive tutorials are for users who are looking to do a deep dive into some feature of a product or coding concept. They may present users with some hypothetical situation or starter project to help guide their learning. A good example is React's [Intro to React](https://reactjs.org/tutorial/tutorial.html) tutorial. These tutorials could also be comprised of several modular tutorials.

Scale is the differentiator here.

## What's next

I generally feel confident with these tutorial types. The next step is to start writing drafts of the templates and to think about what sections each tutorial template needs.

For example, the "hello world" tutorial will probably require some section that gives an overview of the product, language, or framework. The "modular" and "deep dive" tutorials might not need that section, or if I include them, the description should be very brief, because I'm assuming that you've completed the "hello world" tutorial and understand a thing or two about the product.

The "modular" and "hello world" tutorials will require step headings, but the "deep dive" tutorials probably won't (at least the way I'm thinking about it, as having more of a "reference" feel).

Lots to think about here. But I'm enjoying it! Hopefully I'll have some drafts ready to go soon.


