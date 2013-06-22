# greedy-git

A tool for analysing remote git files which have been accidentally shared on a web project

## Usage

greedy-git -[aiIr] [-g <file>]  <url>

By default, greedy-git checks a URL for the presence of <url>/.git/config, downloads it to ./<url domain>/config and makes a basic check to see if it looks like a git config file. If this file is present, it can then go on to do a number of other checks:

optional arguments:
  -i --index    Fetch and parse the index file at <url>/.git/index, creating also index.txt (human readable version), index.json (json encoded version), index.lst (flat file list) and index.rpt (analysis report on files found in index)
  -g <path>     Download the file relating to the path relative to the repository root, unzip it and save it in ./<url domain>/files/<path>
  -r --report   Show an overview of files in the repository (report.md)
  -I --get-interesting  Automatically get "interesting" files. These are:
      * Things that look like backup archives
      * Things that look like configuration files or that might contain credentials
      * Anything that looks like dynamic scripting source code
      * *.sql, *.inc, *.config, *.ini
      * hidden files, i.e. starting with "."
  -a            Get all files referenced in index

