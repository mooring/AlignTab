Align Tabular
==============
An alignment plugin for Sublime Text 2/3 -- ST version of the excellent VIM plugin, tabular.

How does it differ from other alignment plugins?
------------
- Flexibility: Align with user defined regular expression
- Efficiency: Smart line detection for alignment if no lines are selected
- Multiple cursors support
- Table mode: super efficient for editing tables

Usage
------------
###First time user

- Predefined alignment tools can be found under the mouse menu `Align By`

<img src="https://github.com/randy3k/AlignTab/raw/fig/alignby.png">

###Advanced user

- Two ways to toogle Align Tabular:
 * 1. keyboard: type `Align Tabular` in command palette (`C+shift+p`).
 * 2. mouse: right click -> `Align Tabular`
- Enter delimiter in Python regex in the input panel
- The input should be in the from of `regex/option`
- For regex, do not use capturing parenthese. Instead, use non-capturing parenthese `(?:regex)`.
- The option, e.g., `c2r2f1`, controls
 - left/right/center justification: `r` or `l` or `c`
 - spaces after the columns: the number after `r` or `l` or `c`
 - max number of delimiters: the number after `f`
- The option for alignment cycles through the columns and delimiters are also columns.
  - the symbol `*` repeats the preceeding justification flags, for example `r*3` equals `rrr`, and `(cr2)*2` equals `cr2cr2`.
- Default option is `l1f0`.
 * All columns are left-justified.
 * A space is added after each column.
 * All matched delimiters are aligned.

<img src="https://github.com/randy3k/AlignTab/raw/fig/aligntab.gif">

###Table Mode

Installation
------------
[Package Control](http://wbond.net/sublime_packages/package_control)


[Examples](https://github.com/randy3k/AlignTab/wiki/Examples)
-----------

Keybinds
------------
For frequent patterns, consider the following keybind in your user keybinds file. (Remember to change the key and regex.)

```
 //align =
  {
    "keys": ["super+shift+a"], "command": "align_tab",
    "args" : {"user_input" : "=/f"}
  }
```
or syntex specific keybind.
```
  // latex align keybind, to align & and \\, but not \&
    {   
    	"keys": ["super+shift+a"], "command": "align_tab", 
        "args" : {"user_input" : "(?<!\\\\)&|\\\\\\\\"}, 
        "context":[
            { "key": "selector", "operator": "equal", "operand": "text.tex.latex" }
        ]
    }
```



Predefined patterns
------------
To make it easier to remember complex patterns, you can save them in
a dictionary in the settings file. Use the name as key and the regex as value.
These patterns are included in the default file:

```
  "named_patterns": {
     "first_equal": "=/f",
     "first_comma": ",/f",
     "first_colon": ":/f"
  }
```

You then just use the name instead of the pattern in the input field.
To edit the patterns, go to `Perferences -> Package Settings -> Aligh Tabular -> Settings`.
