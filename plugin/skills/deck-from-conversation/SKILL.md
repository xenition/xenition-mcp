---
name: deck-from-conversation
description: Use when the user wants the conversation so far, a document of theirs, or meeting notes turned into a slide deck — "make this into slides", "turn our plan into a pitch deck", "I need a presentation from this doc".
---

# A deck from what is already here

`create_slides` designs a deck from a brief. The quality of the deck is the
quality of the brief — so build the brief from the material, not from memory.

## 1. Gather the material

- From the conversation: pull the decisions, numbers, names and conclusions
  already agreed. Leave out options that were rejected.
- From a file: find it with `search_artifacts`, then `get_artifact`. For a long
  document, `summarize_artifact` with key points first.
- From an existing Xenition item you only need re-shaped: `repurpose_artifact`
  to slides does it in one step — prefer it.

## 2. Write the brief

State the audience, the goal of the deck, the slide count (default 8–12), and
an outline of one line per slide carrying the actual facts. Include any real
numbers verbatim. Name a tone (investor, internal update, classroom).

## 3. Create, then refine

Call `create_slides` with the brief and a title. Share the link. For changes
("shorter", "add a pricing slide", "less text"), revise the brief and call
`create_slides` again, or point the user to the deck editor for small tweaks —
`edit_artifact` is built for documents and notes, not decks. `export_pdf` works on documents, not decks —
for a PDF of a deck, point the user to Export in the editor.

## Rules

Never invent figures, quotes or customer names that are not in the material;
leave a clearly marked placeholder instead.
