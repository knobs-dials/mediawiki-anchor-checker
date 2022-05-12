# mediawiki-anchor-checker

Checks whether internal mediawiki links with an #anchor match a header in the target page.


Does not store anything beyond the run, so only works reasonably on small wikis - it checks my ~1000-page wiki in a minute, which is more that good enough for me, but you don't want to run this on wikipedia without a lot more work to, say, not refetching six million pages every time...
