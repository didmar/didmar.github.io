---
layout: page
title: Habitsync
description: Cross-device Habit Tracking App
img: assets/img/habitsync.png
importance: 1
category: personal
---

Stack: Typescript, [React](https://reactjs.org), [Ionic framework](https://ionicframework.com), [Capacitor](https://capacitorjs.com/), [Firestore](https://cloud.google.com/firestore)

Code on [GitHub](https://github.com/didmar/habitsync)

![](/assets/img/habitsync.png){: style="display: block; margin-left: auto; margin-right: auto; width: 80%; border: solid white 1px;" }

# Problem

I'm a big fan of habit tracking and I've been using [this app](https://github.com/iSoron/uhabits) on Android for years. But I always wanted to be able to tick off my habits from my computer as well, or even automate some of the tickings through API calls (making it less likely to cheat!).

The goal of this project was to create a habit-tracking app that:

- Is multi-platform: desktop, web and Android (optionally iOS)
- Can work offline
- Synchronizes data bi-directionally
- Enables programmatic integrations from outside the app

# Solution

For the application part, my first idea was to use [Elm](https://elm-lang.org/) to generate JS code and combine it with [Electron](https://www.electronjs.org/), a popular framework for creating "native apps" with web technologies.
But the drawback of Electron is that it is very resource intensive because it embeds the Chromium browser which runs behind the scenes. Therefore, this approach is more appropriate for desktop apps, although it is perfectly possible to create mobile apps with it.

I found out about Ionic, a framework for building [Progressive Web Apps (PWA)](https://web.dev/progressive-web-apps/). PWAs support offline mode and can be installed on mobile devices as a native app. Using it with React is pretty straightforward, even though I did not have that much prior experience with either of them.

For the storage and synchronization part, I wanted to make things as simple as possible and not have to code a server nor host the server and the database myself.
[Firestore](https://cloud.google.com/firestore), a NoSQL database from Google, was the perfect solution for this. I already experimented with it for a YouTube analytics project and the developer experience was great.
For a personal project like this, the free tier is more than enough (up to 50k read and 20k write requests per day).
Also, it can be used like an API such that I didn't have to code a backend at all. However, I would not recommend doing this for a more critical application, because a malicious user could mess up their data by sending inconsistent updates to the database.

Transforming the web app into an Android app was super simple thanks to a native runtime called [Capacitor](https://capacitorjs.com/). I haven't tried to build an iOS app, but in theory, it should be possible.

Finally, I made a simple Python script to export habit data from my current app and import it into Firestore.

The application is functional for my needs, further improvements would be managing multiple users and adding stats (like streaks) and graphs. I did not try programmatically using the app yet, but this can be done quick-and-dirty by sending update requests to Firestore or more cleanly using Google Cloud Functions.

# Challenges

The biggest challenge was to get the hang of how Ionic handles offline and synchronization, configuring the service worker properly.
For some reason, the very convenient "offline mode" toggle in the Chrome Developer tools did not work for simulating being offline: the updates I made while offline would never be synchronized afterward.
To test everything, I ended up juggling between toggling roaming on and off on my phone, and checking what was happening in Firestore and another instance of the app on my desktop. This was not ideal, but it worked.

The other challenge was CSS... I still managed to make it look decent enough!