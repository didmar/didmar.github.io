---
layout: page
title: Furiganalyse
description: Annotate Japanese ebooks with readings
img: assets/img/furiganalyse_kindle.jpg
importance: 3
category: personal
---

Stack: Python, [FastAPI](https://fastapi.tiangolo.com)

Try it [here](http://furiganalyse.itsupera.co)

Code on [GitHub](https://github.com/itsupera/furiganalyse)

![](/assets/img/furiganalyse_app.png){: style="display: block; margin-left: auto; margin-right: auto; width: 80%;" }

# Problem

I love reading Japanese ebooks, but I struggled from the lack of furigana (the readings of kanji characters).
What difference does it make? Here is an example:

- Without readings
> そのため、台湾の人々は「なぜ新型コロナウイルスの対策を厳重にしなければならないか」という理由をよく理解しています。

- With all readings:
> そのため、<ruby>台湾<rt>たいわん</rt></ruby>の<ruby>人々<rt>ひとびと</rt></ruby>は「なぜ<ruby>新型<rt>しんがた</rt></ruby>コロナウイルスの<ruby>対策<rt>たいさく</rt></ruby>を<ruby>厳重<rt>げんじゅう</rt></ruby>にしなければならないか」という<ruby>理由<rt>りゆう</rt></ruby>をよく<ruby>理解<rt>りかい</rt></ruby>しています。

Books intended for adult natives have no readings, because they know how to read the characters (duh!), with the exception of rare words / kanjis.

As a Japanese learner without a lot of reading experience, this means that I would have to look up a lot of words just to check their reading, which takes a few seconds each time on a Kindle and gets in the way of the reading experience.

# Solution

I created a Python library and web app that allows you to upload an ebook, and it will return a copy of that ebook with furigana added... all of them!

I further extended it to export to other formats, such as an [Anki](https://apps.ankiweb.net/) deck (for flashcards) or an HTML file (for reading in a web browser).

![](/assets/img/furiganalyse_kindle.jpg){: style="display: block; margin-left: auto; margin-right: auto; width: 80%;" }

# Challenges

Parsing Japanese text is not trivial: even tokenizing characters into words is not straightforward, because there are no spaces between words, and how words are composed from parts [^1].
But finding the correct reading for each word is even harder, because there are many possible readings for a single word, and the correct reading depends on the context!
I could leverage an [existing library](https://github.com/MikimotoH/furigana) to get started, but I had to improve it a lot and fix many edge cases. Thorough unit testing proved to be very useful.
The results are not perfect, but they are good enough for my use case.

While EPUB is a standard format for ebooks, there are subtle variations with regard to the metadata, the HTML tags used or the encoding. I had to test it on ebooks coming from various sources to deal with all these cases. But I learned a lot about ebook formats in the process!

Finally, a framework like FastAPI is designed for static websites, not for dynamic usages like handling the conversion tasks running in the background (it can take a while for big books!). I made it work with a simple hack: using an AJAX request to poll the status of the task, and redirecting the user to the download page when it is done. I made a minimal example of this [here](https://github.com/didmar/fastapi_ajax_polling).

[^1]: Check out [this great article](https://towardsdatascience.com/how-japanese-tokenizers-work-87ab6b256984) for more details