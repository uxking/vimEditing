# vim Starter Cheatsheet
**Never use the arrow keys!**
#### vim has three modes:
"insert mode" vs "normal mode" vs "visual mode"  

**Cursor Movement**  
Get around your file via the `jkhl` keys  
`j` - move down a line  
`k` - move up a line  
`h` - move left a character  
`l` - move right a character  
`wWbBeE` - move to the next word, backwards, or end of word  
`0` - places you at the begining of a line  
`^` - places you at the begining of the first non-whitespace character  
`$` - places you at the end of the line  
`g_` - places you at the last non-whitespace character  
`1G` OR `gg` - move to top, the first line of the file  
`12G` - is the 12th line of the file  
`G` - last line of the file  

## Normal mode: hit escape  
_use : (colon) for further actions_  

**File commands**  
`:w`  - Saves file  
`:w <filename>` - saves file with `<filename>`  
`:q` - quit file  
`:q!` - quit without saving  
`:wq` - save and quit the file  

**Normal mode editing commands**  
`x` - delete single character | `<num>x` - delete `<num>` characters  
`d` - delete | `dw` - delete word | `diw` - delete in word | `d$` - delete to end of line | `dd` - delete line | `<num>dd` - delete `<num>` lines  
`dd` - delete entire line - everything  
`dG` - delete from current line to the end of the file  
`s` - substitute and places you in insert mode  
`r` - replace - one time function - replaces a single characters with the next characters you type  
`S` - delete entire line and place in insert mode  
`J` - join two lines  
`.` - repeats the last command  
`*` - highlights each occurance of that word  
`~` - switch case of the current character - also works in visual mode - changes case of highlighted text  
`u` - undo  
`:redo` OR `:red` OR `<CTRL>-R` - redo  

### Find and Search  

`f` OR `F` - finds an occurance of a character on the line your cursor is on  
>	Example: `fa` would find the first "a" on the line you are on
>	`3fa`- would find the 3rd occurance of "a" on the line you are on

**Find something and move to it**  
`/pattern` -  search forward  
>	Example: `/something<enter>` moves you to the fisrt occurance of that "something"
>	`n` moves you to the next occurance - `N` moves you to the previous occurance

`?pattern` - search backward  
>	Example: `?something<enter>` moves you backward to the occurance of that "something"
>	`n` moves you back further to the next item - `N` moves you to the next occurance

## Insert mode:  
Various ways to get into insert mode.  
`i` - gets into insert mode at the cursor - start typing  
`a` - gets into insert mode following the cursor  
`c` - change | `cw` - change word | `ciw` - change in word | `ci'`, `ci"`, `ci(`, `ci{` - change in ', " , (), {}  
`o` - new line after cursor  
`O` - new line before cursor  

**Cut and Pasting**  
In _Normal_ mode  
`y` - yank text | `yy` - yank line | `Y` - same as yy | `<num>yy` OR `<num>Y` - yanks `<num>` lines| `yw` - yank word | `yiw` - yank in word | `<num>yw` - yank `<num>` words | `y$` - yank to end of line  
>	In visual mode `Y` is lines and `y` is text or chars (it's wierd, but they are pretty much interchangable)  

`p` - paste after | `P` - paste before  
>	Example: `3Yp` yanks three lines and pastes them after the current line  
>	`xp` - deletes one character and pastes it after the delete. Good for swapping characters  
>	("mkie" would become "mike" if I did `xp` with the cursor at the "k")  

## Using Registers  
Registers are locations where you can store yanked or deleted text. Registers are accessed via `"` (double quote).  
`"<char>y` - adds the yanked text to the register located at `<char>`  
>	Example: `"ay` - loads the yanked text into the a register

`"<char>p` - pastes the text in register `<char>`  
>	Example: `"ap` - pastes the text in register "a"

`:reg` - display the registers and their contents  

**Read output from a file or a command into your file**  
`:read Myfile.txt` - reads the contents of `Myfile.txt` into the current vim session  
`:read !ls` - adds the output of the `ls` command to your current vim session  

### Using Marks  
Marks allow you to "reference" a line/char in your file. Marks are accessed via `'` (single quote).  
`m<char>` - adds a mark named `<char>`  
>	Example: `ma` - marks the line/char under the cursor

`'<char>` - takes you to the "mark" made earlier named `<char>`  
>	Example: `'a` - takes you to the line/char at mark "a"
>	`3Y'ap` - yanks three lines and pastes them at mark "a"

`:marks` - list all current marks  

## Using Macros  
Macros are recordings of key commands that can be replayed  
`q<char>` - starts recording a macro and saves in `<char>` register
>	After the above, start typing the commands you want to save, and when finished type `<esc>q`
>	Example: `qb$x<esc>q` - record a macro at register "b" which moves to the end of the line and deletes the last character
`@<char>` - executes the macro saved at register `<char>`  
>	Example: `@b` - executes macro at register "b"

`@@` - executes the macro again  
`<num>@<char>` - execute the macro `<num>` times  
`:reg` - see what macros are stored  

## Visual Mode  
In _Normal_ mode type `v`  
This allows you to highlight text and issue commands against the highlighted text- like `d`, `c`, `y`, `s`, `x`  

***Cool things you can do in _Normal_ mode***  
`:set number` - adds line numbers to your vim  
`:set relativenumber` - adds relative line numbers to vim  
`:set hlsearch` - highlights searches  
`:set incsearch` - highlights searches as you type them  
`:noh` - clears the highlight until next search  
`:syntax on` - syntax highlighting for certain files  
`:!` run a shell command - does not put the ouput in the vim session  
`:f` - gives you information about the current file you are editing  
