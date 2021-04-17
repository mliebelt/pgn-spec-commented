# Exporting PGN

Goal: Provide the information of the [spec](../pgn-specification.md) in a way that a reader understands what is said about exporting of PGN.

## Link Collection

* [2.2 Specification Goals](../pgn-specification.md#22-specification-goals) Motivation: Explains why it is essential to have a format that can be read and computed by everyone (no vendor lock-in). No information to export format.
* [3 Import and Export](../pgn-specification.md#3-formats-import-and-export):  Explains the difference of import and export, without any concrete rule of hint.
* [3.2.4 Reduced Export Format](../pgn-specification.md#324-reduced-export-format): Explains how to provide a minimal export format in leaving out many things.
* [4.1 Character codes](../pgn-specification.md#41-character-codes) Reduce the character codes to ISO 8859/1 (Latin 1), better to ASCII 7 bit only.
* [4.2 Tab characters](../pgn-specification.md#42-tab-characters) Don't use tab characters at all.
* [4.3 Line lengths](../pgn-specification.md#43-line-lengths) Line length should be held to 80 characters.
* [5 Commentary](../pgn-specification.md#5-commentary) Mostly about import format.
* [8.1 Tag pair section](../pgn-specification.md#81-tag-pair-section) Tags should be left justified.
* [8.1.1 Seven Tag Roster](../pgn-specification.md#811-seven-tag-roster) Special considerations for the Seven Tag Roster.
* [8.2 Movetext section](../pgn-specification.md#82-movetext-section) Rules for the export of moves text.
* [8.2.3.7 Import and export SAN](../pgn-specification.md#8237-import-and-export-san) Rules to export SAN
* [8.2.3.8 SAN move suffix annotations](../pgn-specification.md#8238-san-move-suffix-annotations) Rules for NAGs
* [8.2.5 Movetext RAV (Recursive Annotation Variation)](../pgn-specification.md#825-movetext-rav-recursive-annotation-variation) No additional information
* [12 PGN collating sequence](../pgn-specification.md#12-pgn-collating-sequence) mostly relevant for export.
* [17 Alternative chesspiece identifier letters](../pgn-specification.md#17-alternative-chesspiece-identifier-letters) why not to use in export format.

## Extraction from the spec

1. Use LF for line breaks in the export format: See [section 3.2.2](../pgn-specification.md#322-archival-storage-and-the-newline-character), there
  > The **archival representation of a newline** is the ASCII control **character LF** (line feed, decimal value 10, hexadecimal value 0x0a).
2. Use ISO 8859/1 (Latin 1), better to ASCII 7 bit only. See [section 4.1](../pgn-specification.md#41-character-codes), there:
  > PGN data is represented using a **subset of the eight bit ISO 8859/1 (Latin 1)** character set.
  > 
  > ... The 32 ISO 8859/1 code values from 128 to 159 are non-printing control characters. They are not used for PGN data representation. The 32 code values from 160 to 191 are mostly non-alphabetic printing characters and their use for PGN data is discouraged as their graphic representation varies considerably among other ISO Latin sets. Finally, the 64 code values from 192 to 255 are mostly alphabetic printing characters with various diacritical marks; their use is encouraged for those languages that require such characters. The graphic representations of this last set of 64 characters is fairly constant for the ISO Latin family. 
  > 
  > ... **Printing character codes outside of the seven bit ASCII range may only appear in string data and in commentary.** They are not permitted for use in symbol construction. 
  > 
  > ... PGN software authors should have their programs handle such environments by displaying a question mark ("?") for non-ASCII character codes.
3. Don't use TAB characters in export format. See [ section 4.2](../pgn-specification.md#42-tab-characters)
  > **Tab characters**, both horizontal and vertical, **are not permitted** in the export format.
4. Using line lengths under 80 characters, if possible. See [section 4.3](../pgn-specification.md#43-line-lengths)
  > Import format PGN text lines are limited to having a maximum of 255 characters per line including the newline character. **Lines with 80 or more printing characters are strongly discouraged** because of the difficulties experienced by common text editors with long lines.
5. No information in the spec about export comment format. See [section 5](../pgn-specification.md#5-commentary) 
  > **Export format representation of comments needs definition work.**
6. Tags have a standard format. See [section 8.1](../pgn-specification.md#81-tag-pair-section)
  > For PGN export format, there are **no white space characters between the left bracket and the tag name**, there are **no white space characters between the tag value and the right bracket**, and there is a **single space character between the tag name and the tag value**.
  >
  > ... All tag names used for archival storage begin with an upper case letter.
  > 
  > ... Export format requires each tag pair to appear **left justified on a line by itself**; **a single empty line follows the last tag pair**.
7. Export the Seven Tag Roster in a standard format. See [section 8.1.1](../pgn-specification.md#811-seven-tag-roster), there
  > For export format, the STR tag pairs appear before any other tag pairs. (The STR tag pairs must also appear in order; this order is described below). Also for export format, **any additional tag pairs appear in ASCII order by tag name**.
  > 
  > ...  The seven tag names of the STR are (in order): **Event, Site, Date, Round, White, Black, Result**.
  > 
  > ... For PGN export format, a single blank line appears after the last of the tag pairs to conclude the tag pair section. This helps simple scanning programs to quickly determine the end of the tag pair section and the beginning of the movetext section. 
8. Export of moves text. See [section 8.2](../pgn-specification.md#82-movetext-section), there
  > In PGN export format, tokens in the move text are placed **left justified** on successive text lines each of which has **less than 80 printing characters**. As many tokens as possible are placed on a line with the remainder appearing on successive lines. A **single space character appears between any two adjacent symbol tokens on the same line** in the move text. As with the tag pair section, a **single empty line follows the last line of data to conclude the move text section**.
  >
  > Neither the first or the last character on an export format PGN line is a space. (This may change in the case of commentary; this area is currently under development.)
9. Export of move numbers. See [section 8.2.2.2](../pgn-specification.md#8222-export-format-move-number-indications), there
  > There are two export format move number indication formats, one for use appearing **immediately before a white move element** and one for use appearing **immediately before a black move element**. A white move number indication is formed from **the integer** giving the full move number with **a single period character** appended. A black move number indication is formed from the **integer** giving the full move number with **three period characters** appended.
  > 
  > **All white move elements have a preceding move number indication**. A black move element has a preceding move number indication **only in two cases**: first, if there is **intervening annotation or commentary between the black move and the previous white move**; and second, if there is **no previous white move in the special case where a game starts from a position where Black is the active player**.
  > 
  > There are no other cases where move number indications appear in PGN export format. 
10. Export of SAN. So all rules of 8.2.3 are used. See [section 8.2.3.7](../pgn-specification.md#8237-import-and-export-san)
  > PGN export format **always uses the above canonical SAN to represent moves in the move text section** of a PGN game.
11. How to export NAGs. See [section 8.2.3.8](../pgn-specification.md#8238-san-move-suffix-annotations)
  > When exported, a move suffix annotation is **translated into the corresponding Numeric Annotation Glyph** as described in a later section of this document. For example, if the single move symbol "Qxa8?" appears in an import format PGN move text, it would be replaced with the two adjacent symbols "Qxa8 $2".
12. No information about RAV. See [section 8.2.5](../pgn-specification.md#825-movetext-rav-recursive-annotation-variation)
  > *** The specification for import/export representation of RAV elements needs further development.
13. Game termination marker has to be last. See [8.2.6 Game Termination Markers](../pgn-specification.md#826-game-termination-markers), highlight is mine.
  > Each movetext section has **exactly one game termination marker**; the marker **always occurs as the last element in the move text**. The game termination marker is a symbol that is one of the following four values: "1-0" (White wins), "0-1" (Black wins), "1/2-1/2" (drawn game), and "*" (game in progress, result unknown, or game abandoned). Note that the digit zero is used in the above; not the upper case letter "O". The game termination marker **appearing in the move text of a game must match the value of the game's Result tag pair**. (While the marker appears as a string in the Result tag, it appears as a symbol without quotes in the movetext.)
14. How to order games when doing an export. See [section 12](../pgn-specification.md#12-pgn-collating-sequence), there
  > There is a standard sorting order for PGN games within a file. This collation is based on eight keys; these are the seven tag values of the STR and also the move text itself.
  > 
  > ... The **first** (most important, primary key) is the **Date tag**. Earlier dated games appear prior to games played at a later date.
  > 
  > ... The **second** key is the **Event tag**. This is sorted in ascending ASCII order.
  > The **third** key is the **Site tag**. This is sorted in ascending ASCII order. The fourth key is the Round tag.
  > 
  > ... The fifth key is the White tag. This is sorted in ascending ASCII order. The sixth key is the Black tag. This is sorted in ascending ASCII order. The seventh key is the Result tag. This is sorted in ascending ASCII order. The eighth key is the movetext itself. 
15. Why to use English for piece letters? See [section 17](../pgn-specification.md#17-alternative-chesspiece-identifier-letters), there
  > English language piece names are used to define the letter set for identifying chesspieces in PGN movetext. However, authors of programs which are used only for local presentation or scanning of chess move data may find it convenient to use piece letter codes common in their locales. This is not a problem **as long as PGN data that resides in archival storage** or that is exchanged among programs **still uses the SAN (English) piece letter codes**: "PNBRQK".