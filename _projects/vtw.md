---
layout: page
title: Visible Thoughts Writer
description:
img: assets/img/vtw_thumbnail.png
importance: 1
category: work
---

Stack: Typescript, [React](https://reactjs.org), [Firebase](https://firebase.google.com/), [Material UI](https://mui.com/core/), [SlateJS](https://www.slatejs.org/)

![](/assets/img/vtw.png){: style="display: block; margin-left: auto; margin-right: auto; width: 80%;" }

[MIRI](https://intelligence.org/) is a non-profit research institute that aims to promote and develop friendly artificial intelligence.
I worked with them to **develop a tool to create datasets collaboratively** for the [Visible Thoughts Project](https://intelligence.org/2021/11/29/visible-thoughts-project-and-bounty-announcement/).

# Context

The [Visible Thoughts Project](https://intelligence.org/2021/11/29/visible-thoughts-project-and-bounty-announcement/) is an AI-alignment project that attempts at training an AI that could explain its reasoning.

Language models like OpenAI's ChatGPT are trained on large datasets of text and can be used to **generate very convincing texts from an initial prompt**.
For example, it can be used to continue a story, and this was the basis for [AI Dungeon](https://play.aidungeon.io), a text-based role-playing game where the dungeon master is an AI.
But the **generated text could be offensive or dangerous**. Even if we set up some counter-measures like profanity detection, with the current models we simply can't anticipate all the possible problems.

MIRI researchers hypothesize that **if we could train a language model on a dataset that contains intermediary "thoughts", it would be much easier to understand why it came up with a particular sentence** and correct the model from there.
For this experiment, MIRI started to create a dataset of "thought-annotated dungeon runs", which is similar to the output of the text-based role-playing game, except that the dungeon master explains everything that happens in the game world. For example, why does a character react in a certain way to the protagonist's action, how did that character feel or think...

# Problem

Such a dataset did not previously exist and must be created from scratch, so MIRI started looking for contributors.
**Scaling this project became a challenge**: players and dungeon masters must coordinate to write a run, but without the player seeing the "thoughts", which excludes using a tool like Google Docs. The runs also have a specific format that must be enforced. Finally, reviewers need to annotate some parts to have the dungeon master correct things accordingly to ensure the data quality.

This is where my work started.

# Solution

Visible Thoughts Writer (VTW) is an interface for players and dungeon masters to create "thought-annotated dungeon runs".

Users can create runs and invite other users to play on them.
Each run is made of a series of steps, which each have a set of sections (prompts, thoughts, ...).
The users write or edit these sections using a custom text editor.
Similarly to a messaging application, users are notified when it is their turn to play.
The data can also be exported as a JSON file and re-imported back as a new run.

Under the hood, this is a web app using [React](https://reactjs.org) and [Firebase](https://firebase.google.com/) (Hosting, Firestore, Authentication and Cloud Functions).
The text editor is built using [SlateJS](https://www.slatejs.org/), a React framework for building rich text editors.
For the UI, I used [Material UI](https://mui.com/core/), a React component library.

# Challenges

I must say that this was my first professional project using React, and I learned a lot (and even more since!).
That also means that the code is far from perfect, and I would do things differently now.
For example, I would create more hooks to separate the logic from the components, and maybe use React Query on top of Firebase to manage the data fetching.

The most challenging part was the **rich-text editor**.
SlateJS is a very powerful framework, but it took me a while to get the exact behavior I wanted.

![](/assets/img/vtw_composer.png){: style="display: block; margin-left: auto; margin-right: auto; width: 80%;" }

For example, a thought section contains bullets, each of which is composed of thoughts delimited by end-of-sentence characters.
Each thought has a type, that corresponds to a particular formatting (e.g., color).
Removing the end-of-sentence character collapses the two thoughts into one, keeping the type of the first one.
Similarly, collapsing two bullets into one merges the thoughts of the second bullet into the first one.
Things like bullets with no thoughts but some end-of-sentence characters must also be prevented by the editor...

There are many such constraints, and they **must be handled indirectly** by overriding a `normalizeNode` callback function.
In order words, you need to fix the document structure _a posteriori_, which is not ideal.
Adding such "fixes" would sometime break other (more important) things!