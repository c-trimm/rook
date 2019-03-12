# Rook
### A simple php-based journal manager
Rook is a command-line based journal manager. You can create journal entries by using the inline entry method `-m`, or by editing the rook script and specifying an editor. By default, rook uses nano. 

## Installation
Rook requires PHP 7.0+ to be installed.

Clone the repo
```bash
git clone git@github.com:c-trimm/rook.git
```
Add rook to your path. Assuming you cloned rook in your home directory, put this in your .profile to use anywhere.
```bash
export PATH=~/rook:$PATH
```

## Usage
Simply call the `rook` command and a new markdown journal entry will be created with todays date in the format `YYYY-MM-DD.md`. Once an entry is created for the day, calling `rook` again will open the file and place the cursor at the end.

## Appending
You may use the `-m` option to specify an inline message and append it to today's journal entry.
```bash
rook -m 'My journal messages are the best!'
```

## Journals
Journal entries are saved to an `entries` folder inside the rook directory. You can create sub-journals by specifying the `-j` option with the name of your journal. For instance, you may have one journal for personal entires and another for work entries.
```bash
rook -j work
```

## Git Repo
If there is a git repository in `entries` or in a journal directory (i.e. `entries/work`), rook will attempt to stash, pull, commit, then push after every change.

## Deleting Entries
Delete today's entry with `-d`. To skip the prompt, use `-df`.
```bash
rook -d #or
rook -df
```

## Templates
You can create a .template file to use the same template every day. Rook will replace some template tags for you:
- **{date}**: Pretty print of today's date.
- **{start}**: If using nano, Rook will remove this and place cursor here.
- **{tags}**: If the `-t` option is used, Rook will replace this with option value. Ex: `rook -t 'mytag, foo'` 