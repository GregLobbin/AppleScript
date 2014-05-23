tell application "Evernote"
--exists "notebook:haystack"
-- count "notebook:haystack"
-- create note title "Note 1" with text "Here is my new text note" notebook "haystack"

---------------------------------------------------------------------------------------
-- version control
-- May 22, 2014 - updated to allow for default year and title offsets
---------------------------------------------------------------------------------------

---------------------------------------------------------------------------------------
-- configure settings before each run
---------------------------------------------------------------------------------------
set notebook_name to "1982.Scrapbook" as string

set default_year to "xxxx" as string

set title_offset to 0 as integer

log "String offset = " & title_offset


---------------------------------------------------------------------------------------
-- validate settings
---------------------------------------------------------------------------------------
exists "notebook:" & notebook_name

if (notebook named notebook_name exists) then
  set noteyears to {"1980", "1981", "1982", "1983", "1984", "1985", "1986", "1987", "1988", "1989", "1990", "1991", "1992", "1993", "1994", "1995", "1996", "1997", "1998", "1999", "2000", "2001", "2002", "2003", "2004", "2005", "2006", "2007", "2008", "2009", "2010", "2011", "2012", "2013", "2014"}
  set notemonths to {"01", "02", "03", "04", "05", "06", "07", "08", "09", "10", "11", "12"}
  set notedays to {"01", "02", "03", "04", "05", "06", "07", "08", "09", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20", "21", "22", "23", "24", "25", "26", "27", "28", "29", "30", "31"}
  set matches to find notes "notebook:" & notebook_name
  #set name of aFile to ((characters 4 thru -1 of filename) as string)

-- ---------------------------------------------------------------------------------------
-- for each note in the folder, look for a date in the title YYYY*MM*DD
-- ---------------------------------------------------------------------------------------

set file_count to 0 as integer

repeat with match in matches
set file_count to file_count + 1
set notetitle to title of match
try
  set noteyear to ((characters (title_offset + 1) thru (title_offset + 4) of notetitle) as string)
end try
try
  set notemonth to ((characters (title_offset + 6) thru (title_offset + 7) of notetitle) as string)
end try
try
  set noteday to ((characters (title_offset + 9) thru (title_offset + 10) of notetitle) as string)
end try

-- ---------------------------------------------------------------------------------------
-- if a default year is set then use it only
-- ---------------------------------------------------------------------------------------
log "******* File " & file_count & ": " & notetitle
log noteyear
log notemonth
log noteday

-- ---------------------------------------------------------------------------------------
-- if a date is found in the note title use whatever potion (Y|M|D) is available 
-- ---------------------------------------------------------------------------------------

if (noteyears contains noteyear) then
  set creationDate to current date
  set year of creationDate to noteyear as integer

if (notemonths contains notemonth) then
  set month of creationDate to notemonth as integer
else
  set month of creationDate to "01"
end if

if (notedays contains noteday) then
  set day of creationDate to noteday as integer
else
  set day of creationDate to "01"
end if

set time of creationDate to 0

set creation date of match to creationDate

log ">>>if loop (date found) " & creationDate

else if (noteyears contains default_year) then
set creationDate to current date
set year of creationDate to default_year as integer
set month of creationDate to "01"
set day of creationDate to "01"
set time of creationDate to 0
set creation date of match to creationDate

log ">>>else loop (default year) " & creationDate
else
log ">>>no action taken "

end if

end repeat
end if
end tell
