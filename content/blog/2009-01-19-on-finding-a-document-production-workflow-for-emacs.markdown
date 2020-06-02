---
author: pfhawkins
categories:
- essay
date: 2009-01-19T10:48:56Z
slug: on-finding-a-document-production-workflow-for-emacs
status: publish
tags:
- Emacs
- git
- markdown
- pandoc
- writing
title: On Finding a Document Production Workflow for Emacs
url: /2009/01/19/on-finding-a-document-production-workflow-for-emacs/
wordpress_id: "63"
---

I have a modest goal: write some fiction. Instead of actually working toward
accomplishing that goal, I'm going to obsess about the toolchain and other
externalities used to support this endeavor.

I will use revision control. By an accident of history I will be using git.

I will use a text editor. Since I don't want to have to run into frictions
from modal editing while fiction writing, I will be using Emacs.

If fictions were primarily distributed and displayed as [plain-text
files](https://www.gutenberg.org/catalog/), I'd be good to go. They aren't, and
I would like to at least attempt to send this higher up the food chain, ending
in either a Microsoft Word Document or PDF.

Say, LaTeX makes some nice pdfs. While it manifestly does not suck, and
[AucTeX](https://www.gnu.org/software/auctex/) is the bee's knees, I want to do
whatever I can in the way of premature optimization to tilt the ratio of
writing to formatting heavily in writing's favor. LaTeX is formatting heavy,
so I'd like to avoid that.

Docbook XML also suffers from the same issue. It is a well-specced and quite
nice document format. And while [nxml-
mode](https://www.emacswiki.org/emacs/NxmlMode) is bar-none the premier way to
edit straight XML, sorry, it ain't happening.

So, what essentially plain-text formats can I convert to either LaTeX or
Docbook XML, which I can then use to produce my output format of choice? As of
this writing, I see three viable options:

  * [org-mode](https://orgmode.org/)
  * [muse-mode](https://www.gnu.org/software/emacs-muse/)
  * [markdown](https://markdown.infogami.com/) and [pandoc](https://johnmacfarlane.net/pandoc/)
  
org-mode ships with emacs, and is great. Writing novels in it would be
orthogonal to its original purpose in note-taking and agenda-organizing. It
only exports LaTeX/PDF, not Docbook. While it may work, I think successive
options are more promising.

muse-mode is designed from the ground up for publishing, not note-taking. It
exports both LaTeX and Docbook. This would probably be my first choice, except
for one thing: its wiki syntax.

It seems asinine of me to start complaining about a wiki syntax now. I mean,
isn't that the whole point of this exercise, to find a wiki-like syntax I can
convert from? Right. I'm not complaining about **a** wiki syntax, I'm
complaining about **this** wiki syntax. All in all it's not necessarily a bad
one, but it is a domain-specific language for this mode only. [It enjoys no
reuse outside of this particular
application.](https://blog.wired.com/monkeybites/2008/05/a-million-littl.html)
If the third option didn't exist, I'd probably use it anyway.

But we have markdown, and the magical frobnicator that frobnicates markdown
into a potpourri of other formats: namely, pandoc. [Markdown
mode](https://jblevins.org/projects/markdown-mode/) is pretty handy, and I'll
probably end up writing a simple minor-mode or git-hook bash script for
automating the pandoc conversions.

I'll let you know how this turns out.

