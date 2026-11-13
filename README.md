# typist

Typing practice in the terminal, written in Avin with [`dev.avinlang.tui`](https://github.com/avin-lang/tui).
Type literary passages or word drills and watch your speed and accuracy as you go.

```sh
avin run .
avin build . -o typist
avin test .
```

The manifest fetches `avin-lang/tui` 0.2.5. Run it in a terminal at least 40 columns wide and 15
rows tall.

## Drills

Choose one from the menu with Up/Down and Enter, or press its number:

1. **Short passages**: 24 excerpts, four each from Austen, Carroll, Melville, Conan Doyle, Dickens
   and Stevenson. The author and book are shown on the passage's frame. See
   [sources and text normalization](SOURCES.md).
2. **Longer passages**: 8 longer excerpts from the same books, for sustained practice.
3. **Tricky words**: 24 words drawn at random from 40 that trip the fingers: doubled letters,
   awkward sequences, capitals, contractions and punctuation.
4. **My mistakes**: up to 24 of the words you have mistyped this run, each once and in a random
   order, including mistakes you corrected with Backspace. Words keep their letters and the
   apostrophes inside contractions (`don't`, `I'm`); surrounding punctuation, symbols and digits are
   dropped, and curly apostrophes become straight ones. Case variants count as one word, spelled as
   first seen, and `I` keeps its capital. A mistake on a space saves nothing. The list lasts until
   you quit.

Passage drills are chosen at random and never repeat the passage just typed.

## Typing

The clock starts with your first key. Correct characters turn green; mistakes are shown in white on
red, a mistyped space as `·`. The next character to type is shown reversed. The passage wraps at
words and scrolls to keep your place in view, with a scrollbar on its frame when it does not fit.

Above the passage are your live speed, accuracy and time, and a bar of how far through you are.

- **Backspace** takes back the last character.
- **Ctrl-R** starts the same drill again with a fresh score.
- **Tab** moves on to another drill of the same kind.
- **Esc** returns to the menu; Esc on the menu quits.
- **Ctrl-C** quits from anywhere and puts the terminal back.

A drill is complete once you have typed as many characters as it holds, mistakes included. The
results then open over it: speed, accuracy, time, correct characters and mistakes. **Enter** (or
Tab) starts the next drill, **r** retries this one, **Esc** goes to the menu and **q** quits.

## Scoring

- **Speed** is correct characters in the text at the end, divided by five, per minute.
- **Accuracy** is correct keystrokes over all printable keystrokes: correcting a mistake does not
  erase it.

Paste is ignored.

## Tests

`avin test .` covers scoring, timing and corrections, passage and word selection, word extraction for
the mistakes drill, the menu, drill and results keys, the layout of passages in rows, and every
screen drawn into a grid at sizes from too small to large. `tests/pty.avin` builds the program and
runs it under `script`, which gives it a pseudo-terminal, to check that it draws on the alternate
screen, quits on Ctrl-C and puts the terminal back.
