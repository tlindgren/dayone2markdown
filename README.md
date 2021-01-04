# dayone2markdown
Converting DayOne journals into markdown files

Forked from: [ploum/dayone2markdown: Converting DayOne journals into markdown files](https://github.com/ploum/dayone2markdown)

## usage

1. Export you DayOne journal as JSON and unzip the folder.
2. Put the script in the unzipped folder.
3. Run the script `./do2md.py Journal.json`

## Results:

1. Each entry is now converted to an MD file. Name of the file is the date-time of the entry.
2. A YAML header is created with title (set to date), date, time, location
3. Pictures are inserted with a relative path ( photos/)
4. Tags are inserted in the text as " #tag" (if they were not previously)

## Limitations

1. If there are two entries at the same second, one will be lost.
2. Metadata other than tags, time and location are lost.

## Set creation date based on filename

Since the files creation date will be set to the time of conversion, it would be preferable to set the file dates to match the original journal entry.

Place the files in a folder with just the MD file and navigate to it in your terminal. 

Then, run this initially to test: 

,,,
for f in *; do t=$(echo $f | sed -E 's/[-. md]//g'); echo touch -t $t "$f"; done
,,,

Then run this to actually change all the files at once:
,,,
for f in *; do t=$(echo $f | sed -E 's/[-. md]//g'); touch -t $t "$f"; done
,,,

Source: [macos - Batch command to change each file's creation date to match the information in the file name - Ask Different](https://apple.stackexchange.com/questions/245373/batch-command-to-change-each-files-creation-date-to-match-the-information-in-th)