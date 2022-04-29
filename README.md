# VimNotes
## Visual Mode
- Reselect last visual block mode selection: `gv`
- Select entire current line: `V`
  - Can be used in both visual and command modes
  - When used in visual mode, all lines with at least 1 selected character will be selected in full
  - When used in command mode, whatever line the cursor is on will be used for selection

## Deletion
- Delete quoted string (incl. quotes): `da"`
  - Select "a"n object including white space
- Delete contents of quoted string: `di"`
  - Select an "i"nner object without white space
- Delete entire code block: `d%`
  - With cursor at beginning of first line
- Delete from current line to EOF: `dG`
- Delete from current line to BOF: `dgg`

## Navigation
- Move cursor to previous location: `^o`

### Markers
- Set a marker: `mx`
  - Where `x` is a character to name marker
- Navigate to exact location of marker: \`x (I couldn't escape this at the beginning of a codeblock)
- Navigate to beginning of line of marker: `'x`
- An uppercase and lowercase marker are distinct

### Code
- Jump to matching bracket: `%`

## Ranges
- In place of using a `%` in a substitution command (such as `:%s/foo/bar`), you can use ranges
  - Apply from first to current line: `:1,.s/foo/bar`
  - Apply from current to last line: `:.,$s/foo/bar`
  - Apply from current to marker line: `:.,'xs/foo/bar`

## Numbers
- Increment selected number: `^a`
- Decrement selected number: `^x`

## Substitution
- When doing a find and replace, add a `c` to confirm each substitution
  - For example, `:%s/foo/bar/gc`

## Miscellaneous
- Pretty prent a JSON file open in the editor: `:%!python -m json.tool`
- Delete a word and enter insert mode "'c'hange 'w'ord": `cw`
  - Deletes everything right of cursor, so if you want to replace an entire word, run at beginning of it
