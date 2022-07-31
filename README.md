# mediawiki-anchor-checker

Checks whether internal links within a mediawiki wiki will work as expected:
- checks whether internal mediawiki links with an #anchor match a header in the target page
- checks duplicate section names

First version, doesn't do everyting I want yet.

<br/>
Does not persist anything, which implies it is only reasonably to run on small wikis. 

It checks my ~1000-page wiki in a minute, which is more than good enough for me.
...but you really DON'T want to run this against wikipedia.
You'ld want a lot more work to, say, avoid unconditionally refetching six million pages every run.


# Dependencies
- pywikibot, which is doing most of the heavy lifting, 
- networkx, which makes it easier to select links we _can_ while we're still fetching

Which is covered by `pip3 install networkx pywikibot`


# Setup

Create a `user-config.py` in the same directory. Mine looks something like

        mylang = 'en'
        family = 'placeholder'
        usernames['placeholder']['en'] = 'TestingAnchorBot'
        family_files['placeholder'] = 'https://wiki.example.org/api.php'
For some more explanation, see e.g. https://www.mediawiki.org/wiki/Manual:Pywikibot/user-config.py and https://www.mediawiki.org/wiki/Manual:Pywikibot/Use_on_third-party_wikis


# TODO: 
- stop complaining about non-encoded anchors - mediawiki functins fine with those
- same for redirects, because both name and anchor can vary
- include checks of redirects, in a sensibly-reported way. Including broken redirects.
- add command line parameters

CONSIDER
- discover page names as we go (right now we hope that prefix search for [a-z0-9] gets most things)
- remove the threading, it's probably not worth the complexity. This is one example where back-and-forth sort of concurrency is good enough

