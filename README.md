AppleScript
===========


## Script 1: Pull note created date from title

This repository contains AppleScripts that enable bulk updating of Evernote note properties.

The first script can be configured to pull date information from the note title and will use it to change the "Created Date" of the note.  The script looks for a default date format YYYY?MM?DD where '?' can be any character (e.g. '-', '.', '/', etc).  The script is configurable to work with a 2 digit year format as well.

The script default is to look for date informaiton at the beginning of the note title string, but can be configured with an offset value if date information is located in the middle or at the end.

Partial date infomation is also handled as follows:

YYYY - sets the Created date to 01/01/YYYY
YYYY?MM - set the Created date to 01/MM/YYYY

Notes not matching established criteria are ignored.

