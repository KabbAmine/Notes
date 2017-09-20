> 16 sept. 2017 23:28:40

# Vim

## Motions

- `[[,]]`: Move between function definitions
- `(,)`: Move between sentences
- `[z,]z`: Move to start/end of fold when inside of the fold.
- `zj,zk`: Move to start/end of fold when outside
- `gd`: Go to 1st occurence.
- `g;`: Go back to last edited place.
- `g'X`: Go to mark `X`.

## Operators

- `g~{motion}`: Switch case
- `qg`: Format.

## Registers

- `0` Last yank
- `1` Last deletion
- `2` 2nd last deletion ... and so on
- `:` Last command
- `.` Last inserted text
- `%` Current file name
- `/` Last search pattern

`let @r = '...'` to set a register (e.g `r`)

## Ranges

- `:/^foo/,$delete` From the next line that starts with "foo" to the end.
- `:/^foo/+1,$delete` From the line after the line that starts with "foo" to the end.

- The `/` address can be preceded with another address.
```viml
:/foo//bar//quux/d
```
The above would delete the first line containing "quux" after the first line containing "bar" after the first line containing "foo" after the current line.

## Functions

- Use the new `execute()` instead of `redir => var | ....`.

- How to implement a good command completion function:
```viml
function! Foo(ArgLead, CmdLine, CursorPos)
  return filter(copy(v:oldfiles), 'v:val =~ a:ArgLead')
endfunction
```

## Misc

- `g<C-a/x>`: In visual mode, increment/decrement by additional count.
- `Ctrl-m/j` insert a new line in insert mode
- `[I`: Display all lines that contain the keyword under the cursor.
- `]I`: Like the one above but start at the current cursor position.
- `[i`: Display 1st line where the current word occurs
- `]i`: Like the one above but start at the current cursor position.
- `zM`: Close all folds.
- Macros using `normal`
```vim
normal @r
" Or
:normal @r
```
- Inverse of `:g` is `:g!` or `:v`.
- `!!` execute `.!`.
- We can use `*` in vimhelp (`:h buf*()<C-d>`).

### Autocmd

- `doautocmd XXX` Trigger event XXX

- `doautocmd User XXX` Create your own user event XXX
```viml
function! Foo()
  ...
  doautocmd User FooExit
endfunction

" Now we can execute something after Foo()
autocmd User FooExit call something()

" A better way is to always check if the user autocmd do not exist already.
if exists('#User#FooExit')
  doautocmd User FooExit
endif
```

- By default, autocmds do not nest! If an autocmd executes a command, which in turn would usually trigger another event, it won't happen.
To make it work you should use `nested`:
```viml
" e.g
autocmd VimEnter * nested Do Something
```

### Text-objects

| type      | keys         |
| --------- | ------------ |
| fold      | `iz`, `az`   |

## Tips

### Recursive macro

Using `q` register, the trick is to add `@q` in the end of our macro to make it recursive.

## Plugins

