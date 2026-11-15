# Anki Card Skills · What makes a card worth keeping?

**English** · [简体中文](README.zh-CN.md) · [Back to Bill](../../README.md) · [Project](https://github.com/Bill306/anki-card-skills)

Reading once is a moment. Remembering next month takes a little more care.

## Explore the output

1. **[Browse the source PDF](https://github.com/Bill306/anki-card-skills/blob/main/examples/lumabox/lumabox-test.pdf).** The included LumaBox teaching example has four pages, including a scanned page. Its subject matter is fictional and explicitly labeled in the source.
2. **[Read the cards and their evidence](https://github.com/Bill306/anki-card-skills/blob/main/examples/lumabox/output/review.md).** Each question has an answer, a physical PDF page number, and supporting text. The coverage section records included, repeated, and unanswered concepts.
3. **[Download the sample deck](https://github.com/Bill306/anki-card-skills/raw/refs/heads/main/examples/lumabox/output/deck.apkg).** Import the downloaded `.apkg` through Anki's File → Import menu. The sample contains 12 cards: 10 Basic and 2 Cloze, with one evidence image.

The first two steps can be viewed on GitHub. Importing the deck requires Anki. Creating cards from your own PDF requires an Agent with the [installed Skill](https://github.com/Bill306/anki-card-skills#install-and-use).

![Review page generated from the repository's included sample](https://raw.githubusercontent.com/Bill306/anki-card-skills/main/docs/images/preview.png)

## Decision: keep the answer close to its evidence

**The user problem.** A polished answer can still be difficult to check. When revising study material, the learner needs to find the passage behind a card.

**The design.** Preserve the source document, physical page number, and evidence with each answer. Keep the explanation separate from the short recall answer. Deliver an editable `cards.json` and a review document alongside the deck.

**The consequence.** The learner has a deliberate review step before import and a route back to the material when correcting a card. That review takes attention; the product makes the supporting information available at the point of checking.

**Inspect it.** Open any card in the sample review and follow its page reference in the source PDF.

## Decision: make missing information visible

The sample source gives an observed writing rate and explicitly leaves maximum throughput unspecified. The coverage record marks the missing maximum as `blocked`, while a separate card preserves the distinction between an observation and a maximum. The export records `PARTIAL_SOURCE_COVERAGE` so the gap remains visible.

This is a useful product boundary: completing a deck also involves showing which questions still need source material. You can inspect the exact entry in the [coverage audit](https://github.com/Bill306/anki-card-skills/blob/main/examples/lumabox/output/audit.json).

## Decision: preserve identity when revising a deck

Stable deck and card IDs preserve note GUIDs across exports. That gives revisions an identity Anki can match during import. The documented checks cover repeated imports and an answer update; the update behavior also depends on Anki's import settings and local edits.

## Evidence and current scope

The repository's [verification record](https://github.com/Bill306/anki-card-skills/blob/main/docs/verification.md), dated 2026-10-20, records an actual import through the official Anki backend, 12 notes/cards, media checks, repeated import, and an answer update. It establishes those packaging and import behaviors for the included example. Learning effectiveness and independent learner evaluation remain open questions.

The current exporter supports Basic, single-cloze, and image-assisted cards. Native Image Occlusion is outside the implemented scope. Scanned-page reading depends on the executing Agent's capabilities.

[Project and installation](https://github.com/Bill306/anki-card-skills) · [Back to the other projects](../../README.md#things-ive-been-building)
