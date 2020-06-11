# Now works for firefox-78 (instead of 77)

# Patch descriptions
* 0001-restore-click-selection-behaviour-to-searchbar.patch
* 0002-restore-click-selection-behaviour-to-urlbar.patch

These patches restore the linux behaviour of doubleclicking in the urlbar
to select the entire url (as opposed to needing to click three times).
<br/><br/>
* 0003-hardcode-to-never-strip-https.patch

This patch hardcodes the removed behaviour to never strip https.
<br/><br/>
* 0004-revert-the-removal-of-the-dropmarker-et-al.patch
* 0005-skip-the-topsites-provider-due-to-horrible-priority-.patch
* 0006-do-not-auto-open-on-focus-you-absolute.patch

These patches attemts to restore the dropdown arrow of the urlbar from
before firefox 77 [now fixed to work with 78]. They work in conjunction
with userChrome.css and userprefs so that the arrow is available, while
still making it possible to make the urlbar not expand when clicked or
focused (although it will expand if text is typed into it).
<br/><br/>
* userChrome.css 

contains some styling to make the bar not grow in size when clicked.
<br/><br/>
* prefs

Contains the relevant about:config options being used.

<br/><br/>
There are probably still some quirks leftover that are too tedious to revert,
for instance the overall look of the dropdown menu. It is not the plain wide
one from before but instead a rounded thinner one (though it appears to fit 
the same length of text before the text starts fading, surprisingly).

# Misc/unimportant details about my adventure

* How were the patches for the dropmarker made? patch 0004 and 0005 made?
A combination of adding back lines of code in the commit 
https://github.com/mozilla/gecko-dev/commit/3b8b1171af0c85bd64b38575b7e59a12fcc80d83
```
git log -p 3b8b1171af0c85bd64b38575b7e59a12fcc80d83
```
which did not relate to tests and related to the dropmarker (dropdown arrow),
making as few changes as possible (e.g. by hardcoding values).

And of searching for dropdown marker and other keywords like removed prefs in
the output of the git diff between these two commits:
* https://github.com/mozilla/gecko-dev/commit/c996014ca8d69f8e8a739b19768539cd56dba59c
* https://github.com/mozilla/gecko-dev/commit/4f1ba1ba6728fdea5f21e4aef9e8a62b5f19a166

(which are the commits for firefox 76.0.1 and 77.0.1 respectively, where the
behaviour worked as intended in 76.0.1 but was broken in 77.0.1).

For 78.0.2, https://github.com/mozilla/gecko-dev/commit/35b7f1619d3aa5a61cfca259bea57cef5d28f828
it further broke stuff by first making the original patch not apply
(ok fair enough, that is to be expected), and then by changing up how
providers of search suggestions in the urlbar worked or some stuff like
that (more specifically, making most on-focus and dropmarker searches
use several providers, one of which is topsites provider, which has a
very high priority(?), such that the actually good provider never gets
to return the desirable history-based search results).
A whole bunch of checking the git diff/log and console.prints were used
for that.
