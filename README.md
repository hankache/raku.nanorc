# raku.nanorc
Raku Syntax Highlighting for Nano

## How To
1. Place ```raku.nanorc``` somewhere (usually under ```~/.nano```)
2. Add the following line ```include "~/.nano/raku.nanorc"``` to your ```~/.nanorc``` file

The colours come from your terminal's palette, so they follow its theme, light or dark.

## Screenshots
![Screenshot 1](screenshots/screenshot1.png)

![Screenshot 2](screenshots/screenshot2.png)

![Screenshot 3](screenshots/screenshot3.png)

## Known limits
Nano highlights with regular expressions only, so a few things cannot be done properly:

- A `#` after a space, `;`, `)` or `}` inside a string starts a comment. In a comment that directly follows `;`, `)` or `}`, that character gets the colour of the comment.
- An apostrophe inside an identifier (`doesn't-work`) starts a string.
- Nested brackets in embedded comments end at the first closing bracket.
- A `/regex/` without a prefix is only recognised after `~~`, an opening bracket, a comma, `= `, `: `, some keywords, or at the start of a line. Brackets and commas inside such a regex are left unpainted.
- Heredocs are recognised when the terminator is in capitals. With `END`, `EOF`, `EOT`, `EOS`, `CODE`, `SOURCE`, `TEXT` and `HERE` they end at that terminator; with any other one they end at the first line that is a single word in capitals.
- Code after a heredoc opener on the same line is left unpainted.
- Heredocs, Pod and embedded comments also start inside strings and comments, as multi-line rules cannot see what was painted before them.
- `< a b c >` with spaces inside the brackets is not painted, as it cannot be told apart from two comparisons.
- The subscript of a variable named `q`, `m` or `s` (`$m[0]`) is left unpainted, so that it is not taken for a quote or a regex.
- `s[...]` and `s{...}` without an adverb only count as a substitution when followed by ` = `.
- Quotes and regexes in brackets end at the first closing bracket, unless the brackets are doubled (`q{{ ... }}`).
- A variable inside `q{...}` or `Q[...]` is still painted when the quote directly follows a bracket, as in `(q{$x})`.
- Pod formatting codes (`B<...>`, `C<...>`) are only painted after a space or at the start of a line, and also where they appear in code or in a string.
- Meta-operators made with `R`, `X`, `Z` and `S` (`Z~`, `X+`, `Zmax`) need a space on both sides.

## License
GPL 3 or later
