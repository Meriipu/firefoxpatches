# Currently applies to firefox-88

# Patch descriptions
* 0001-restore-click-selection-behaviour-to-searchbar.patch

restore the linux behaviour of doubleclicking in the urlbar and searchbar
to select the entire url (as opposed to needing to click three times).
<br/><br/>
* 0002-hardcode-to-never-strip-https.patch

This patch hardcodes the removed behaviour to never strip https.
<br/><br/>

* 0003-revert-the-removal-of-the-dropmarker-et-al.patch
* 0004-skip-the-topsites-provider-due-to-horrible-priority-.patch
* 0005-do-not-auto-open-urlbar-on-focus.patch

These patches attemts to restore the dropdown arrow of the urlbar from
before firefox 77 [now fixed to work with 88]. They work in conjunction
with userChrome.css and userprefs so that the arrow is available, while
still making it possible to make the urlbar not expand when clicked or
focused (although it will expand if text is typed into it).
<br/><br/>
* 0006-A-minimum-tab-width-IS-a-minimum-tab-width.patch
* 0007-Removed-from-contextmenu.patch
* 0008-Disable-interventions-without-using-policies.json.patch
* 0009-Stop-resetting-search-engines-on-update.patch
* 0010-one-offs-display-none.patch

Annoyances with urlbar and misc

<br/><br/>
* userChrome.css 

contains some styling to make the bar not grow in size when clicked.
<br/><br/>
* prefs

Contains the relevant about:config options being used.
