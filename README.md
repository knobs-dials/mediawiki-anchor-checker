# mediawiki-anchor-checker

Checks whether internal links will work as expected:
- checks whether internal mediawiki links with an #anchor match a header in the target page
- checks duplicate section names

Does not persist anything, which implies it is only reasonably to run on small wikis. 
It checks my ~1000-page wiki in a minute, which is more that good enough for me.

...but you DON'T want to run this on wikipedia in its current form.
You'ld want a lot more work to, say, avoid unconditionally refetching six million pages every run.


# Dependencies

- pywikibot, which is doing most of the heavy lifting, 
- networkx, which makes it easier to select links we _can_ while we're still fetching


# Setup

Understand pywikibot's user-config.py well enough to tell it about your wiki.

See e.g. https://www.mediawiki.org/wiki/Manual:Pywikibot/user-config.py and https://www.mediawiki.org/wiki/Manual:Pywikibot/Use_on_third-party_wikis

# TODO: 
- figure out how to deal with redirects
- discover page names as we go (right now we hope that prefix search for [a-z0-9] gets most things)
- consider removing the threading, it's probably not worth the complexity. This is one example where concurrency is good enough and you don't really need parallelism
- follow mediawiki behaviour more directly, e.g. the fact that it allows to have spaces in the anchor even though they argably should be underscores
