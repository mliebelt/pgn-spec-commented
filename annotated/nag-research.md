# Research about NAGs

## PGN Specification

Why is research here necessary? The [section 8.2.4](/pgn-specification.md#824-movetext-nag-numeric-annotation-glyph)
is very short, and just tells us that only 255 NAGs are possible `$0` is not allowed.

> An NAG (Numeric Annotation Glyph) is a movetext element that is used to indicate a simple annotation in a language independent manner.
> An NAG is formed from a dollar sign ("$") with a non-negative decimal integer suffix.
> The non-negative integer must be from zero to 255 in value.

The [section 10](/pgn-specification.md#10-numeric-annotation-glyphs) is more informative, but interestingly, the real
symbols used are not (all) included there. A typical part looks like

> | NAG  | Interpretation |
> |-----:| ---------------------|
> | 0    |  null annotation
> | 1    |  good move (traditional "!")
> | 2    |  poor move (traditional "?")
> | 40   |  White has the attack
> | 41   |  Black has the attack
> | 42   |  White has insufficient compensation for material deficit
> | 43   |  Black has insufficient compensation for material deficit

So the graphical symbols used (here for `$1` == `"!"`) are only shown in the interpretation.

> NAG zero is used for a null annotation; it is provided for the convenience of software designers as a placeholder value and should probably not be used in external PGN data.
> 
> NAGs with values from 1 to 9 annotate the move just played.
> 
> NAGs with values from 10 to 135 modify the current position.
> 
> NAGs with values from 136 to 139 describe time pressure.
> 
> Other NAG values are reserved for future definition.

## Wikipedia Article

The [wikipedia article](https://en.wikipedia.org/wiki/Numeric_Annotation_Glyphs) is here much more informative. The following are relevant parts:

* The [Standard NAGs section](https://en.wikipedia.org/wiki/Numeric_Annotation_Glyphs#Standard_NAGs) includes besides the number and meaning symbol, Unicode, HTML entities, and the name.
* The [Non Standard NAGs section](https://en.wikipedia.org/wiki/Numeric_Annotation_Glyphs#Standard_NAGs) includes a column that references the tools that uses that annotation.