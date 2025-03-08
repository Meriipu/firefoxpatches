# Background

Currently applies to firefox-esr-128.8

These patches attemts to restore the dropdown arrow of the urlbar from
before firefox 77. They work in conjunction with userChrome.css and userprefs
so that the arrow is available, while still making it possible to make the
urlbar not expand when clicked or focused (although it will expand if text
is typed into it).

# Patch descriptions

## Restore old behaviour single-clicks and double-clicks in the searchbar/urlbar

* 0001-restore-click-selection-behaviour-to-urlbar-and-sear.patch

Restores the linux behaviour of doubleclicking in the urlbar and searchbar
to select the entire url (as opposed to needing to click three times).

## Restore the old urlbar dropdown menu when clicking the dropmarker

* 0002-revert-the-removal-of-the-dropmarker-et-al.patch
* 0003-skip-the-topsites-provider-due-to-horrible-priority-.patch
* 0004-do-not-auto-open-urlbar-on-focus.patch

## Allow minimum tab-widths smaller than the enormous default value

* 0005-A-minimum-tab-width-IS-a-minimum-tab-width.patch

The default minimum is set to some ridiculously high value which causes
the list of tabs to overflow and start scrolling if you visit more than
a handful of sites.

## Remove trash from the right-click context menu

* 0006-Removed-from-contextmenu.patch

## Disable intrusive suggestions from being injected into the urlbar

* 0007-Disable-interventions-without-using-policies.json.patch
* 0009-one-offs-display-none.patch

## Hardcode search engines to exclude sponsored ones from being added randomly

* 0008-Stop-resetting-search-engines-on-update.patch

## Miscellaneous about:config prefs

* prefs

Some (but not all) of these are likely out of date and no longer used for anything.

TODO: Add my own prefs for other useful stuff to keep better track of them.

## Styling-fixes via userChrome.css

* userChrome.css 
