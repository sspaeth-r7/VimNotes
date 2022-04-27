# VimNotes
## Deletion
- Delete quoted string (incl. quotes): `da"`
  - Select "a"n object including white space
- Delete contents of quoted string: `di"`
  - Select an "i"nner object without white space
- Delete entire code block: `d%`
  - With cursor at beginning of first line

## Navigation
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
