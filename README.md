# mediawiki-anchor-checker

Checks whether internal mediawiki links with an #anchor match a header in the target page. Also reports duplicate sections, because that was easy.

Does not persist anything, which implies only works reasonably on small wikis - it checks my ~1000-page wiki in a minute, which is more that good enough for me.
...but you don't want to run this on wikipedia without a lot more work to, say, not refetch six million pages every run.


# Dependencies

- pywikibot, which is doing most of the heavy lifting, 
- networkx, making 


# Setup

Understand pywikibot's user-config.py well enough to tell it about your wiki.

See https://www.mediawiki.org/wiki/Manual:Pywikibot/user-config.py


# TODO: 
- considering removing the need for networkx
- considering removing the threading, it's probably not worth the complexity
