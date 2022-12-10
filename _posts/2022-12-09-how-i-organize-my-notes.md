---
layout: post
title: How I organize my notes
date: 2022-12-09 21:01:00
description:
tags:
categories: note-taking
---

**TL;DR:** I'm mixing two approaches called PARA and Zettelkasten to create a folder structure for my notes. PARA helps me structure what I'm actively working on, whereas Zettelkasten helps me connect the dots between ideas and concepts.

![](/assets/img/2022-12-09-how-i-organize-my-notes-obsidian.png){: style="display: block; margin-left: auto; margin-right: auto; width: 80%;" }

There is no secret that note-taking is a productive habit shared by many great thinkers, writers, scientists, or artists.
But organizing one's notes is also a key part of making them useful and actionable in our daily work.
Usually, this is where people struggle the most when they start taking notes seriously.

Where should I put my notes? How should I classify them? What should I keep and what should I discard?
There are so many questions that it can be overwhelming.
I have been struggling with this myself over the years, and I have tried many different approaches.
In this piece, I will share my current approach, which I have been using for more than a year now.
I start by explaining the general principles I follow, which might sound pretty abstract, but bear with me. Then, I share how exactly this applies to my notes, which I manage with a program called Obsidian (but it can work for similar applications).
If you are already familiar with concepts like PARA and Zettelkasten, you can skip to the [last section](#mixing-para-and-zettelkasten).

# Organizing by purpose

First of all, you should ask yourself: what is the purpose of my notes? what cool it help me do?
Here are some examples of purposes:

- To better **remember** something important to you, such as a quote, a fact, a personal memory, etc.
- To **share** something that would be useful to others, such as meeting notes, ideas, etc.
- To **plan** something, such as a project, a trip, etc.
- To **write** something, such as a blog post, etc.
- To **outline** something, such as a book, etc.
- To **think** through something, such as a problem, etc.

There are a lot of possible purposes, but I think you get the idea.
The reason why I think it is useful to understand which purpose your notes serve is that it will help you decide how to organize them.

A key distinction is that some of them are more **actionable** than others.
A note on some fact you read might never be useful to you again, but a note on a project will likely be used again and again while you work it, to keep track of the next tasks for example.
The general principle is that you want to keep the more actionable notes close to you, while the non-actionable ones can be kept in a separate place to not get in the way unless you explicitly want to discover them.

This distinction is best captured by the **PARA approach**, created by Tiago Forte [^1].
PARA stands for "Projects — Areas — Resources — Archives", which refers to the folders one must create to organize files and notes.

- **Projects** have deadlines, they are the most actionable. For example, it could be to write a blog post or to develop an application.
- **Areas** are responsibilities that we commit to for some indefinite time. For example, it could be your health, a particular work responsibility, or a hobby.
- **Resources** are project-independent knowledge that is not actionable. For example, a note on a fact or idea that struck you, that might be useful in the future but does not fit any specific project or area.
- **Archives** are where we move anything that is not relevant anymore (from projects, areas, or resources). By moving it away from the main folders, we make sure we don't get distracted by it, but at the same time, we can still access it if ever needed.

Tiago Forte suggests that you move notes from one folder to another as their purpose changes.
Say you have a note on "AI Alignment" in the "Resources" folder, something you find interesting, took some note on, but that does not relate to anything you actively work on.
Now, suppose that you start working on a software project that relates to "AI Alignment". According to the PARA method, you should move it to that project's folder (which is itself in a "Projects" folder containing all your active projects).

Personally, I don't find it very convenient to move the notes between folders.
I prefer to keep my notes in the same place, but connect them through wikilinks. An idea will always be somewhere in the "Resources" folder but referenced in the note on my software project. This also solves the problem of resources used by 2 projects at the same time.
The only time I move a note is when I archive it, which I do for projects and areas that are not active or relevant anymore.

# Connecting the dots

To really understand something, you need to connect it to other things you know.
Similarly, original ideas don't appear out of the blue, but rather as a rearrangement or elaboration from things we already understand well enough.
Therefore, your notes should be organized in a way that facilitates these connections.
How to do this? Well, make it a graph of notes!
Each note is a node, and you link it by hyperlinks to other notes.

This might sound a bit abstract, so let me give you an example. Here are two of my notes, which are nothing but Markdown files:

```
# Anchoring bias

- Anchoring bias or effect states that we tend to rely more heavily on information
  that was acquired early on, or on a first guess that we had made
- It is a pervasive [[Cognitive bias]] that has a strong effect on decision-making.
  It can influence negotiations and even courtroom judgments.
- There are several possible explanations for it, depending on whether the anchor
  comes from us ([[Anchor-and-adjust hypothesis]]) or from
  someone else ([[Selective accessibility hypothesis]]) [^1]

[^1]: [[2021-12-05 Why we tend to rely heavily upon the first piece of information
        we receive]]
```

```
# Anchor-and-adjust hypothesis

- The Anchor-and-adjust hypothesis postulates that when we adjust our estimate
  after making a guess on something, these adjustments tend to be small, as if
  we tried not to deviate too much from our initial estimate. [^1]
- It is a possible explanation of the [[Anchoring bias]] it the case of people
  generating the anchor on their own.

[^1]: Tversky, A., & Kahneman, D. (1974). Judgment under uncertainty: Heuristics
      and biases. _Science_, _185_, 1124-1131. https://doi.org/10.21236/ad0767426
```

The first note is about a concept, the "Anchoring bias". My goal is not to re-create the Wikipedia page on Anchoring bias, but rather give me a quick reminder as to what it is about.
Inside the explanation, the concept of the "Anchor-and-adjust hypothesis" gets mentioned. To keep the note short, I created a separate note on this hypothesis and linked it to my first note.
And vice versa, the note on the "Anchor-and-adjust hypothesis" also links to the note on the "Anchoring bias", to provide the context.

All these links are created using the `[[wikilink]]` syntax, which is supported by many note-taking apps.
Most apps can also give you backlinks, that is the list of notes that point to a particular one.
From my note on "Cognitive bias", it can see that I have a note on "Anchoring bias", as well as many other cognitive biases for which I wrote a note.
This is very powerful because you don't even have to create a system of rigid categories for your notes, they can emerge organically from your links.

You might also have noticed that the first note has a footnote reference with a wikilink.
This is a link to a note on an article, which provided the source for that tidbit of information.
But how exactly do you go from reading an article to writing all these conceptual notes?
This is where the Zettelkasten method comes in.

# From literature to evergreen notes

> "Without the (Zettelkasten) notes, that is, by only thinking, I would not come up with such ideas. Of course, my head is necessary to write down the insights, but it can't take all the credit" — Niklas Luhmann

![](/assets/img/2022-12-09-how-i-organize-my-notes-zettelkasten.jpeg){: style="display: block; margin-left: auto; margin-right: auto; width: 80%;" }

_Zettelkasten_ might sound like a strange name, but it is actually the German word for "slip box", a small box where you put index cards.
Zettelkasten is also the name of a note-taking method developed by Niklas Luhmann, a prolific German sociologist.
Luhmann would read an article, write a note on it on an index card, and put it in his bibliographic slip box.
This **literature note** would be extremely short: a few sentences, or even just a few words that struck his interest, as well as the bibliographic reference.
The goal here is to remember what he found interesting exactly and to be able to find that article again.
Regularly, he would process his most recent additions and think about their relevance to his own thinking and writing.
Then, his personal elaboration or comments on a specific idea would go into a separate note, called **permanent note**, which he would put in his main slip box.
Of course, with the index card size constraints, he would have to be very concise and limit himself to a very specific idea for each card.
But thanks to a smart system of note identifiers, he would simply create a series of related notes, or a hierarchy of them (not unlike a mind map).

Reproducing this exact system digitally would not make much sense, but the general principles are still very relevant.
Essentially, the Zettelkasten method is about having a process to **capture some raw notes** (literature notes) in one place, then **curate, refine, connect them into bite-size pieces that make sense to us** (permanent notes), because we re-phrased it with our own words.
Actually, permanent notes don't mean they can change. That is why I prefer the concept of **evergreen note** from Andy Matuschak [^4]. Like a plant, it can grow and evolve over time. It does not have to be systematic, you can let serendipity do its work and update the note when you stumble upon it.

# Mixing PARA and Zettelkasten

Now that you have a general idea of both methods, let's see how I combine them.
I use a note-taking app called [Obsidian](https://obsidian.md/), which works on top of folders containing Markdown files.
The root folder looks like this:

```
.
├── 001 📥 inbox/
├── 010 📚 biblio/
├── 011 💡 main/
├── 020 🏃 projects/
│   └── backlog/
├── 030 🗺️ areas/
├── 040 📰 journal/
├── 080 💾 archives/
│   ├── areas/
│   └── projects/
├── 090 🏗️ templates/
├── 091 📎 attachments/
├── 093 IW-Queues/
└── 094 hypothesis/
```

The numbering is an old trick to sort the folders like I want to.
Note that I'm leaving some leeway in case I ever want to insert something in between.

The inbox is simply a space to put unfinished notes, typically bibliographic notes for a book I'm currently reading but I'm not done with.

Then come the **slip boxes**, the bibliographic (`010 📚 biblio/`) and the main one (`011 💡 main/`), as in Luhmann's system.
Inside them there is **no sub-folders**, as I don't want to enforce a rigid structure.
I simply put all my notes directly under these folders and make use of wikilinks or special notes to navigate them.
However, I do use some prefixes in the filenames, in some cases.

- I use an `@` prefix before the name of a person I wrote a note on.
- I use a date prefix in `YYYY-MM-DD` for all literature notes, because I find it useful to keep track of when I read a particular piece, or when I wrote a temporary note for myself. Even though they live in separate folders, it also helps to discriminate between literature and evergreen notes.

In the previous section you saw examples of evergreen notes, here is one example of literature notes:

```markdown
- Title: `How to Take Smart Notes: One Simple Technique to Boost Writing, Learning and Thinking – for Students, Academics and Nonfiction Book Writers`
- [Link](https://www.amazon.com/How-Take-Smart-Notes-Nonfiction/dp/1542866502)
- Author: [[@Sönke Ahrens]]
- Tags: [[Zettelkasten]]
- Discovery date: [[2021-11-13]]
- Discovered via: [[@Bryan Jenks]]'s videos
- Publication year: [[2017]]

# What did I learn?

# Notes

- Writing does not start with a blank page but writing notes in preparation for the actual essay or article
- Lots of courses on how to write, but none focusing on writing notes effectively
- Should not use your willpower, but create an environment or system where you can work without forcing yourself
...

# Follow-up links

# Flashcards
```

Note that I don't necessarily fill all the sections. Having them pre-defined from a template works more like a guide for things I might want to add.

The 2 next folders are my active PARA projects (`020 🏃 projects/`) and areas (`030 🗺️ areas/`).
Each area and each project will be represented by a single file.
I don't use sub-folders, except one for separating a backlog with projects that I'm planning to start soon.
Having one note file for each project may sound unpractical at first, but I manage to make it work by referencing other more specific notes. Typically, a meeting for a particular project will have its own literature note, e.g., `2022-12-07 Meeting with John Smith on Project Z`. Or I may be referencing an idea or concept, which has an evergreen note in my main slip box.
All these notes can be referenced from the project note, or if they have a reference back to the project note I can easily find them.
It can even be done automatically: Using an awesome plugin called Dataview, I can dynamically all the literature notes that mention my project.

The `040 📰 journal/` is a folder for journaling, where I keep daily, weekly and yearly notes. I could almost have put them in the bibliographic slip box since they also have this temporal aspect, but I prefer to keep them separate because the purpose is distinct.
A daily note will remind me of this week's goal, let me write the 3 important things to do for the day, and also review how the day went: what went well, what didn't, what I learned, etc. I use a template for this, which makes the process very straightforward.
Similarly, my weekly note will contain and plan for the week, as well as a review section that aggregates the daily notes.
I don't use a monthly note, but I do have a yearly note which contains sections for each month.
There is nothing particularly fancy about these journal notes, the key thing is to have a regular practice of reviewing and planning, which is a lot about setting a few templates to make it as frictionless as possible.

The `080 💾 archives/` folder is the Archive side of the PARA method, to keep old areas and projects that are not active anymore.
I don't really feel the need to ever archive a "Resource" (a note from either of my slip boxes).
The only reason I do move my areas and projects to the archive is simply as a way to distinguish them from the active ones in my queries. Typically, I could have used tags for that instead.

The last folders starting with `09` are reserved for extra tools, things that don't fit with PARA or Zettelkasten.

The `090 🏗️ templates/` folder contains all sorts of templates. Each template provide a predefined structure for a given kind of note. This is saving me a lot of time to capture ideas quickly!

The `091 📎 attachments/` folder is where I keep all files that aren't notes, such as PDFs, images, etc. Basically, I will use a wikilink with a special syntax to embed a particular file in a note. But to be honest, I don't really use this much and my workflow is not very optimized.

`093 IW-Queues/` and `094 hypothesis/` are related to some specific plugins I use, and I won't go into details here.

And voilà, this is how my notes are currently organized.
The folder structure is purposely kept simple, and I'm relying a lot on wikilinks and search to navigate my notes.
I hope you found it interesting and that it will inspire you to try out something similar!

[^1]: [The PARA Method: A Universal System for Organizing Digital Information](https://fortelabs.com/blog/para/)
[^2]: [Introduction to the Zettelkasten Method](https://zettelkasten.de/introduction/)
[^3]: "How to Take Smart Notes", Sönke Ahrens, 2017
[^4]: https://notes.andymatuschak.org/Evergreen_notes
