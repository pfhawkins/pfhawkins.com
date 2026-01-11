---
author: pfhawkins
categories:
  - thought
date: 2008-08-11T11:38:10Z
slug: stupid-simple-bibsonomy-to-delicious-migration
status: publish
tags:
  - api
  - bibsonomy
  - bookmarks
  - delicious
  - project
  - python
  - REST
title: Stupid Simple Bibsonomy to Delicious Migration
url: /2008/08/11/stupid-simple-bibsonomy-to-delicious-migration/
wordpress_id: "45"
---

A while back I switched from [delicious](https://delicious.com) to
[bibsonomy](https://bibsonomy.org) to handle all my social bookmarking needs. I
was all taken in by the RDF backing. I decided recently to switch back, since
it didn't have the user base and general ecosystem, it's geared toward more
academic pursuits, and RDF isn't all it's cracked up to be. Here's a tarball
of the scripts I used to move the bookmarks back into delicious:

Download: [bib2del](/bib2del.tgz)

## Caveats

1. bibsonomy handles unicode characters, delicious doesn't. I opted to delete/edit the few bibsonomy bookmarks that were giving me those errors, but it will error out when you pass delicious a title with a smart apostrophe, smart quotes, em-dash, or other non-ascii character.
2. It is a dumb script. It will take all your bibsonomy bookmarks and add them one by one, with a 1.1 second delay in between to keep delicious happy. If, for some reason, you pass delicious a unicode character and it errors out, it will attempt to readd all the bookmarks you successfully added the last go round.
3. You will need to ask bibsonomy nicely for a developer's api key. delicious only needs username and password.

I could have written something that stored the bibsonomy bookmarks locally,
cleaned up the unicode, and then pushed everything to delicious, but this does
99% of what I wanted it to do.

I'd like to give a shout-out to two fabulous webservices that allow RESTful
api access to the information they store on my behalf, and to those brave
souls who wrote python bindings to those apis.

P.S. Not only does delicious choke on unicode, but it stores tags as
space-delimited strings. Strings! Boggles the mind, it does.
