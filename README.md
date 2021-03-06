# VimNotes
## Visual Mode
- Reselect last visual block mode selection: `gv`
- Select entire current line: `V`
  - Can be used in both visual and command modes
  - When used in visual mode, all lines with at least 1 selected character will be selected in full
  - When used in command mode, whatever line the cursor is on will be used for selection
- Select quoted string (incl. quotes): `va"`
  - Select 'a'll/'a'n of object including white space
- Select contents of quoted string: `vi"`
  - Select an 'i'nner object without white space

## Deletion
- Delete quoted string (incl. quotes): `da"`
  - Delete 'a'll/'a'n of object including white space
- Delete contents of quoted string: `di"`
  - Delete an 'i'nner object without white space
- Delete entire code block: `d%`
  - With cursor at beginning of first line
- Delete from current line to EOF: `dG`
- Delete from current line to BOF: `dgg`
- Delete all blank lines in file: `:%!grep .`
  - Works because `.` is regex for any one character
  - Won't necessarily work on Windows (but who cares)
  - There are other ways to do this in vim, but this is memorable and versatile
- Delete blank lines in range: `:1,5!grep .`
- Delete blank lines in marker range: `:'x,.!grep .`
- Replace multiple blank lines with one: `:%!cat -s`
  - From the `cat` manpage: `-s : Squeeze multiple adjacent empty lines, causing the output to be single spaced.`

## Navigation
- Move cursor to previous location: `^o`
- Jump to previous empty line: `{`
- Jump to next empty line: `}`
- Jump to start of text on line (based off indentation) and insert: `I`
- Jump to auto indent and enter insert mode: `S`
  - Rather than inserting at the beginning of the line, this will insert where the line *should* begin
- Find case-insensitively: `/word\c`
- Make new line after current and enter insert mode: `o`
- Make new line before current and enter insert mode: `O`
- Jump to right after end of word and enter insert mode (like `A` does for lines): `ea`
- Scroll to move current line to center of screen: `zz`
  - Scroll current line to top: `zt`
  - Scroll current line to bottom: `zb`

### Jump to character
Where `x` is the character you'd like to jump to:
- Jump to next occurrence of character on current line: `fx`
- Jump to previous occurrence of character on current line: `Fx`
- Next occurrence: `;`
- Previous occurrence: `,`

### Markers
- Set a marker: `mx`
  - Where `x` is a character to name marker
- Navigate to exact location of marker: \`x (I couldn't escape this at the beginning of a codeblock)
- Navigate to beginning of line of marker: `'x`
- An uppercase and lowercase marker are distinct

### Code
- Jump to matching bracket: `%`

## Numbers
- Increment selected number: `^a`
- Decrement selected number: `^x`

## Substitution
- When doing a find and replace, add a `c` to confirm each substitution
  - For example, `:%s/foo/bar/gc`

### Ranges
- In place of using a `%` in a substitution command (which selects entire file - ex: `:%s/foo/bar`), you can use ranges
  - Apply from first to current line: `:1,.s/foo/bar`
  - Apply from current to last line: `:.,$s/foo/bar`
  - Apply from current to marker line: `:.,'xs/foo/bar`

### Capitalization
Adapt the following examples as needed:
- `~`    : Changes the case of current character
- `g~~`  : Invert case to entire line
- `g~w`  : Invert case from cursor to end of word
- `g~iw` : Invert case of entire current word
- `g~G`  : Invert case for rest of file
- `guG`  : Change to lowercase for rest of file
- `gU)`  : Change until end of sentence to upper case
- `gu}`  : Change to end of paragraph to lower case

## Windowing
Vim can be used as a terminal emulator multiplexer. Primarily, this is for viewing multiple files at once,
but could also be used for having both terminal(s) and file(s) open in one vim process.
- Open a new vim window below (split screen "hot dog"): `^ws`
- Open a new vim window beside (split screen "hamburger"): `^wv`
- Open a new terminal above (split screen "hot dog"): `:term`
- Open a new terminal beside (split screen "hamburger") `:vert term`
- Swap ('e'xchange) current window with next: `^wx`

## Folding
Folds in vim are ways to hide blocks of text/code when you don't need to see them.
In other words, this feature allows you to "collapse" a function.
- Create and collapse a 'f'old: `zf`
  - This expects that you've selected the text you'd like to fold in visual block mode

By placing your cursor on any part of an existing fold, you can:
- Collapse or 'c'lose the fold: `zc`
- Expand or 'o'pen the fold: `zo`

## Miscellaneous
- Pretty prent a JSON file open in the editor: `:%!python -m json.tool`
- Delete a word and enter insert mode "'c'hange 'w'ord": `cw`
  - Deletes everything right of cursor, so if you want to replace an entire word, run at beginning of it
  - Same idea applies to anything else, for instance: `ci{` or `ca(`
- Swap current and line below: `ddp`
