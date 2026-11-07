# Typing practice

A terminal typing practice program written in Avin, using `dev.avinlang.tui`.

From this workspace:

```sh
avin run typing-practice
```

Or from this directory:

```sh
avin run .
avin test .
```

The manifest fetches `avin-lang/tui` version `0.1.0` automatically. Run in an
interactive terminal at least 40 columns wide and 15 rows tall.

Choose a mode with Up/Down and Enter, or press its number:

1. **Short passages**: 24 short excerpts from Austen, Carroll, Melville, Doyle,
   Dickens, and Stevenson, chosen randomly. The author and work appear above
   the passage. See [sources and text normalization](SOURCES.md).
2. **Longer passages**: 8 longer literary excerpts for sustained practice,
   with author and book attribution.
3. **Tricky words**: randomized 24-word drills from 40 words covering repeated
   letters, awkward sequences, capitalization, contractions, and punctuation.
4. **Practice my mistakes**: randomized drills of up to 24 unique words you
   mistyped during this run, including mistakes fixed with backspace. Words
   retain their source capitalization and apostrophes inside contractions
   (such as `I'm` and `don't`). `I` and its contractions keep a capital `I`.
   Surrounding punctuation, symbols, and digits are removed; curly apostrophes
   become straight apostrophes. Case variants count as one entry, retaining
   the first source spelling. Words do not repeat within a drill. Mistakes
   at spaces are ignored when collecting words. History lasts until you quit.

The first passage and each subsequent passage are chosen randomly. Passage
modes never immediately repeat the current passage. Ctrl-R keeps the same text.

Type the text as shown. The clock starts on your first printable character.
Correct characters turn green; mistakes turn red, with incorrect spaces shown
as dots. Backspace lets you correct mistakes until the drill is complete.
Words wrap together, and the passage scrolls as you type or resize the terminal.

- **Ctrl-R** retries the current drill with fresh scores.
- **Tab** chooses another drill in the same mode.
- **Enter** chooses another drill after completion.
- **Esc** returns to the menu; Esc from the menu quits.
- **Ctrl-C** quits from either screen and restores the terminal.

Completion occurs when you have typed as many characters as the passage,
including any remaining mistakes. WPM counts correct characters currently in
the text, divided by five, per minute. Accuracy is correct keystrokes divided
by all printable keystrokes: correcting a mistake does not erase that attempt.
The final time and scores freeze at completion. Paste events are ignored.

Tests cover scoring, timing, corrections, navigation, randomized selection,
word extraction, personal drills, wrapping, and rendering without a terminal.
