+++
date = "2016-11-20T20:18:29+00:00"
draft = false
title = "Identity and Cryptography in the Current Year"

+++

I've got about three different lead-ins to this post rattling around my head.
There's the "we don't have flying cars, but we have public-key cryptography
that isn't completely terrible" angle. There's the "truly we are living
in a William Gibson novel" angle. But I think I'll take the "here's a true story
about how [public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)
is being used right this second" angle.
Everybody loves a good anecdote, right?

So there's this fellow by the name of [Michael Anderson](https://keybase.io/microchip).
Big alt-right Trump
supporter type. He tends to approach Twitter the way Leroy Jenkins approaches
WoW raids: big, loud, and in a way that aggravates a large number of the party.
Mr. Anderson has had his account banned repeatedly, both before and after Twitter's
recent [purges of alt-right accounts](http://www.foxnews.com/tech/2016/11/17/twitter-suspends-several-accounts-in-alt-right-purge.html).
But every time his account is suspended for good, he makes a new account and keeps
on trucking.

If you or I had to start a new twitter account, it would take us quite a while
to get the word out that the new account is actually a replacement for the old
account. It would likely take
months to regain just a fraction of the followers. If Twitter didn't grace us
with a blue check mark, some would be skeptical that the new account was ours.
But MicroTurkeyLeaks' few thousand followers
are able to easily find his latest account, even though he's cycled
through as many as three accounts in a _single day_. And what's more, they're
almost positive it's his, even without a blue checkmark.

How does he manage this impressive feat? [keybase.io](https://keybase.io).

Keybase describes itself thusly:

> Keybase maps your identity to your public keys, and vice versa.

Traditional use of PGP (the most popular form of public-key cryptography)
requires [key-signing parties](https://en.wikipedia.org/wiki/Key_signing_party)
in real life in order for people to vouch for each other's PGP identities.
Keybase uses less direct methods of verification. I don't wish to get into the
nitty gritty of cryptographic signing here, but once you have a PGP public key
in keybase's system, you can then sign proofs on various social media accounts,
as well as any websites you run. Others [can then review and sign off on those
proofs](https://keybase.io/docs/server_security/following), building a web of
trust much more easily than with straight PGP.

I've set up a [keybase profile for P.F. Hawkins](https://keybase.io/pfhawkins).
I cannot stress enough that not only has much thought been put into the system,
but it's been the _right_ thought. The process was streamlined, the UX intuitive,
the copy understandable and engaging… I'll stop gushing over it sometime, I
suppose, but only when it (or a system like it) becomes _de rigueur_.

We don't have flying cars, but we now have non-terrible public-key cryptography.
Truly we are living in a William Gibson novel.

<blockquote class="twitter-tweet" data-lang="en"><p lang="de" dir="ltr">Verifying myself: I am pfhawkins on Keybase.io. 0uTF6wyyXhVGK_QGhh2zfFB3RZuW4PrFCE-l / <a href="https://t.co/TVorAyf35g">https://t.co/TVorAyf35g</a></p>&mdash; P.F. Hawkins (@pfhawkins) <a href="https://twitter.com/pfhawkins/status/800045976551563264">November 19, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
