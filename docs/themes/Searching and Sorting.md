tags: #DF #search-and-sort
 
# Searching and Sorting

links: [[705 DF TOC - Encryption & Timelines & Find|DF TOC -Encryption & Timelines & Find]] - [[themes/000 Index|Index]]

---

## Search Basics

When conducting a search in digital forensics, the objective can vary significantly:

- **Searching for Known Items:** Such as specific file names or content you are aware of.
- **Searching for Unknown Items:** Attempting to discover evidence or anomalies without specific details.

### Challenges

Forensic searches can be complex due to several challenges:

- **Too Many Hits:** Filtering through numerous search results.
- **Protected Content:** Dealing with encrypted or hidden data.
- **Compound Files:** Handling multiple layers of file types (e.g., ZIP, TAR, attachments).
- **Hidden Content**: [[Encryption#Steganography|Steganography]]
- **Proprietary Formats:** Difficulty in accessing content due to unique file formats.
- **Large File Lists:** Managing extensive lists from tools like `fls`, which list deleted files, multiple partitions, and drives.

## GNU Grep

`grep` is a powerful command-line tool for searching plain-text data sets for lines that match a regular expression.

Basic examples:

- Search for a pattern in a file: `grep evil files.txt`
- Search in log files: `journalctl | grep failed`

Using regular expressions with `egrep`:

- Match JPEG files: `egrep [jm]peg files.txt`
- Match multiple extensions: `egrep .+\.[mM][pP][34] files.txt`

Other useful options:

- Use a pattern file: `grep -f patterns.txt files.txt`
- Exclude a pattern: `grep -v tmp files.txt`
- Ignore case: `grep -i mp3 files.txt`
- Recursive search in directories: `grep -r pattern /some/path`
- Search binary files: `grep -a pattern file.dll`

## GNU Find

`find` is used to search for files in a directory hierarchy based on various criteria.

Examples:

- Find files by name: `find / -name "*.mp3"`
- Find files by size: `find / -size +50M`
- Find files by owner or group: `find / -user freddy` or `find / -group bfh`
- Execute a command on matched files: `find / -exec stat {} \;`

Custom formatting and sorting:

- Sort by last accessed: `find /home -printf '%As %Ac %p\n' | sort -n`
- Sort by inode change: `find /home -printf '%Cs %Cc %p\n' | sort -n`
- Sort by timestamp: `find / -printf '%As A %Ac %p\n%Ts C %Tc %p\n%Cs M %Cc %p\n' | sort -n`
- Sort all files by size: `find / -printf '%s %p\n' | sort -n`

## Searching for Strings

The `strings` command is useful for extracting printable strings from binary files, often used in digital forensics to identify readable text within disk images.

Examples:

- Extract strings with offsets: `strings -td image.dd`
- Extract strings with locale: `strings -td -e l image.dd`
- Extract and filter strings: `strings -td partition.dd | grep keyword`

The Sleuthkit provides an enhanced version called `srch_strings`.

## Hash Databases and Hashsets

> Exam question: Why are hashsets important for forensics

Hash databases are vital in digital forensics for identifying known files by their hash values. The [National Software Reference Library (NSRL)](https://www.nsrl.nist.gov) provides a comprehensive set of known file hashes.

Creating and using hashsets:

- Generate a hashset: `md5deep -r * > hash.txt`
- Create an index: `hfind -i md5sum hash.txt`
- Lookup a hash: `hfind hash.txt 64d088ee1ffd86ef591de77f8bb34d8b`

Law enforcement agencies often use specialized hash databases to detect illegal material.

## Sleuthkit Sorter

The Sleuthkit sorter tool organizes files from disk images based on various criteria:

- Generate a report of identified files: `sorter -d . partition.dd`
- Sorted extraction of files: `sorter -s -d . partition.dd`
- Include specific hash database: `sorter -a contraband.db -d . partition.dd`
- Exclude NSRL database: `sorter -n nsrl_db -d . partition.dd`

This tool leverages multiple Sleuthkit utilities and is highly configurable.

## Commercial Support

Commercial forensic tools provide enhanced capabilities, including:

- User-friendly GUIs for searching, sorting, and filtering.
- Initial indexing of disk images for faster searches.
- Better support for proprietary formats and international languages.
- Commercial hashsets for identifying known files: [Hashsets](https://www.hashsets.com/)
- Advanced features like fuzzy searching, artificial intelligence, OCR scanning, and audio/video transcription.

---
links: [[705 DF TOC - Encryption & Timelines & Find|DF TOC -Encryption & Timelines & Find]] - [[themes/000 Index|Index]]