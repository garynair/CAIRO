# CAIRO Anki Deck

A ready-made flashcard deck covering key facts and distinctions from all twelve modules — named frameworks, specific article/section citations, structural facts (counts, categories), and the recurring conceptual distinctions the curriculum draws (e.g., governance vs. compliance, inherent vs. residual risk).

This is a starting point, not a substitute for the module exercises — the exercises test your ability to produce a real deliverable (a crosswalk, a charter, a risk register); this deck is for keeping named frameworks, article numbers, and structural facts cold. Use it while you read, review it before a capstone, and add your own cards as you go deeper into each module.

## How to import

1. Install [Anki](https://apps.ankiweb.net/) (free, desktop and mobile) if you don't have it.
2. Open Anki → **File → Import**.
3. Select [`cairo-deck.txt`](cairo-deck.txt).
4. Anki auto-detects the format from the file's header lines (tab-separated, plain text, three columns: Front, Back, Tags). Confirm the field mapping looks right (Field 1 → Front, Field 2 → Back, Field 3 → Tags) and import.
5. Cards land tagged by module (e.g., `CAIRO::mod101`, `CAIRO::mod106`). Use Anki's **Browse** view to filter by tag and study one module at a time, or study the whole deck together.

## Coverage

52 cards across all twelve modules as of this writing — every module has at least 2 cards, the modules with the deepest lecture-note content (101, 102, 106, 108) have more. This deck is deliberately not exhaustive: it covers named frameworks, specific citations, and structural facts you want cold-recall fluency on, not every nuance in the lecture notes (that's what re-reading the chapter is for).

## Contributing more cards

Good candidate cards:

- A named framework/standard and what it specifically requires (e.g., "Which EU AI Act article covers X?").
- A structural fact with a specific count (e.g., "How many trust-gate placement patterns does mod-106 name?").
- A distinction the module explicitly draws (e.g., governance vs. compliance, leading vs. lagging indicator).

Avoid cards that require a paragraph-long answer — if the back doesn't fit in one or two sentences, it's a discussion topic for the module, not a flashcard.

Add new rows to `cairo-deck.txt` in the same `Front\tBack\tCAIRO::modXXX` format, or add a `SOLUTION.md`-informed card after you've done an exercise and want to lock in something you got wrong.

---

Maintained by [Girish Nair](https://github.com/garynair)
