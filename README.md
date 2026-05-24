# LMS Editing Guide

An interactive, self-contained course that teaches course instructors to **read** our standard
LMS page structure, **recognise** what broke when a page looks wrong, and **put it back** — without
needing to write HTML from scratch.

**Live link:** _(added after first deploy)_

## What's here

| File | Purpose |
|------|---------|
| `index.html` | The whole course (hero, fundamentals + quiz, page anatomy, live sandbox, 4 "spot the break" exercises, cheat sheet). Self-contained — the only file. |

The sample lesson is a harmless made-up topic (the water cycle) that reuses our **real class names
and a faithful subset of our real stylesheet**, so every break behaves exactly like it would on a
live course page — without exposing any real courseware. The sample image (Picsum) and video
(National Science Foundation, via YouTube) are loaded from the public web so there are no broken links.

## How to update it

You don't edit this by hand — **just ask Claude.** For example: *"add a fifth exercise about broken
links"* or *"reword the intro"* or *"the sandbox should also cover tables."* Claude edits the files,
commits, and pushes. GitHub Pages republishes automatically, and the **same link** reflects the change
in about a minute.

If you ever want to edit prose yourself: the headings, paragraphs, quiz questions, and cheat sheet are
plain HTML in `index.html`. The live code samples (the "good code", the broken variants, and the
stylesheet the preview uses) live in one clearly-marked `<script>` block at the bottom labelled
`EDITABLE COURSE DATA`.

## Hosting

Published with GitHub Pages from the `main` branch root. To deploy a fresh copy:

```sh
git init && git add . && git commit -m "Course"
gh repo create lms-html-course --public --source=. --push
gh api -X POST repos/<owner>/lms-html-course/pages -f source.branch=main -f source.path=/
```
