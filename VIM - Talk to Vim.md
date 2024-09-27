#### Verbs
```
Verbs are the actions we take, and they can be performed on nouns. 
d: delete
c: change
y: yank (copy)
v: visually select (V for line vs. character) 
```

---
#### Modifiers
Modifiers are used before nouns to describe the way in which you’re going to do something.
```
i: inside
a: around
t: to; searches for something and stops before it
f: for; searches for that thing and lands on it
/: find a string (literal or regex) 
NUM: number (e.g.: 1, 2, 10)
```

---
#### Nouns
In English, nouns are objects you do something to. They are objects. With Vim it’s the same. 
```
w: word
s: sentence
): sentence (another way of doing it)
p: paragraph
}: paragraph (another way of doing it)
t: tag (think HTML/XML)
b: block (think programming) 
```

---
#### Building sentences (commands) using this language
```
d2w: Delete two words
cis: Change inside sentence  (delete the current one and enter insert mode) 
yip: Yank inside paragraph (copy the paragraph you’re in) 
ct<: Change to open bracket (change the text from where you are to the next open bracket)
f<: Jump forward and land on the < character
t<: Jump forward and land right before the < character
ct,: change to ,
```

---
#### Working With Your File
Some quick basics on working with your file.
```
vi file: open your file in vim
:w: write your changes to the file
:q!: get out of vim (quit), but without saving your changes (!)
:wq: write your changes and exit vim
:saveas ~/some/path/: save your file to that locationvim 
ZZ: a faster way to do :wq. no : required
```

---
#### Searching Your Text
```
/{string}: search for string
/: search forward
?: search backward
n: jump to next occurrence in search direction
N: jump to previous occurrence in search direction
\*: search for other instances of the word under your cursor 
f:  jump onto a character
t: jump up to a character
;: go to the next instance when you’ve jumped to a character
,: go to the previous instance when you’ve jumped to a character 
```

---
### Moving around in your text
#### Basic motions
```
j: move down one line
k: move up one line
h: move left one character
l: move right one character 
w: move forward one word
b: move back one word
e: move to the end of your word 
W: move forward one big word
B: move back one big word 
```

#### Moving within the line
```
0: move to the beginning of the line
$: move to the end of the line
^: move to the first non-blank character in the line
t": jump to right before the next quotes
f": jump and land on the next quotes 
;: go to the next instance when you’ve jumped to a character
,: go to the previous instance when you’ve jumped to a character 
```

#### Moving by sentence or paragraph
```
): move forward one sentence
}: move forward one paragraph 
```

#### Moving within the screen
```
H: move to the top of the screen
M: move to the middle of the screen
L: move to the bottom of the screen
gg: go to the top of the file
G: go to the bottom of the file
^U: move up half a screen
^D: move down half a screen
^F: page down
^B: page up 
```

#### Jumping back and forth
```
Ctrl-i: jump to your previous navigation location
Ctrl-o: jump back to where you were 
```

#### Other motions
```
:$line_numberH: move to a given line number
^E: scroll up one line
^Y: scroll down one line
^U: move up half a page
^D: move down half a page
^F: move down a page
^B: move up a page 
```

---
### Basic change/insert options
```
i: insert before the cursor
a: append after the cursor
I: insert at the beginning of the line
A: append at the end of the line
o: open a new line below the current one
O: open a new line above the current one
r: replace the one character under your cursor
R: replace the character under your cursor, but just keep typing afterwards
cm: change whatever you define as a movement, e.g. a word, or a sentence, or a paragraph.
C: change the current line from where you’re at
ct?: change up to the question mark
s: substitute from where you are to the next command (noun)
S: substitute the entire current line 
```

---
#### Changing Case
```
~:  Change case on character or selected text 
```

---
#### Format the current paragraph
```
gq ap:  format around paragraph
```

---
#### Deleting text
```
x: exterminate (delete) the character under the cursor
X: exterminate (delete) the character before the cursor
dm: delete whatever you define as a movement, e.g. a word, or a sentence, or a paragraph.
dd: delete the current line
dt.: delete delete from where you are to the period
D: delete to the end of the line
J: join the current line with the next one (delete what’s between) 
```

---
#### Undo and Redo
```
u: undo your last action.
Ctrl-r: redo the last action 
```

---
#### Repeating Actions

```
 .: to repeat your last action
 
dw : delete a word 
5 .  : delete five more words
```

---
#### Copy and Paste
```
y: yank (copy) whatever’s selected
yy: yank the current line 
p: paste the copied (or deleted) text after the current cursor position
P: paste the copied (or deleted) text before the current cursor position 
```

---
#### Text Objects
```
i: inside
a: around

words: iw and aw
sentences: is and as
paragraphs: ip and ap
single quotes: i' and a'
double quotes: i" and a"
back ticks: i` and a`
parenthesis: i( and a(
brackets: i\[ and a\[
braces: i{ and a{
tags: it and at 
```

---
#### Visual Mode
```
v : character-based
V : line-base
Ctrl +v : paragraphs or column wise
vi( : Select inside of parenthesis
vi\[ : Select inside of brackets
v2i{ : Select everything inside the second tier braces
```
