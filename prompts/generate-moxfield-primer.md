---
name: generate-moxfield-primer
description: Generates a comprehensive, copy-pasteable Magic: The Gathering deck primer formatted specifically for Moxfield's custom markdown syntax from a provided decklist or Moxfield link.
---

# Moxfield Decklist Primer Generator

## Overview
This skill analyzes a Magic: The Gathering decklist (provided as plain text or a Moxfield URL) and generates a Markdown primer tailored specifically to Moxfield's custom markdown syntax (including card tooltips, mana symbols, and centering blocks).

## Workflow

### Step 0: Writing Style
You must write in a factual, descriptive writing style that does not include flowery language that attempts to do a salesman job for the deck. Avoid listing positive adjectives everywhere when you write content, only describe things that are notably unique. 

### Step 1: Input Gathering & Deck Analysis
1. **Check for Decklist:** Ensure the user has provided either a raw text decklist or a Moxfield link. If missing, prompt the user to provide one along with their target format (e.g., Commander/EDH, cEDH, Modern, Pauper) and intended power level/bracket if not obvious.
2. **Analyze the List:** Identify:
   - The Commander(s) or build-around engine(s) and color identity.
   - Primary archetype (e.g., Turbo Combo, Midrange Value, Stax, Control, Aggro).
   - Win conditions, infinite combos, and layered synergy lines.
   - Core engine pieces, tutors, ramp, and interaction suites.
   - Notable deckbuilding restrictions (e.g., singleton mana base for `[[Tainted Pact]]`, companion requirements, budget constraints).

### Step 2: Moxfield Formatting Rules (Strictly Enforce)
Moxfield uses a custom flavor of Markdown. You MUST adhere to these exact syntax rules so the user can copy and paste the output directly into Moxfield without broken embeds:
- **Card Hover Tooltips:** Wrap EVERY Magic card name in double brackets: `[[Card Name]]`.
  - For double-faced/split cards, use the full name separated by ` // `: `[[Front Name // Back Name]]`.
- **Mana & Game Symbols:** Use `[[symbol:X]]` where `X` is lowercase (`w`, `u`, `b`, `r`, `g`, `c`, `1`, `2`, `t` for tap, `x`, etc.).
- **Centering Blocks:** Use `===center` and `===endcenter` on their own lines to center headers, symbol dividers, and art crops.
- **Commander Art Banner:** Include a Scryfall art crop placeholder or actual URL using standard Markdown image syntax inside the header center block: `![Commander Name](https://cards.scryfall.io/art_crop/...)`. (If the exact Scryfall image ID is unknown, use a clean placeholder URL and add a brief note instructing the user to swap in their preferred art crop URL).
- **Clean List Formatting:** Avoid stray empty bullet points or broken line wraps inside list items. Keep bullet formatting clean (`- [[Card Name]] — Explanation`).

### Step 3: Primer Structure & Required Sections
Generate the primer, including the following sections, tailored to the depth and complexity of the deck. Each section should assume the reader has a high level knowledge of MTG, and thus should only contain notable interactions or synergies that are above standard deck operation. E.g. don't cover typical ramp cards, but explain why the architecture of this deck or its commander makes certain cards perform well above their baseline. Do not cite too many cards, just those that are critical to understanding how the deck plays and why. When explaining the commander's utility, or why we run the cards we do, cite what situations they are strong in, or what result we get from running them, rather than rewording what they do an explaining why that effect is a good thing.

1. **Header Banner (`===center`)**
   - A decorative top and bottom border made of alternating `[[symbol:x]]` tags matching the deck's color identity (approx. 30–36 symbols wide).
   - `# Deck Title`
   - Centered art crop image of the Commander or flagship card. Use Scryfall art crop links to select a proper card, or use the following image link of a Black Lotus as a template: https://cards.scryfall.io/art_crop/front/b/d/bd8fa327-dd41-4737-8f19-2cf5eb1f7cdd.jpg?1783939332
2. **Introduction & Overview**
   - Explanation of why the commander/archetype is exciting, its core mechanical identity, and what sort of gameplan it prefers (control/aggro/combo/midrange and subcategories, etc).
   - Optional placeholder section for external references/variants (e.g., budget versions or related primers), or other relevant links the user might have. Do NOT relate to the moxfield list, as this primer will be going on that page. 
3. **Gameplan & Mulligan Strategy**
   - **Early Game (Turns 1–2):** Ramp, setup, and ideal opening hands (what to keep vs. what to ship). Use the context of the deck's gameplan (aggro vs combo, etc) to explain what is risky and what is desired in an opening hand. When discussing opening hands, talk about the TYPES of cards we are looking to have, don't just list opening hand examples.
   - **Mid Game (Turns 3–4, if applicable):** Engine assembly, value generation, and navigating interaction. How does the deck recover from a win attempt or push being stopped?
   - **Late Game / Closing:** How does the deck push for win attempts and protect itself on the winning turn.
4. **Win Conditions & Combos**
   - Step-by-step breakdowns of every combo and primary win line in the deck.
   - Format: `- [[Card A]] + [[Card B]] = Clear explanation of prerequisites, mana requirements, execution steps, and payoff.`
   - Note that decks will often run layered combos, meaning that combos may have interchangeable pieces. If the result of the combo is the same no matter which cards we swap in, we can keep things as a one-liner, otherwise we can have a line for each combo variant.
5. **Important Cards & Synergy Packages**
   - Group key non-combo cards by role (e.g., **Value Engines**, **Key Tutors**, **Protection & Silence Effects**, **Unique Tech**). Explain *why* they are vital rather than just reading the card text.
6. **Notable Includes**
   - Cards that might look surprising or niche at first glance, explaining the specific meta call or synergy that earned them a slot.
7. **Notable Excludes**
   - Popular staples in the archetype/colors that were intentionally cut, explaining the deckbuilding rationale (e.g., non-bos, mana curve constraints, anti-synergy).
8. **On-The-Fence / Flex Slots**
   - Cards currently being tested, meta-dependent flex slots, or budget swaps for different pods/brackets.

## Example Output Template

```markdown
===center
[[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]]
# [Deck Name]
[[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]][[symbol:g]][[symbol:b]]

![Commander Name](https://cards.scryfall.io/art_crop/front/0/0/00000000-0000-0000-0000-000000000000.jpg)
===endcenter

[Engaging 1–2 paragraph introduction covering the deck's core theme, commander synergies, and overall feel.]

### Helpful References
- [Link Title](https://moxfield.com/decks/example)

## Gameplan & Mulligans
- **Opening Hands:** [Describe ideal early acceleration, draw engines, and what hands to mulligan.]
- **Early Game:** [Establishing mana and board presence.]
- **Mid-to-Late Game:** [Sculpting a protected win window or out-valuing the table.]

## Combos & Win Conditions
- [[Card A]] + [[Card B]] = [Step-by-step execution, prerequisites, and outcome.]
- [[Card C]] + [[Card D]] + [[Card E]] = [Step-by-step execution, prerequisites, and outcome.]

## Important Cards
- [[Engine Piece]] — [Why this card drives the deck's core strategy.]
- [[Key Tutor]] — [Primary lines this tutor unlocks.]

## Notable Includes
- [[Tech Card]] — [Specific synergy or meta reason this card made the cut.]

## Notable Excludes
- [[Common Staple]] — [Why this popular card was left out of this specific build.]

## On-The-Fence Cards
- [[Flex Card]] — [What this card is being tested for and what could replace it.]