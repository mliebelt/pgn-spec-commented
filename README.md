# In a nutshell

Collects information about pgn (portable game notation), and explains typical usage of it.

PGN is a pretty old specification, and never changed afterwards. There are some discussions going on, so this repository shall collect information about it, and provide a better way to access it.

It will not implement the specification, there are already many implementations available. 

## Ideas

I got the idea to start with this when reading about [fsmoscas PGN-Standard](https://github.com/fsmosca/PGN-Standard) repository. The goal here is slighly different, he tries to change the standard.

So what should be done here:

* Have a one [stop collection of information](resources.md) available about PGN.
* Provide a [better readable version](pgn-specification.md)  (similar to the one provided by [Saremba in his colophon](http://www.saremba.de/chessgml/standards/pgn/pgn-complete.htm#AEN10)) that may then be commented by just using Git and markdown, without any complex tooling around it. The [original version](pgn-specification.txt) is provided as well unchanged.
* Have additional documents linked to it, as well as commented sections, that may lead to the wish to expand or change the specification.
  * [PGN Specification Supplement](pgn-spec-supplement.md) Addition to PGN done ~8 years later, that adds structured comments for graphical symbols, timing, ...

