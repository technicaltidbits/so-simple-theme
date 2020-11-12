---
layout: post
title: "Testing docs with Vale - Part 3: Running the CLI"
tags: [sample project, testing, QA, vale, documentation]
excerpt: In this part, you'll create a `.vale.ini` file, customize it, and apply styles to some Markdown prose.
---

In this series, you'll learn how to configure and customize Vale to lint Markdown files.

Part 1: Installing the Vale CLI\
Part 2: Configuring the Vale CLI

In this part, you'll create a `.vale.ini` file, customize it, and apply styles to some Markdown prose.

> Assumptions I'm making: you have some familiarity with the command line.

## Prerequisites

* A code editor, like VS Code, Sublime, or Atom
* The Vale-compatible implementation of the Microsoft Style Guide, which you can download [here](https://github.com/errata-ai/Microsoft/releases/download/v0.7.0/Microsoft.zip)

## Step 1: Create project folder

In the terminal, create a new folder called `vale-tutorial`:

```bash
$ mkdir vale-tutorial
```

## Step 2: Add project files

Change directories to the `vale-tutorial` folder:

```bash
$ cd vale-tutorial
```

Create a `.vale.ini` file in the `vale-tutorial` folder:

```bash
$ touch .vale.ini
```

Next, create a Markdown file called `sample-file` in the `vale-tutorial` folder:

```bash
$ touch sample-file.md
```

Finally, create a `styles` folder:

```bash
$ mkdir styles
```

Your project structure now looks like this:
```
vale-tutorial
├── .vale.ini
├── sample-file.md
└── styles
```

## Step 3: Add Microsoft styles to styles folder

Download and open the zip file containing the Vale-compatible implementation of the Microsoft Writing Style Guide. Then move the `Microsoft` folder to the `styles` folder. Now, your project structure looks like this:

```
vale-tutorial
├── .vale.ini
├── sample-file.md
└── styles
    └── Microsoft
```

## Step 4: Edit the .vale.ini file in your code editor

Open your code editor now, and open the `vale-tutorial` folder. Click on the `.vale.ini` file to edit it. The first property to add is `StylesPath`.

### StylesPath

In the `.vale.ini` file, set the `StylesPath` to `styles`. Remember: this is where you tell Vale where to look for any third-party styles.

### MinAlertLevel

Next, set `MinAlertLevel` to `suggestions`. If you remember, you can set this value to show errors, errors and warnings, or errors, warnings, and suggestions.

### BasedOnStyles

Set `BasedOnStyles` to `Vale, Microsoft`. Don't forget to add [\*] so these styles are applied to all files.

Your `.vale.ini` file looks like this once you're done:

```ini
StylesPath = styles

MinAlertLevel = suggestions

[*] //don't forget the asterisk!
BasedOnStyles = Vale, Microsoft
```

## Step 5: Add content to sample-file.md

Copy these three paragraphs and paste them into the `sample-file.md` file:

> `This is a sampl file that we can use to tst the Vale CLI. There are 2 things that you need to know about using it. Ergo There are plenty of cool things you can do with this linter...`

> `In this tutorial, you will learn how to install Vale, a style linter this tool allows you to tst your doc file for style and grammar.`

> `When a software developr tests their code, he may test the application's functionality or look for any security issues in their code. When technical writers test their documentation, we may check to assure that the links are not broken, the style is consistent, and that there are not grammar, spelling, or punctuation errors.`

## Step 6: Run the linter

From the terminal, run the command `vale sample-file.md`. You'll see the errors, warnings, and suggestions Vale finds in the files, in addition to the number of errors, warnings, and suggestions:

```ini
6 errors, 4 warnings and 5 suggestions in 1 file.
```

### The results

`Vale.Spelling` identified several typos:

```ini
1:11   error       Did you really mean 'sampl'?    Vale.Spelling
1:41   error       Did you really mean 'tst'?      Vale.Spelling
4:94   error       Did you really mean 'tst'?      Vale.Spelling
6:17   error       Did you really mean             Vale.Spelling
                    'developr'?
```

`Microsoft.We` identified use of the first-person pronoun "we." `Microsoft.Vocab` caught several words that aren't on the word list:

```ini
 1:27   warning     Try to avoid using              Microsoft.We
                    first-person plural like 'we'.
 2:83   suggestion  Verify your use of 'cool' with  Microsoft.Vocab
                    the A-Z word list.
 6:200  suggestion  Verify your use of 'assure'     Microsoft.Vocab
                    with the A-Z word list.
```

Notice that the `Vale.Spelling` has `error` level severity, while `Microsoft.Vocab` has `suggestion` level severity. This is how the rules are structured when you first download them, but you can change them, if you want. I'll talk about this in the next tutorial.

## Key takeaways

* Your `.vale.ini` file is 1) required and 2) controls Vale's behavior.
* Your `.vale.ini` file should be in the root of your project.
* Any third-party styles should be in your `styles` folder.
* The `.vale.ini` file can be customized to show errors, errors and warnings, or errors, warnings, and suggestions.
* To lint a file, use the command `vale` `filename`, or, if you want to lint many files, `vale` `directory`.

## Conclusion

Now that you have Vale installed on your computer, you can start linting your own files to make sure they're error-free and consistent in style. This doesn't necessarily have to be documentation files, by the way; you can use Vale's default style to help with editing blog posts and emails (I'm using it for blog posts 😁).

Next, you'll learn how to customize a `vale.ini` file and modify style rules!

## Links to learn more

* [Vale's documentation](https://errata-ai.gitbook.io/vale/)
* [Vale's style library](https://github.com/errata-ai/styles)
