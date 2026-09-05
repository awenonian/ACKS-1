# Playtest 01 — ACKS II: character creation and the Mirmen road

**Session 1.** Full transcript, in order.

| | |
|---|---|
| **Date** | 2026-08-24 (the session's own clock reported 2026-09-05) |
| **System** | ACKS II Imperial Imprint, via the bundled `acks-ii` rules skill |
| **Started from** | character creation |
| **Where it ran** | Claude Code on the web, remote container, entrypoint `remote_mobile` |
| **Branch** | `claude/acks-character-creation-izgrz2`, fast-forwarded onto the repo's default branch at end of session |
| **Session id** | `17f7c5a0-5b45-5b48-a119-5b7f34898dfa` |

**Opening message, verbatim:** "I want to play a session of ACKS. We can start with
character creation."

## What this is

Player and GM text is **verbatim and untidied**, in the order it happened — the same
rule the campaign record follows, for the same reason.

**Tool calls are included in full**, collapsed under `tool —` summaries. Every dice
roll and every oracle consultation is here with its output untruncated, because that
is the main thing a playtest of this prompt is for: the transcript should show whether
the numbers arrived before the narration or after it. Long non-random outputs (rules
lookups, file writes) are cut to their first 1,500 characters.

**Turns are labelled by who actually spoke.** `Player` is a human turn. `System` is
the harness talking — stop-hook messages, skill-load banners. They are kept because
they interrupted play and a reader should see where.

**What was removed:** noise injected into the user turns by the runtime rather than
typed by anyone — `<system-reminder>` blocks, the skill-availability listing repeated
before most turns, MCP connect/disconnect notices, agent-type listings, and token
counters. 3 non-human user turns were processed this way.

**There were no `log:` entries this run.** Nothing was flagged during play.

**The export is not in here.** After the session closed the player asked for this
transcript to be written into the repo. That request and the GM's reply are kept
below, because they happened; the tool calls that read the session log and built this
file are not, because they would embed the transcript inside itself. The final GM turn
of the session is therefore the last thing recorded.

---

### Player

I want to play a session of ACKS. We can start with character creation.

### GM

I'll start by reading the campaign notes and loading the ACKS rules.

<details><summary>tool — List repo and read notes README</summary>

```
ls -la && echo "--- README ---" && cat notes/README.md 2>/dev/null
```

</details>

<details><summary>tool — load rules skill</summary>

```
acks-ii-gm
```

```
total 64
drwxr-xr-x 8 root root  4096 Aug 24 18:12 .
drwxr-xr-x 3 root root  4096 Aug 24 18:12 ..
drwxr-xr-x 3 root root  4096 Aug 24 18:12 .claude
drwxr-xr-x 8 root root  4096 Aug 24 18:12 .git
-rw-r--r-- 1 root root 21545 Aug 24 18:12 CLAUDE.md
-rw-r--r-- 1 root root  5307 Aug 24 18:12 README.md
drwxr-xr-x 3 root root  4096 Aug 24 18:12 docs
drwxr-xr-x 5 root root  4096 Aug 24 18:12 notes
drwxr-xr-x 2 root root  4096 Aug 24 18:12 playtests
drwxr-xr-x 2 root root  4096 Aug 24 18:12 scripts
--- README ---
# Notes

Everything that survives between sessions. A session starts with the GM knowing
nothing but `CLAUDE.md` and this tree.

Two axes organise it. The **directory** is who the notes are for; the **file**
is what kind of thing they are. `CLAUDE.md` defines both axes — this file is
just the map.

```
notes/
  player-owned/     the player's, not yours. Don't edit without permission.
  player-facing/    what the player knows, or what people in the world know.
    RECORD.md       what happened, in play order, append-only, never tidied
    STATE.md        the ledger of known things
    POSITIONS.md    what characters committed to, in the open
  gm/               your journal. Nobody else reads it. Hide nothing from yourself.
    STATE.md        the truth behind the ledger — secrets, clocks, offscreen movement
    THREADS.md      every open loop and its status. Nothing ambiguous.
    CLUES.md        the mystery as a graph: revelations, who knows what
    characters/     one fil
… (truncated)
```

</details>

> **System —** Base directory for this skill: /root/.claude/skills/synced/acks-ii-gm
> 
> # ACKS II Imperial Imprint — GM Reference
> 
> > **⚠ Reliability Warning:** The AI's prior knowledge of ACKS II may be inaccurate, outdated, or conflated with other systems. Every rule invoked during play must be verified against these files before being applied. Do not trust the AI's unprompted recall of specific numbers, table entries, or rule text.
> 
> ---
> 
> ## Finding Rules
> 
> **For specific lookups** (a named ability, condition, spell, or concrete question like "can I cleave after a special maneuver?"): use the **search tool** first with a keyword or plain-language question.
> 
> **For broad topics** (how does combat work? how do domains function?): use the **Contents** section below to identify the right file and open it.
> 
> **Critical:** A search result is a *summary only* — it locates the right file but may omit exact values, conditions, ranges, or restrictions. Before answering, **open and read the matched file in full**. For reference tables, read **the complete row**, not just the snippet — table rows rarely survive search intact.
> 
> ---
> 
> ## Core Rules Summary
> 
> *All mechanics below are extracted verbatim or directly paraphrased from the source IR. Nothing here is assumed from prior knowledge.*
> 
> ### Resolution: Throws
> 
> > "A throw occurs whenever a character or monster is taking an action that will succeed or fail."
> > — Roll 1d20, add modifiers, compare to a **target value** expressed as `#+`.
> > — **Equal to or exceeding** the target value = success. Below = failure.
> > — **Unmodified 1** always fails. **Unmodified 20** always succeeds *if the character is proficient* in the task; non-proficient characters do not auto-succeed on 20.
> > *(Source: p.11–12)*
> 
> **Adjusting target values:** A bonus reduces the target value; a penalty increases it. Mathematically identical to modifying the die roll. *(p.12)*
> 
> **Rounding:** Round to nearest whole number; 0.5 rounds to nearest even (0.5→0, 1.5→2, 4.5→4). *(p.12)*
> 
> ---
> 
> ### Attack Throws
> 
> Roll 1d20 + modifiers vs. target value from the Attack Throw table (p.298) **+ target's AC**.
> - STR modifier applies to melee attack throws and damage rolls.
> - DEX modifier applies to missile attack throws.
> - Unmodified 1 = always miss; unmodified 20 = always hit.
> - Damage modifiers cannot reduce a successful hit below 1 hp except by magic. *(p.297, p.301)*
> 
> **Key attack throw bonuses/penalties:**
> | Situation | Modifier |
> |---|---|
> | Charge / countercharge | +2 attack |
> | Flanking attacker | +2 attack |
> | Attacker at higher elevation (subjacent target) | +1 attack |
> | Attacking from rear (vulnerable target) | +2 attack |
> | Blinded attacker | -4 attack |
> | Missile, medium range | -2 attack |
> | Missile, long range | -5 attack |
> | Most special maneuvers | -4 attack |
> 
> ---
> 
> ### Action Economy (per Round)
> 
> Each combatant gets **one** of the following each round:
> - **One full-round action** (cast spell, charge, run, retreat, etc.)
> - **Two movement actions**
> - **One movement action + one combat action**
> 
> Movement action must be taken before the combat action. *(p.295)*
> 
> **Pre-initiative declaration required for:** casting spells, retreat, withdraw. *(p.293)*
> 
> ---
> 
> ### Initiative
> 
> Roll **1d6** + DEX modifier. Judge counts down from 10; combatants act when their number is called. A combatant may **delay** up to the negative of their initiative number (e.g., init 5 may delay to −5). *(p.293–294)*
> 
> ---
> 
> ### Saving Throws
> 
> Five categories (in priority order, top = use first):
> 1. **Paralysis** — immobilizing effects (paralysis, sleep, fear, petrification)
> 2. **Death** — instant death, disease, disintegration, blindness
> 3. **Blast** — area damage (breath weapons, explosions, artillery)
> 4. **Implements** — magical items (rings, rods, staves, wands)
> 5. **Spells** — any other cast spell
> 
> Roll 1d20 + WIL modifier (and others) vs. class/level target value. Unmodified 1 = always fail; unmodified 20 = always succeed. *(p.305)*
> 
> ---
> 
> ### Cleaving
> 
> When a combatant **reduces an opponent to 0 or fewer hp** with a melee or missile attack, it may immediately make another attack against another target in range, with the same weapon.
> 
> - **Fighters / HD-based monsters:** max cleaves per round = Hit Dice.
> - **Crusaders / Thieves:** max cleaves = ½ Hit Dice (rounded down).
> - **Mages:** cannot cleave.
> 
> Cleave after a charge retains +2 attack and impact damage only if the combatant takes a **5' step** after each cleave. *(p.304)*
> 
> ---
> 
> ### Damage & Death
> 
> - At **0 hp or fewer**: unconscious, fate uncertain until wounds are treated.
> - Treat wounds → roll **1d20 + 1d6** on the Mortal Wounds table (Appendix C, p.517). Modified 1d20 determines condition; unmodified 1d6 determines permanent wound.
> - **Constructs, incarnations, undead** reduced to 0 hp are immediately destroyed. Plants and oozes at 0 hp are immediately slain.
> - Natural healing: **1d3 hp per full day of rest** in reasonably sanitary conditions. *(p.303)*
> 
> ---
> 
> ### Key Condition Modifiers (Frequently Referenced)
> 
> | Condition | Key Effect |
> |---|---|
> | **Vulnerable** | +2 to all attack throws vs. creature; eligible for ambush/backstab at +4 |
> | **Prone** | −4 attack throws; all attackers gain +2 (vulnerable) |
> | **Flanked** | Attackers gain +2 (never stacks with vulnerable; vulnerable takes precedence) |
> | **Disordered** | −2 AC; ends at start of own next initiative |
> | **Blinded** | −4 melee attack; no missile attacks; speed reduced to 1/3 |
> | **Charging** | +2 melee attack, −2 AC (disordered) until next initiative |
> | **Surprised** | Cannot act; vulnerable; ends at start of next round |
> | **Frightened** | Must flee at full speed; cannot attack or cast spells |
> | **Faltering** | −2 attack throws, proficiency throws, and saving throws vs. source |
> | **Grabbed/Wrestled** | Cannot act except to escape; vulnerable |
> 
> ---
> 
> ## Contents
> 
> | File | Description |
> |---|---|
> | `introduction.md` | Core dice resolution, throw mechanic, abbreviations, and how the game works |
> | `characters.md` | Character creation, attributes, AC, HP, combat stats, alignment |
> | `classes.md` | All character classes, progression tables, class powers, templates |
> | `proficiencies.md` | Proficiency rules, per-class acquisition, full proficiency descriptions |
> | `equipment.md` | Weapons, armor, gear costs, encumbrance, hirelings |
> | `spells.md` | Spellcasting rules, spell lists, spell descriptions |
> | `adventures.md` | Dungeon and wilderness exploration, encounters, reactions, evasion |
> | `combat.md` | Initiative, actions, attacks, damage, special maneuvers, conditions, mounted combat |
> | `voyages.md` | Sea travel, naval combat, weather, underwater rules |
> | `campaigns.md` | Strongholds, domains, realms, magic research, hijinks |
> | `armies.md` | Raising and organizing armies, troop types, unit morale |
> | `maneuvers.md` | Strategic movement, supply, reconnaissance, pillaging |
> | `battles.md` | Large-scale battle resolution, hero forays, pursuit |
> | `sieges.md` | Blockade, bombardment, assault of fortifications |
> | `setting.md` | Auran Empire lore, timeline, peoples, deities, languages |
> | `conditions-reference.md` | All conditions, their effects, and how they end |
> | `wounds-and-woe.md` | Mortal wounds tables by damage type; tampering with mortality |
> | `resources.md` | Character sheets, indexes, appendices |
> | `tables/` | Quick-reference tables for troops, deities, classes, spells, monsters, equipment, etc. |
> 
> ---
> 
> ## Preload Guidance
> 
> Read these files **in full at session start** based on session type:
> 
> | Session Type | Read in Full |
> |---|---|
> | **Combat-heavy / dungeon** | `combat.md`, `conditions-reference.md` |
> | **Wilderness / travel** | `adventures.md`, `combat.md` |
> | **Naval / sea** | `voyages.md`, `combat.md` |
> | **Domain / campaign turn** | `campaigns.md`, `armies.md` |
> | **Strategic warfare** | `maneuvers.md`, `battles.md`, `armies.md` |
> | **Siege** | `sieges.md`, `combat.md` |
> | **Character creation session** | `characters.md`, `classes.md`, `proficiencies.md`, `equipment.md` |
> | **Any session with spellcasters** | `spells.md` (relevant spell entries) |
> | **Any session with mortal wounds** | `wounds-and-woe.md` |
> 
> ## Searching These Rules
> 
> This skill bundles a search script next to these files. To find a specific rule,
> run it from the skill's directory:
> 
> ```
> python search.py "your search term"
> ```
> 
> It scans every rules file and returns matching section headings and snippets with
> their file paths — enough to answer directly or to know which file to open. Use it
> for specific lookups (a keyword, condition, ability, or "can I do X if Y?"
> interaction); use the Contents list above to orient on a whole topic. Options:
> `--max-results N`, `--context N`, `--regex`.

<details><summary>tool — Read notes tree and key files</summary>

```
find notes -type f | head -50 && echo "=== CAMPAIGN ===" && cat notes/gm/plans/CAMPAIGN.md 2>/dev/null; echo "=== gm/STATE ===" && cat notes/gm/STATE.md 2>/dev/null; echo "=== player-facing/STATE ===" && cat notes/player-facing/STATE.md 2>/dev/null
```

```
notes/gm/plans/README.md
notes/gm/plans/CAMPAIGN.md
notes/gm/THREADS.md
notes/gm/characters/TEMPLATE.md
notes/gm/characters/README.md
notes/gm/README.md
notes/gm/STATE.md
notes/gm/CLUES.md
notes/README.md
notes/player-owned/README.md
notes/player-facing/RECORD.md
notes/player-facing/README.md
notes/player-facing/STATE.md
notes/player-facing/POSITIONS.md
=== CAMPAIGN ===
# Campaign

Fill this in from the player's first message, so that no later session has to
ask again.

- **System:**
- **Started from:** <character creation / an existing character / mid-campaign>
- **Rules skill in use:**
- **House rules and table conventions:**

## Lines and veils

Settled with the player before the first scene, revisited as the campaign finds
its shape. Lines stay out entirely; veils happen off-page.

- **Lines:**
- **Veils:**
- **Last checked:**

## The long shape

What this campaign is about, and where it is pointed. Revise it when play
demands; keep it consistent with everything already revealed.
=== gm/STATE ===
# State — GM-facing

The truth behind the ledger. Secrets, who is actually where, what is moving
offscreen, clocks and how far along they are, what a thing really is.

Terse and revised freely, like the player-facing ledger — but this one is
allowed to know things.

Mark anything that hasn't reached play yet, so a later session doesn't mistake
your decision for something the table established.

## Chaos factor

**5** — how much the world intrudes, 1 to 9. Feeds `scripts/oracle.py
… (truncated)
```

</details>

<details><summary>tool — List rules files with sizes</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && ls && wc -l *.md
```

```
SKILL.md
active_rules.md
adventures
adventures.md
annotations.md
armies
armies.md
battles
battles.md
campaigns
campaigns.md
characters
characters.md
classes
classes.md
combat
combat.md
conditions-reference.md
equipment
equipment.md
introduction
introduction.md
maneuvers
maneuvers.md
proficiencies
proficiencies.md
resources
resources.md
search.py
search_index.json
setting
setting.md
sieges
sieges.md
spells
spells.md
tables
voyages
voyages.md
wounds-and-woe
wounds-and-woe.md
   187 SKILL.md
     6 active_rules.md
    47 adventures.md
     4 annotations.md
    33 armies.md
    24 battles.md
   124 campaigns.md
    52 characters.md
    49 classes.md
    34 combat.md
   727 conditions-reference.md
    46 equipment.md
    10 introduction.md
    32 maneuvers.md
    27 proficiencies.md
    14 resources.md
    19 setting.md
    37 sieges.md
    34 spells.md
    54 voyages.md
    38 wounds-and-woe.md
  1598 total
Shell cwd was reset to /home/user/ACKS-1
```

</details>

<details><summary>tool — Read character and class index files</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && cat characters.md && echo "===CLASSES===" && cat classes.md && echo "===DIR===" && ls characters classes
```

```
## Quick Reference

**Character Creation (11 steps):** Roll attributes (5d6 drop 2 for first, 4d6 drop 1 for second and third, 3d6 for rest; minimum 13 for first, 9 for second/third); choose class (must meet key attribute minimums of 9); roll hit points (minimum 4, add CON modifier); roll template; note proficiencies and spells; select starting equipment; calculate AC and encumbrance; determine homeland, age, languages, alignment.

**Attributes (scores 3–18):** Six core attributes (Strength, Intellect, Will, Dexterity, Constitution, Charisma) each grant a bonus or penalty (−3 to +3). Bonus/penalty applies to specific rolls: STR to melee/thrown damage and Dungeonbashing (×4); INT to proficiencies and languages; WIL to saving throws; DEX to missile attacks and AC; CON to hit points; CHA to reaction rolls and henchmen (4 + CHA modifier = 1–7 henchmen).

**Combat Characteristics:** Classes grant proficiencies in armor types (very light, light, medium, heavy, or all), weapon categories (size/type), and fighting styles (missile weapon, single weapon, dual weapon, two-handed weapon, weapon and shield). Non-proficient use (1st level+) attacks as 0th level fighter; 0th level non-proficient gets additional −1 penalty. Each class has attack throw and saving throw progression tables; some grant damage bonuses or cleaving.

**Hit Points:** Rolled using class die (minimum 4 result), plus CON modifier (penalty cannot reduce below 1 per die). Represents character vitality; reduced by damage,
… (truncated)
```

</details>

<details><summary>tool — Read character creation entries</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && sed -n '1,200p' characters/entries.md
```

```
# Characters

## Armor Class

### Quick Reference

**Armor Class (AC)** measures how difficult it is to damage a character. An unarmored character of average attributes has AC 0. AC is determined by:
- Armor worn
- Shield equipped (if any)
- DEX modifier
- Class powers, proficiencies, conditions, magic items, and spells

Calculate and record AC on your character sheet after purchasing equipment.

---

### ARMOR CLASS

Armor class (AC) is a measure of how challenging it is to damage your character. An unarmored character of average attributes has an AC of 0. AC is determined by what kind of armor the character is wearing and whether he has a shield equipped. AC can be modified by the character's DEX modifier and certain class powers, proficiencies, conditions, magic items, and spells. After you buy your equipment, calculate your character's AC and record it on your character sheet.

*[Source: ACKSII_Revised_Rulebook_DIGITAL_FINAL_r10_2nd_Printing.pdf, p.19]*

---

### See Also

[Armor & Barding Reference Table](../tables/equipment/entries.md#armor-table)
[Combat Characteristics](entries.md#combat-characteristics)
[Equipment Basics & Availability](../equipment/equipment-basics.md)
[Weapon & Armor Descriptions](../equipment/weapon-descriptions.md)

---

## Attributes

### Quick Reference

**Attribute Score Bonus/Penalty Table:**

| Score | Modifier |
|-------|----------|
| 3 | −3 |
| 4–5 | −2 |
| 6–8 | −1 |
| 9–12 | 0 |
| 13–15 | +1 |
| 16–17 | +2 |
| 18 | +3 |

**Key Attribute 
… (truncated)
```

</details>

<details><summary>tool — List headings in characters entries</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && grep -n "^## \|^### " characters/entries.md | head -60
```

```
3:## Armor Class
5:### Quick Reference
17:### ARMOR CLASS
25:### See Also
34:## Attributes
36:### Quick Reference
62:### Character Attributes
123:### Classes and Attributes
137:### See Also
146:## Combat Characteristics
148:### Quick Reference
161:### Combat Proficiencies
232:### Combat Progression
256:### Class Powers
266:### See Also
280:## Creating A Character
282:### Quick Reference
299:### Character Creation Procedure
348:### Optional Rules for Character Creation
368:### See Also
380:## Hit Points
382:### Quick Reference
396:### Standard Rules
424:### Optional Rules for Hit Points
454:### See Also
463:## Languages Age Alignment
465:### Quick Reference
481:### Languages
489:### Starting Age
509:### Character Aging
540:### Death from Old Age
558:### Size & Weight
571:### Alignment
597:### See Also
605:## Speed And Encumbrance
607:### Quick Reference
619:### Calculating Encumbrance
657:### Calculating Speed
684:### See Also
Shell cwd was reset to /home/user/ACKS-1
```

</details>

<details><summary>tool — Read creating a character procedure</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && sed -n '280,380p' characters/entries.md
```

```
## Creating A Character

### Quick Reference

**Character Creation Steps (Summary)**
1. Obtain a character sheet
2. Roll attributes (Strength, Dexterity, Constitution, Intelligence, Wisdom, Charisma)
3. Choose a character class (which includes race)
4. Record 0 experience points
5. Roll hit points using your class die; minimum 4, add Constitution modifier
6. Roll 3d6 on your class's template table; may choose a lower result but not higher
7. Write starting proficiencies from template; all characters gain Adventuring proficiency
8. If a caster, write starting spells from template
9. Record starting equipment and gold; calculate Armor Class and encumbrance
10. Choose homeland and sex; roll starting age; write languages; record size and weight
11. Create name, appearance, background, personality, and alignment; form adventuring party

---

### Character Creation Procedure

Follow these eleven steps to create a character:

#### Step 1: Obtain a Character Sheet
Break out a new character sheet. You can use the one provided in the rulebook, download and print a fan-made character sheet, or reproduce an existing sheet by hand on a piece of paper. If all else fails, scribble down notes on scratch paper.

#### Step 2: Roll Attributes
Roll for your character's attributes, as described below in Character Attributes. Write the results after the names of the abilities and record the attribute bonus or penalty for each score.

> **Note:** Some campaigns might use optional rules that change 
… (truncated)
```

</details>

<details><summary>tool — Check branch and test roll script</summary>

```
git branch --show-current && python3 scripts/roll.py '3d6' && sed -n '1,40p' scripts/oracle.py | head -20
```

```
claude/acks-character-creation-izgrz2
     9   3d6: [4 1 4]
#!/usr/bin/env python3
"""An oracle, for questions the GM should not be allowed to answer itself.

A single intelligence running both sides of a game collapses toward
wish-fulfilment: it proposes the problem and then chooses the solution, and the
surprise goes out of it. This script is the external source of uncertainty that
prevents that. Its answers are not suggestions.

    oracle.py ask "does the harbourmaster know?" --odds unlikely
    oracle.py scene "she agrees to meet"
    oracle.py event
    oracle.py chaos

The chaos factor (1-9) tunes how often the world intrudes. It lives in
notes/gm/STATE.md, not in this script — pass it with --chaos. Raise it when the
player is losing control of the situation, lower it when they are gaining it.

`ask` also fires a random event on a doubles roll within the chaos factor, the
same way a scene check can be interrupted. When that happens the event is not
optional colour; something has just happened, and it is the GM's job to work
```

</details>

<details><summary>tool — Record system in campaign file</summary>

```
python3 - <<'EOF'
import re
p='notes/gm/plans/CAMPAIGN.md'
s=open(p).read()
s=s.replace("- **System:**","- **System:** ACKS II (Adventurer Conqueror King System, Imperial Imprint)")
s=s.replace("- **Started from:** <character creation / an existing character / mid-campaign>","- **Started from:** character creation")
s=s.replace("- **Rules skill in use:**","- **Rules skill in use:** `acks-ii-gm` (bundled ACKS II reference; search with `python3 /root/.claude/skills/synced/acks-ii-gm/search.py`)")
open(p,'w').write(s)
EOF
head -12 notes/gm/plans/CAMPAIGN.md
```

```
# Campaign

Fill this in from the player's first message, so that no later session has to
ask again.

- **System:** ACKS II (Adventurer Conqueror King System, Imperial Imprint)
- **Started from:** character creation
- **Rules skill in use:** `acks-ii-gm` (bundled ACKS II reference; search with `python3 /root/.claude/skills/synced/acks-ii-gm/search.py`)
- **House rules and table conventions:**

## Lines and veils
```

</details>

### GM

ACKS II it is. I've got the rulebook loaded and the dice are a script, so every roll happens in the open.

**One housekeeping thing first, and then I'll shut up about it.** At any point — mid-sentence, mid-scene — you can say *stop*, *skip that*, or *rewind*, and I'll do it immediately, no questions, no negotiating. I can literally un-narrate a thing and take another run at it, which a human GM can't. Use it whenever, for any reason, including "I'm just not enjoying this bit."

Related: are there subjects you want kept **out entirely** (lines), or ones that can exist in the world but happen off-page (veils)? Torture, harm to children, body horror, that sort of thing. "Nothing comes to mind, just use judgment" is a completely fine answer. ACKS is a fairly brutal system — characters die, mortal wounds leave people missing pieces — so if the gorier end of that is something you'd rather have summarised than described, now's a good time to say.

---

**Now, the character.**

ACKS rolls attributes with a weighted method: you pick **one** attribute to roll **5d6, drop the lowest two** (floor of 13), then **two more** at **4d6, drop the lowest** (floor of 9), and the remaining three are straight 3d6. So you get to aim the good dice before you know what you're playing.

The six are **Strength, Intellect, Will, Dexterity, Constitution, Charisma**. Race is folded into class here, so a dwarf or an elf is a class choice you'll make after we see the numbers.

Roughly what they're key to:

| | Points you toward |
|---|---|
| **STR** | Fighter, Barbarian, Assassin, Dwarven Vaultguard, Elven Spellsword |
| **INT** | Mage, Elven Nightblade, Elven Spellsword, Zaharan Ruinguard, Nobiran Wonderworker |
| **WIL** | Crusader, Priestess, Shaman, Bladedancer, Dwarven Craftpriest |
| **DEX** | Thief, Assassin, Bard, Bladedancer, Elven Nightblade |
| **CON** | Explorer, Barbarian |
| **CHA** | Venturer, Bard, Priestess |

Which one gets the **5d6**, and which two get the **4d6**? You can name them by attribute, or just tell me the kind of character you want to play and I'll aim the dice for you.

> **System —** Stop hook feedback:
> [~/.claude/stop-hook-git-check.sh]: There are uncommitted changes in the repository. Please commit and push these changes to the remote branch.

<details><summary>tool — Commit and push campaign notes</summary>

```
git add -A && git commit -q -m "Record ACKS II campaign start in CAMPAIGN.md

Session begins from character creation with the acks-ii-gm rules skill." && git push -u origin claude/acks-character-creation-izgrz2 2>&1 | tail -5
```

```
remote:      https://github.com/awenonian/ACKS-1/pull/new/claude/acks-character-creation-izgrz2        
remote: 
To https://github.com/awenonian/ACKS-1
 * [new branch]      claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

Notes committed and pushed to `claude/acks-character-creation-izgrz2`.

Back to you on the two questions above:

1. **Lines and veils** — anything to keep off the table, or off-page?
2. **Where the dice go** — which attribute takes the **5d6 drop 2**, and which two take the **4d6 drop 1**? Or just describe the character you want and I'll aim them.

### Player

For lines and veils, you got the list exactly actually. No violence to children, no body horror. Torture is more veil than line: I won't do it, and if it's done to a character by a villain, don't go into details, and it marks that villain as 100% a bad guy, no buts.
On character, I'm interested in playing a Venturer, and like the Antiquarian, if I remember the system, you aren't guaranteed to get to play an Antiquarian, which is based on a dice roll, or something? I'd appreciate if we fudged *that* roll, but nothing else. 
So for a Venturer, I think the recommended spread is 5d6 in CHA, and INT and WIS for 4d6? WIS helps with longer negotiations, and INT gets them extra knowledge, or something?

<details><summary>tool — Read Venturer class file</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && cat classes/venturer.md
```

```
## Quick Reference

**Venturer** – Commerce-focused class. Key Attribute: CHA. Hit Dice: 1d6. Max Level: 14.

**Combat:** Weapon proficiency with arbalests, composite bows, crossbows, daggers, knives, long bows, short bows, short swords. Armor proficiency with light, medium, very light. Fighting style: weapon and shield only. Attack/Saving Throws advance +2 per 4 levels (as thieves). No damage bonus. Cleave max once per round per 2 levels (rounded down).

**Starting Powers:**
- **Bribery:** +1 bonus to reaction rolls for one day's pay; +2 for one week's pay; +3 for one month's pay. Detected only on unmodified 2d6 roll of 2.
- **Diplomacy:** +1 to all reaction rolls when parlaying with intelligent creatures.
- **Expert Bargaining:** Buy 10% cheaper, sell 10% more expensive. If both parties have Bargaining, opposed reaction rolls determine who gets discount. Each additional Bargaining proficiency selection grants +2 to reaction roll vs. other bargainers.

**Level Progression:** Titles and XP thresholds given in table below. At 10th+ level, Hit Dice = 9d6 + flat bonus (no CON mod).

**Additional Powers by Level:**
- **2nd – Steady Trade Route (1st):** +½ class level (rounded up) to market impact for chosen merchandise type between two visited markets. One additional passive investment per route.
- **4th – Rumormongering:** 1d4 rumors from old contacts when re-visiting urban settlement (once per month per settlement, one day activity).
- **6th – Steady Trade Route (2nd):** Second
… (truncated)
```

</details>

<details><summary>tool — Record lines, veils, and chargen house rule</summary>

```
python3 - <<'PY'
p='notes/gm/plans/CAMPAIGN.md'
s=open(p).read()
s=s.replace("- **House rules and table conventions:**","""- **House rules and table conventions:**
  - **Character-creation template rolls are the player's choice, not random.** The
    player asked for this specifically for the Venturer's Antiquary template and
    was explicit that it applies to chargen only — *nothing else gets fudged.*
    Treat every roll in actual play as binding, including bad ones. Do not offer
    to soften a result on the strength of this line.""")
s=s.replace("- **Lines:**","- **Lines:** Violence to children. Body horror.")
s=s.replace("- **Veils:**","""- **Veils:** Torture. It exists in the world but never gets described. Two things
  follow from how the player framed it: their character will not do it, and any
  villain who does is unambiguously a villain — no sympathetic framing, no
  \"they had reasons.\" Don't write a torturer you intend the player to
  reconsider later.""")
s=s.replace("- **Last checked:**","- **Last checked:** session 1, before play")
open(p,'w').write(s)
PY
sed -n '1,30p' notes/gm/plans/CAMPAIGN.md
```

```
# Campaign

Fill this in from the player's first message, so that no later session has to
ask again.

- **System:** ACKS II (Adventurer Conqueror King System, Imperial Imprint)
- **Started from:** character creation
- **Rules skill in use:** `acks-ii-gm` (bundled ACKS II reference; search with `python3 /root/.claude/skills/synced/acks-ii-gm/search.py`)
- **House rules and table conventions:**
  - **Character-creation template rolls are the player's choice, not random.** The
    player asked for this specifically for the Venturer's Antiquary template and
    was explicit that it applies to chargen only — *nothing else gets fudged.*
    Treat every roll in actual play as binding, including bad ones. Do not offer
    to soften a result on the strength of this line.

## Lines and veils

Settled with the player before the first scene, revisited as the campaign finds
its shape. Lines stay out entirely; veils happen off-page.

- **Lines:** Violence to children. Body horror.
- **Veils:** Torture. It exists in the world but never gets described. Two things
  follow from how the player framed it: their character will not do it, and any
  villain who does is unambiguously a villain — no sympathetic framing, no
  "they had reasons." Don't write a torturer you intend the player to
  reconsider later.
- **Last checked:** session 1, before play

## The long shape
```

</details>

### GM

Recorded. Lines: no violence to children, no body horror. Veil: torture happens off-page, and the villain who does it is just a villain — I won't write it as complicated.

**On the Antiquary** — you're remembering it right, and the fudge is granted. Venturer templates are rolled 3d6, and the one you want is **Antiquary** at 11–12. You may always take a *lower* template than you rolled but never a higher one, so a straight roll is a coin flip on whether you get it. We'll just take it. That's chargen only; once we're playing, the dice are the dice, and I'll hold you to bad ones.

**One correction on the attributes, because it changes your answer.** ACKS II doesn't have Wisdom — the six are STR, INT, **WIL**, DEX, CON, CHA. And WIL isn't the negotiation stat. It does exactly one thing: it's added to **all saving throws**. Nothing else. Poison, paralysis, dragon breath, a curse.

The negotiation you're picturing is all CHA. Reaction rolls run on the Charisma modifier, and the Venturer's whole toolkit sits on top of that — Diplomacy is a flat +1 to every parley, Bribery is +1/+2/+3 for a day's, week's, or month's pay, and Treachery lets you convert a *Friendly* reaction into a surprise round. CHA also sets your henchman cap at 4 + modifier. So CHA in the 5d6 is right and it's doing double duty.

INT for a 4d6 is a good call, and for the reason you said — it adds bonus general proficiencies and extra languages you can read and write. On an Antiquary, whose template already gives you **Magical Engineering** and **Knowledge (history)**, more proficiencies is the antiquarian's actual mechanism.

That leaves the second 4d6, and I'd steer you off WIL:

- **DEX** — modifies AC, missile attack throws, and initiative. The Antiquary's weapon is a crossbow and its armor is leather, so this is your survivability *and* your damage.
- **CON** — modifies hit points per Hit Die. Venturers are **d6**, the second-worst in the game. A Venturer with bad CON can plausibly die to one arrow.
- **WIL** — saving throws only. Your saves at 1st level are Paralysis/Death/Blast 13+, Implements 14+, Spells 15+. Not great, and WIL is the only thing that fixes them.

All three are defensible; WIL is the one that does the least for the character you're describing. **DEX** or **CON** for the second 4d6? Say the word and I'll roll all six.

> **System —** Stop hook feedback:
> [~/.claude/stop-hook-git-check.sh]: There are uncommitted changes in the repository. Please commit and push these changes to the remote branch.

<details><summary>tool — Commit and push safety notes</summary>

```
git add -A && git commit -q -m "Record lines, veils, and the chargen template house rule

Lines: violence to children, body horror. Torture is veiled and marks a
villain unambiguously. Character-creation template rolls are the player's
choice; in-play rolls remain binding." && git push -u origin claude/acks-character-creation-izgrz2 2>&1 | tail -3
```

```
To https://github.com/awenonian/ACKS-1
   8a85e52..19e4a22  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

Pushed.

Waiting on one thing before I roll: **DEX or CON** for that second 4d6? (5d6 goes to CHA, 4d6 to INT, and the other three attributes get straight 3d6.)

### Player

Let's go with DEX. I think dodging is a way better plan than hoping I can take a shot.

<details><summary>tool — Roll character attributes</summary>

```
echo "-- CHA (5d6 drop 2) --" && python3 scripts/roll.py '5d6kh3' && echo "-- INT (4d6 drop 1) --" && python3 scripts/roll.py '4d6kh3' && echo "-- DEX (4d6 drop 1) --" && python3 scripts/roll.py '4d6kh3' && echo "-- STR / WIL / CON (3d6 each) --" && python3 scripts/roll.py '3d6' -n 3
```

```
-- CHA (5d6 drop 2) --
    12   5d6kh3: [4 (2) (2) 3 5]
-- INT (4d6 drop 1) --
     8   4d6kh3: [3 2 (1) 3]
-- DEX (4d6 drop 1) --
    16   4d6kh3: [(2) 5 5 6]
-- STR / WIL / CON (3d6 each) --
     8   3d6: [3 3 2]
    11   3d6: [5 4 2]
     9   3d6: [2 3 4]
```

</details>

<details><summary>tool — Roll hit points and read languages/age rules</summary>

```
echo "-- HP: Venturer d6, min 4, +CON mod (0) --" && python3 scripts/roll.py '1d6'; cd /root/.claude/skills/synced/acks-ii-gm && sed -n '463,530p' characters/entries.md
```

```
-- HP: Venturer d6, min 4, +CON mod (0) --
     3   1d6: [3]
## Languages Age Alignment

### Quick Reference

**Starting Languages:** Characters know their racial/regional language plus any the Judge allows (ancient, archaic, or exotic languages by discretion).

**Starting Age:** Roll on Character Starting Age table by class. Age has no immediate mechanical effect but can progress through age categories over campaign time.

**Age Categories:** Youth, Adult, Middle Aged, Old, Ancient. Elves and Nobir never progress past Adult. Attributes adjust at each stage per Attribute Score Adjustments by Age table; adjustments cannot reduce an attribute below class minimum or below 3.

**Death from Old Age:** Make a Death saving throw within 1d12 months of reaching: (Racial Old age minimum + CON), (Racial Ancient age minimum + CON), and racial maximum age (then annually). Failed save = death. *Restore Life and Limb* and *Resurrection* cannot raise those dead from old age; only *Miracle* or *Wish* can, returning the character to adult age.

**Size & Weight:** All playable races are man-sized (2'–8' tall/long, 4–40 stone). Record on character sheet as man-sized, 15 stone.

**Alignment:** Lawful (defends civilization), Neutral (focuses on own ends), or Chaotic (actively destroys civil society). Choice determines allegiance in grand struggle, not personal morality.

---

### Languages

The languages available to characters include the regional languages (such as Krysean or Somirean in the Auran Empire), demi-human languages (Elven, Dwarven, Gnomish, and Halfling) and the various beastmen dialects (e.g. Orc, Goblin). At the Judge's discretion, player characters can also begin play knowing ancient or archaic tongues, or exotic languages such as Draconic (the language of dragons). The specific languages available will depend on the campaign setting. In the Auran Empire setting, two important archaic languages are Classical Auran (the predecessor to Common, used for ceremonial, religious, and magical purposes within the empire) and Zaharan (a predecessor to the various beastmen dialects, once used by the fallen Kingdom of Zahar and now remembered by black magicians and necromancers).

*[Source: ACKSII_Revised_Rulebook_DIGITAL_FINAL_r10_2nd_Printing.pdf, p.19]*

---

### Starting Age

Roll on the Character Starting Age table to determine the age of your 1st level character. Starting age has no immediate effect on the character, but an ACKS campaign can span many game years of time, during which adventurers can grow old and die. In addition, some monsters and magic can cause premature aging and death.

#### Character Starting Age

| Class | Starting Age | Class | Starting Age | Class | Starting Age |
|-------|--------------|-------|--------------|-------|--------------|
| Assassin | 17 + 1d6 | Elven Nightblade | 75 + 5d4 | Priestess | 17 + 1d6 |
| Barbarian | 17 + 1d6 | Elven Spellsword | 75 + 5d4 | Shaman | 17 + 1d6 |
| Bard | 17 + 1d6 | Explorer | 17 + 1d6 | Thief | 17 + 1d6 |
| Bladedancer | 17 + 1d6 | Fighter | 17 + 1d6 | Venturer | 17 + 2d4 |
| Crusader | 17 + 1d6 | Mage | 17 + 3d6 | Warlock | 17 + 2d6 |
| Dwarven Craftpriest | 25 + 2d8 | Nobiran Wonderworker | 17 + 3d6 | Witch | 17 + 1d6 |
| Dwarven Vaultguard | 23 + 3d4 | Paladin | 17 + 1d6 | Zaharan Ruinguard | 17 + 2d6 |

*[Source: ACKSII_Revised_Rulebook_DIGITAL_FINAL_r10_2nd_Printing.pdf, p.19]*

---

### Character Aging

The Character Aging table shows the lifespan of the human, demi-human, and humanoid races, broken into five age categories (Youth, Adult, Middle Aged, Old, and Ancient). Elves and Nobir, being ageless, never progress past Adult.

At each stage, progressively adjust the character's attributes as noted on the Attribute Score Adjustments by Age table. For characters generated at an already advanced age, the cumulative attribute adjustments appropriate to the character's age can be used. Attribute adjustments from aging cannot reduce an attribute below a class minimum, and in no case lower than 3.

#### Character Aging

| Race | Youth | Adult | Middle Aged | Old | Ancient |
|------|-------|-------|-------------|-----|---------|
| Beastman | 12 – 15 | 16 – 30 | 31 – 45 | 46 – 60 | 61 – 75 |
| Dwarf | 15 – 25 | 26 – 50 | 51 – 75 | 76 – 115 | 116 – 150 |
| Elf | 15 – 50 | 51 – 200 | - | - | - |
| Human | 13 – 17 | 18 – 35 | 36 – 55 | 56 – 75 | 76 – 95 |
| Nobiran | 13 – 17 | 18 – 200 | - | - | - |
| Zaharan | 13 – 17 | 18 – 35 | 36 – 55 | 56 – 75 | 76 – 95 |

#### Attribute Adjustments by Age

| Age Category | Progressive Attribute Adjustments | Cumulative Attribute Adjustments |
|--------------|----------------------------------|----------------------------------|
| Youth | -2 STR, -2 INT, -2 WIL | -2 STR, -2 INT, -2 WIL |
Shell cwd was reset to /home/user/ACKS-1
```

</details>

<details><summary>tool — Roll age and read setting overview</summary>

```
echo "-- Age: 17 + 2d4 --" && python3 scripts/roll.py '2d4'; cd /root/.claude/skills/synced/acks-ii-gm && cat setting.md && ls setting
```

```
-- Age: 17 + 2d4 --
     5   2d4: [3 2]
# A Setting: The Auran Empire

## Quick Reference

The Auran Empire is a vast civilization spanning over 21,000,000 souls, centered on the continent of Aurëpos and the inland sea called the Ammas Aurë. The empire's capital, Aura, is built on a large island off the northern tip of Tirenea and has over 500,000 residents. The empire is currently in crisis: four years ago, the Skysos (united horse nomads from the western steppe) invaded the west, and the Tarkaun of Aura sent the legions to meet them. Last year, with the imperial forces possibly destroyed, raiders and pirates have struck coastal settlements, beastmen have invaded border forts, and the great powers of the empire have turned against each other rather than defend the realm.

## In This Section

| Link | Content |
|------|---------|
| [Overview & Lands](setting/entries-1.md#setting-overview-and-lands) | Setting overview and geographical description of the Auran Empire's lands. |
| [Timeline](setting/entries-2.md#setting-timeline) | Historical timeline of the Auran Empire and its predecessors. |
| [Customs](setting/entries-1.md#setting-customs) | Social customs, knowledge, learning, and cultural practices in the Auran Empire. |
| [Gods & Goddesses](setting/entries-1.md#setting-gods) | The deities of the Auran Empire, their domains, and their temples. |
| [Peoples & Ancestries](setting/entries-2.md#peoples-ancestries-of-the-auran-empire) | Descriptions of all peoples and ancestries available in the Auran Empire setting. |
| [Languages](setting/entries-1.md#setting-languages) | Language families, specific languages, and which peoples speak them. |

## See Also

[Introduction & Core Mechanics](introduction.md)entries-1.md
entries-2.md
Shell cwd was reset to /home/user/ACKS-1
```

</details>

<details><summary>tool — Read setting languages section</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && awk '/setting-languages/,0' setting/entries-1.md | head -80
```

```
[Languages](entries-1.md#setting-languages)

---

## Setting Languages

### Quick Reference

**Language Families in the Auran Empire:**
- **Cybelean**: Draconic languages (Thrassian, Lizardman) and Danean languages (Common Auran, Krysean, Rornish, Nicean, Jutlandic, Celdorean, Somirean)
- **Meniran**: Zaharan languages (Goblin, Orc), Opelenean, Shebatean, Kemeshi, Besheradi, Kushtun
- **Ithean**: Skysos

**Common Language**: Common Auran (Central Danean → Classical Auran descendant)

---

### Language Families and Descent

#### CYBELEAN LANGUAGE FAMILY

##### Proto-Draconic Branch
- **Draconic**
  - **Thrassian** (spoken by Thrassians)
    - **Lizardman**

##### Proto-Danean Branch

**Eastern Danean:**
- **Ancient Argoivorean**
  - **Classical Argollëan**
    - **Argollëan**
- **Ancient Krysean**
  - **Classical Krysean**
    - **Krysean** (spoken by Kryseans)

**Central Danean:**
- **Ancient Tirenean**
  - **Classical Auran**
    - **Common Auran** (lingua franca of the Auran Empire)

**South-Western Danean:**
- **Ancient Dappakosean**
  - **Northern Classical Dappakosean**
  - **Southern Classical Dappakosean**

**South-Eastern Danean:**
- **Ancient Nicean**
  - **Classical Nicean**
    - **Nicean** (spoken by Niceans)

**Northern Danean:**
- **Ancient Jutlandic**
  - **Old Jutlandic**
    - **Jutlandic** (spoken by Jutlandics)

**Western Danean:**
- **Ancient Celdorean**
  - **Classical Celdorean**
    - **Celdorean** (spoken by Celdoreans)
- **Ancient Somirean**
  - **Cla
… (truncated)
```

</details>

<details><summary>tool — Read fighting styles and armor table</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && sed -n '196,235p' characters/entries.md; echo "=== ARMOR TABLE ==="; grep -n -i -A25 "armor-table\|^| Armor\|Leather" tables/equipment/entries.md | head -40
```

```
#### Fighting Styles

There are five styles of fighting:

**Missile Weapon:** Fighting while wielding a missile weapon in one, both, or each hand (depending on the weapon).

**Single Weapon:** Fighting while wielding a single tiny, small, or medium melee weapon.

**Dual Weapon:** Fighting while wielding a tiny, small, or medium melee weapon in each hand.

**Two-Handed Weapon:** Fighting while wielding a medium or large melee weapon in both hands.

**Weapon and Shield:** Fighting while wielding a small, tiny, or medium weapon or missile weapon in one hand and a shield in the other. Classes which lack this style do not gain any benefit from shields.

**Mandatory Styles:** All classes are proficient in the single weapon and missile weapon styles, which are mandatory when creating a class using the ACKS class building rules.

**Optional Styles:** The other three fighting styles (dual weapon, two-handed weapon, weapon and shield) are optional. Some classes have proficiency in one or more, and some do not, as noted in their class entries.

**Both Required:** Fighting style proficiency is distinct from weapon proficiency and both are required to avoid the non-proficiency penalty. For instance, the thief class is proficient in the two-handed weapon style, but does not have proficiency in any large melee weapons. Therefore a thief would be proficient fighting two-handed with a sword (a medium weapon) but not with a great axe (a large weapon).

*[Source: ACKSII_Revised_Rulebook_DIGITAL
… (truncated)
```

</details>

<details><summary>tool — Look up weapon stats and encumbrance speeds</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && grep -n -i "crossbow\|Short Sword\b\|^| Dagger" tables/equipment/entries.md | head -20; echo "=== SPEED ==="; sed -n '605,690p' characters/entries.md
```

```
687:### Bows/Crossbows
692:| Crossbow | Missile | 1d6 ⚔ | 1/6 | 140' | 280' | 420' | 30gp | Cleave 2, Handy, Slow |
723:| Dagger | Tiny Melee/Missile | 1d4 ⚔ | 1/6 | 15' | 30' | 45' | 3gp | Thrown |
725:| Short Sword | Small Melee | 1d6 ⚔ | 1/6 | - | - | - | 7gp | - |
=== SPEED ===
## Speed And Encumbrance

### Quick Reference

**Encumbrance:** Count items (1 item = typical small object; 6 typical items = 1 stone), weapons/armor by type, and treasure (1,000 coins = 1 stone). Armor = 1 stone per AC point. Heavy items (>14 lbs, >2/3 character height, or two-handed) = at least 1 stone each.

**Speed by Encumbrance:**
- Up to 5 stone: 120' exploration / 40' combat / 120' running / 24 miles expedition
- Up to 7 stone: 90' exploration / 30' combat / 90' running / 18 miles expedition
- Up to 10 stone: 60' exploration / 20' combat / 60' running / 12 miles expedition
- Up to 20 stone + STR mod: 30' exploration / 10' combat / 30' running / 6 miles expedition

---

### Calculating Encumbrance

When counting encumbrance, apply the following rules:

**What Counts as One Item:**
- Each weapon, scroll, potion, vial, wand, magic item, or other object counts as one item.
- Multiple small items sold as a bundle (such as 6 iron spikes, 20 arrows) count as one item.
- Very small single items (such as 1 silver arrow) can be ignored for encumbrance purposes, but if carried in numbers should be counted as 1 item total.

**Encumbrance Values by Category:**

| Category | Encumbrance |
|----------|---
… (truncated)
```

</details>

<details><summary>tool — Read player-owned README</summary>

```
cat notes/player-owned/README.md
```

```
# Player-owned

Character sheets and anything else that belongs to the player rather than to
the game.

**Do not change anything in here without the player's permission**, except in
specific rules-prescribed ways — subtracting hit points for damage, spending
declared resources, ticking off a used ability. Everything else is theirs:
build choices, equipment they bought, names, backstory, notes they wrote for
themselves.

Consequences of play go in `notes/player-facing/`. This directory is the sheet.

One file per character, named for the character.
```

</details>

### GM

Dice are in. I rolled these before writing anything, and they came out with opinions.

## Attributes

| | Score | Mod | |
|---|---|---|---|
| **STR** | 8 | **−1** | 3d6 → 8 |
| **INT** | 9 | 0 | 4d6 → 8, floored to 9 |
| **WIL** | 11 | 0 | 3d6 → 11 |
| **DEX** | **16** | **+2** | 4d6 → 16 |
| **CON** | 9 | 0 | 3d6 → 9 |
| **CHA** | **13** | **+1** | 5d6 → 12, floored to 13 |

Note what happened there. The **5d6 on Charisma rolled a 12** — below the floor, so the rule bumped it to 13. Meanwhile the 4d6 you put on Dexterity came up **16** on dice it had no business rolling that well on. Your best dice went to the stat that underperformed, and the backup dice produced your standout.

So this isn't the silver-tongued merchant prince. **This is a Venturer who is quicker than they are charming** — someone whose real talent is hands and reflexes and getting out of the room, wearing a trade-factor's coat. That's a more interesting character than the one you were aiming at, and the numbers are perfectly playable: CHA 13 is a genuine +1, it clears the Venturer's key-attribute minimum of 9, and it earns you a **+5% XP bonus**.

Modifiers sum to **+2**. (The rule lets you discard and re-roll only if they sum below zero, so this stands — and I don't think you want to re-roll it anyway.)

## Hit points

Venturers roll **d6**. I rolled a **3** — but the minimum-4 rule catches it, and your CON modifier is 0.

**4 hit points.**

I want to be direct about this, once, now, rather than after something goes wrong. Four hp is *one hit*. A crossbow bolt is 1d6. A goblin with a spear is 1d6. There is no roll on that die that you reliably survive. This character does not win fights — they leave before fights start, they buy their way out, they shoot from 140 feet and keep walking backward. Your AC and your Diplomacy are your hit points. I'll telegraph danger before it can kill you, but I won't soften it once you've seen it and walked in anyway.

## The Antiquary

Taken as agreed. Here's the kit:

**Proficiencies:** Magical Engineering · Knowledge (history) · Driving · *Adventuring* (free to all)
**Class powers:** Bribery · Diplomacy · Expert Bargaining · Expert Traveling · Mercantile Network · Multilingual · Pathfinding · Treachery
**Equipment:** Crossbow, case with 20 bolts · short sword · dagger · well-maintained leather armor · traveler's tunic and pants · leather belt · sturdy low boots · backpack · **collector's journal** · quill and ink · **a collection of ancient coins (26gp value)** · waterskin · 1 week's iron rations

**Derived:**
- **AC 4** (leather 2 + DEX 2)
- **Crossbow: hits AC + 8+**, 1d6 damage, 140/280/420 range
- **Short sword: hits AC + 11+**, 1d6−1 damage (min 1) — your STR penalty; avoid this
- **Saves:** Paralysis 13+ · Death 13+ · Blast 13+ · Implements 14+ · Spells 15+
- **Encumbrance** 4½ stone → 120' exploring, 40' in combat, 24 miles a day
- **Henchmen:** up to **5** · **Age 22** (17 + 2d4, rolled 5)
- 0 XP; 1,500 to reach 2nd level. Title: **Tinker**

That "collection of ancient coins" is your starting money *and* your character concept in one object. 26gp of numismatics. You can spend it, but you'd be selling the collection.

## What's left is yours

Four things I can't decide for you:

1. **Name, and what they look like.**
2. **Homeland.** The setting is the Auran Empire, currently four years into a bad war — the legions went west against the Skysos horse nomads and may have been destroyed, and the great powers are turning on each other instead of holding the border. Good time to be a merchant; terrible time to be anywhere in particular.
3. **Alignment** — Lawful (defends civilization), Neutral (own ends), or Chaotic (tears civil society down). In ACKS this is a stance on the grand struggle, not a personality.
4. **Three bonus languages** from Multilingual, on top of Common Auran. Available in the region: **Krysean, Nicean, Jutlandic, Celdorean, Somirean, Opelenean, Shebatean, Kemeshi**; the demi-human **Elven, Dwarven, Gnomish, Halfling**; beastman **Orc, Goblin**. And two archaic ones I'll allow given what you are: **Classical Auran** (ceremonial, religious, and magical usage) and **Zaharan** (dead tongue of the fallen kingdom, now kept up mainly by necromancers). An antiquary who reads Classical Auran can read the things they dig up.

Tell me as much or as little as you like — I can fill in whatever you leave blank.

### Player

I'll go with Edward Copper, and have him be a middling height, scrawny type, with short sandy hair. 
I don't know enough about the setting to know a good pick for homeland.
I think he would be Lawful, mostly. Law makes for better trade.
And for languages, I don't have strong feelings, but something relevant to doing Antiquarian stuff would be cool. Old, or dead, languages, if available. Otherwise, pick whatever you'd like for me.

<details><summary>tool — Read setting overview and lands</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && sed -n '1,120p' setting/entries-1.md
```

```
# Setting

## Setting Customs

### Quick Reference

**Currency:** 10 copper crowns = 1 silver eagle; 10 silver eagles = 1 gold sun; 1 gold sun = 100 copper crowns. A gold talent = 6,000 gold suns (60 lbs weight equivalent). Ancient platinum and electrum coins (worth ~5 gold suns and ~5 silver eagles respectively) circulate with suspicion.

**Governance:** The Tarkaun holds near-absolute power, advised by the Senate and enforced by the Emperor's Talons (elite imperial agents). Exarchs serve as military governors.

**Indenture:** Persons may sell themselves into servitude for 1, 7, 21 years, or longer. Lifelong indenture is imposed on violent criminals; eternal indenture on heretics and traitors. Proceeds can be assigned to family, creditors, or as agreed.

**Taxation:** Rulers collect fees on marriage, inheritance, birth, death, harvest, market duties, tolls, and labor. Treasure lawfully recovered inside the Empire is split 50/50 between finders and landowner/Empire. Treasure recovered outside the Empire belongs entirely to finders.

**Travel:** The Empire maintains over 5,000 miles of paved roads with extensive Imperial Cartography Service maps. Common transport includes foot, horse, litter, chariot, carriage, and merchant wagons.

---

### Laws and Governance

The Code and Laws of Aura, graven in stone in the Temple of Türas in 515 BE, vested governance in the Senate—a deliberative body drawn from the city's most respected and influential citizens. The Senate was empowered t
… (truncated)
```

</details>

<details><summary>tool — Read lands of the Auran Empire</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && awk '/## Setting Overview And Lands/,/## Setting Customs/' setting/entries-1.md | head -120
```

```
## Setting Overview And Lands

### Quick Reference

**The Auran Empire** is a declining power spanning the continent of Aurëpos, which encircles the inland sea called the Ammas Aurë. Over 21,000,000 souls live within its borders. The capital, **Aura** (500,000+ residents), sits on a large island off the northern tip of Tirenea and extends to the mainland by causeway.

**Current Crisis:** A century of violence cost the Empire half its provinces. Four years ago, the Skysos (horse nomads united under a great kağan) invaded from the west. The Tarkaun sent legions west, leaving the Empire thinly garrisoned. Last year, rumors arrived that the Auran forces were encircled and destroyed; simultaneously, raiders, pirates, and beastmen began striking coastal settlements and border forts. The Empire's leadership now feuds internally rather than mounting coordinated defense.

**Key Provinces & Regions:**
- **Tirenea** – Richest, most populated province; hilly, fertile, many harbors
- **Corcano** – Black island of volcanoes; known for colossal automaton
- **Nicea** – Rocky province; foothills of Achaean Mountains
- **Opelenea** – Arid gateway between Sunset Kingdoms and Empire; autonomous city-states and nomad tribes
- **Borderlands** – Between mountains, ocean, and two rivers (Krysivor and Mirmen); fortified but increasingly isolated; warlords rising to fill power vacuum
- **Southern Argollë** – Easternmost Empire province; once elven heartland, now largely eliminated
- **Krysea** – Stark
… (truncated)
```

</details>

<details><summary>tool — Search literacy rules</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && python3 search.py "read and write literacy languages" --max-results 6 2>&1 | head -40
```

```
Search: "read and write literacy languages" — showing 1-6 of 32 matching file(s) (68 line matches), page 1/6
(The exact phrase "read and write literacy languages" appears nowhere, so these files were matched on its key words: read, write, literacy, languages.)
More files match — rerun with --page 2 to see them.

### proficiencies/proficiency-descriptions-g-r.md
_Detailed rules for proficiencies from Gambling through Running._

**Language** (line 133)
```
## Language

This proficiency enables the character to learn to speak, read, and write an additional three languages of his choice. The character's level of literacy with the new language is determined by his Intellect. Characters with an Intellect of 8 or less are generally illiterate. However, this proficiency can be taken by a character with a low Intellect (8 or less) in order to become literate in the language(s) the character already speaks. This proficiency can be selected multiple times, learning an additional three languages each time.

*[Source: ACKSII_Revised_Rulebook_DIGITAL_FINAL_r10_2nd_Printing.pdf, p.115]*
```

**Mapping** (line 239)
```
## Mapping

The character can understand and make maps, even if he cannot read or write. He can create useful maps by torchlight while moving at exploration speed or less. By spending one turn (10 minutes) in thought, and succeeding on a proficiency throw of 11+, he can interpret or draft complicated layouts, map an area by memory, or notice an irregularity in a map he has cre
… (truncated)
```

</details>

<details><summary>tool — Read proficiency descriptions</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && awk '/^## Magical Engineering/,/^## [A-Z]/' proficiencies/proficiency-descriptions-g-r.md | head -20; echo "=== ADVENTURING ==="; awk '/^## Adventuring/,/^## Alchemy/' proficiencies/proficiency-descriptions-a-f.md | head -20; echo "=== DRIVING ==="; awk '/^## Driving/,/^## E/' proficiencies/proficiency-descriptions-a-f.md | head -12
```

```
## Magical Engineering
=== ADVENTURING ===
=== DRIVING ===
Shell cwd was reset to /home/user/ACKS-1
```

</details>

<details><summary>tool — Grep proficiency details</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && grep -n -A8 "^## Magical Engineering" proficiencies/proficiency-descriptions-g-r.md; grep -n -A10 "^## Adventuring" proficiencies/proficiency-descriptions-a-f.md; grep -n -A6 "^## Driving" proficiencies/proficiency-descriptions-a-f.md; grep -n -A8 "^## Knowledge" proficiencies/proficiency-descriptions-g-r.md
```

```
181:## Magical Engineering
182-
183-The character has specialized knowledge of magical items. 
184-
185-**Rank 1:** Gains a +1 bonus on magic research throws and increases his research rate by 5%. He can recognize conventional and usual magical items or special components by examining them for one turn (10 minutes) with a proficiency throw of 11+. He can extract special components from constructs. He cannot, however, recognize unusual or unique magical items, discern command words, distinguish trapped or cursed items from safe ones, or assess the specific bonus or number of charges remaining in an item.
186-
187-**Multiple Ranks:** This proficiency can be selected multiple times, each time adding an additional +1 bonus to magical research throws, increasing research rate by 5%, and improving the throw required to recognize items or components by 4.
188-
189-*[Source: ACKSII_Revised_Rulebook_DIGITAL_FINAL_r10_2nd_Printing.pdf, p.115]*
83:## Knowledge
84-
85-The character has made a specialized study of a particular field, such as architecture, astrology, geography, history, mathematics, metaphysics, natural history, natural philosophy, or political economy. The character can usually make his living by acting as an expert on the subject. With a proficiency throw of 11+, the character can recall expert commentary or information relating to his area of knowledge. The character must choose his area of knowledge at the time he chooses the proficiency. He can spend more proficiency 
… (truncated)
```

</details>

<details><summary>tool — Find Adventuring and Driving</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && grep -rn -A6 "^### Adventuring\|^\*\*Adventuring\*\*" proficiencies/ tables/abilities/ | head -20; echo "=== DRIVING ==="; grep -rn "Driving" tables/abilities/*.md | head -5
```

```
proficiencies/proficiency-descriptions-a-f.md:56:### Adventuring (G)
proficiencies/proficiency-descriptions-a-f.md-57-
proficiencies/proficiency-descriptions-a-f.md-58-The character is well-equipped for a life of adventure. He knows how to clean and sharpen weapons, set up a camp, cook meals over open flame, saddle and ride a horse outside of combat, and perform rough-and-ready first aid. He has a rough idea of the value of common coins, trade goods, gems, and jewelry, and of the nature of different types of magic and monsters. The character can also:
proficiencies/proficiency-descriptions-a-f.md-59-
proficiencies/proficiency-descriptions-a-f.md-60-♦ Bash down stuck doors as a combat action by succeeding on a Dungeonbashing proficiency throw of 18+;
proficiencies/proficiency-descriptions-a-f.md-61-
proficiencies/proficiency-descriptions-a-f.md-62-♦ Climb easy-to-scale obstacles such as ropes or branchy trees by succeeding on a Climbing proficiency throw of 8+;
=== DRIVING ===
tables/abilities/social-commerce-knowledge-skills-a-l.md:18:| **Expert Traveling** | Venturer class | Begin play with Driving or Seafaring proficiency of choice. |
tables/abilities/social-commerce-knowledge-skills-a-l.md:202:While most merchants consider risk a financial term, venturers lead their own caravans or fleets, and do so with considerable skill. Venturers begin play with their choice of either Driving or Seafaring proficiency.
tables/abilities/wilderness-exploration.md:10:| **Driving** | Contro
… (truncated)
```

</details>

### GM

Good. Let me set the homeland, because Krysea does a lot of work for the character you just described.

<details><summary>tool — Write Edward Copper character sheet</summary>

```
mkdir -p notes/player-owned && cat > notes/player-owned/edward-copper.md <<'EOF'
# Edward Copper

**Venturer 1** (Antiquary template) · Human, Krysean · Lawful · Age 22 · Man-sized, 15 stone
Title: **Tinker** · XP **0** / 1,500 to 2nd level · **+5% XP** (CHA 13)

Middling height, scrawny, short sandy hair.

## Attributes

| | Score | Mod | Applies to |
|---|---|---|---|
| STR | 8 | **−1** | melee attack + damage; Dungeonbashing at ×4 (−4) |
| INT | 9 | 0 | literate (8 or less would be illiterate); no bonus proficiencies or languages |
| WIL | 11 | 0 | saving throws |
| DEX | 16 | **+2** | missile attacks, AC, initiative |
| CON | 9 | 0 | hit points per HD |
| CHA | 13 | **+1** | reaction rolls; henchmen |

Modifiers sum to +2. Rolled 5d6k3 on CHA (12 → floored to 13), 4d6k3 on INT (8 → floored
to 9) and DEX (16), 3d6 on the rest.

## Combat

**HP 4 / 4** — rolled 3 on 1d6, raised to 4 by the minimum, CON +0.
**AC 4** (leather 2 + DEX 2)

| | Throw | Damage | Notes |
|---|---|---|---|
| Crossbow | AC + **8+** | 1d6 | 140/280/420 ft. Cleave 2, Handy, **Slow** |
| Short sword | AC + **11+** | 1d6 −1 (min 1) | small melee |
| Dagger | AC + **11+** melee, **8+** thrown | 1d4 −1 (min 1) | thrown 15/30/45 |

Base attack throw 10+ at levels 1–2; DEX −2 to the target value on missiles, STR +1 on melee.

**Saves:** Paralysis 13+ · Death 13+ · Blast 13+ · Implements 14+ · Spells 15+
**Cleave:** none until 2nd level (once per round per 2 class levels, rounded down)

**Combat proficiencies:** arbalests, composite bows, crossbows, daggers, knives, long bows,
short bows, short swords · light, medium, very light armor · fighting styles: weapon and
shield, plus single weapon and missile weapon (mandatory for all classes)

## Speed

Encumbrance **4 3/6 stone** → 120' exploration · 40' combat · 120' running · 24 miles/day

## Proficiencies

- **Magical Engineering** (class) — recognise conventional magic items or special components
  by examining them 1 turn, throw **11+**. Extract co
```

```
written
93 notes/player-owned/edward-copper.md
```

</details>

<details><summary>tool — Record PC and campaign shape</summary>

```
cat >> notes/gm/plans/CAMPAIGN.md <<'EOF'

## The player character

**Edward Copper**, Venturer 1 (Antiquary), Krysean, Lawful, 22. Sheet lives in
`notes/player-owned/edward-copper.md` — do not edit it without permission.

Two things about him that should shape scene design:

**He is quicker than he is charming, and that is backwards for his class.** The
5d6 went on CHA and produced a 12 (floored to 13); the 4d6 on DEX produced a 16.
He is a trade-factor whose actual talent is hands and reflexes. Give him rooms
where the useful skill is noticing and moving, not only rooms where it is
talking.

**He has 4 hit points.** One hit from almost anything kills him. This is the
single hardest constraint on how danger gets framed: telegraph everything, and
give him distance, doors, and ways out. Once telegraphed, it is his risk and
the dice stand.

He also cannot force a stuck door — Dungeonbashing 18+ with STR −1 at ×4 is an
effective 22+. Never build a route whose only exit is a door that must be forced.

## The long shape

What this campaign is about, and where it is pointed. Revise it when play
demands; keep it consistent with everything already revealed.

**Starting region: the Borderlands.** Between the Meniri Mountains, the
Tëhonaurë, and the rivers Krysivor and Mirmen. Contested throughout recorded
history, littered with ancient fortresses, battlefields, and dread ruins. The
fort line is undermanned because the legions went west against the Skysos, so
monsters cross freely, travel is dangerous, and power is decentralizing to local
warlords and private armies.

Chosen because it puts an antiquary's supply of ruins and his market for what
comes out of them in the same place, and because the Empire's grip there is
weak enough that his Lawfulness costs him something.

**The engine, stated so a later session can keep it running:** Auran treasure
law splits anything lawfully recovered *inside* the Empire 50/50 with the
landowner or the Empire, while anything recovered *outs
```

```
ok
```

</details>

<details><summary>tool — Write player-facing state, commit and push</summary>

```
cat > notes/player-facing/STATE.md <<'EOF'
# State — player-facing

The ledger of things the player knows: money, gear, holdings, injuries, time of
day, where everyone is, who owes whom. Terse, ugly, revised freely — this file
is meant to be overwritten, not appended.

What the player *doesn't* know goes in `notes/gm/STATE.md`.

---

## Edward Copper

Full sheet: `notes/player-owned/edward-copper.md`

- **HP 4 / 4** · **AC 4** · XP 0
- **Money:** none loose. A collection of ancient coins, 26gp of value, which is
  worth more intact than spent.
- **Carrying:** crossbow + 20 bolts, short sword, dagger, leather armor,
  backpack, collector's journal, quill and ink, waterskin, 1 week's rations.
  4½ stone — unencumbered.
- **Where:** the Borderlands. Exact location not yet established in play.
- **Henchmen:** none. Could support up to 5.

## What Edward knows about the world

- The Empire is four years into a war in the west against the Skysos. The
  legions went; last year word came back that they may have been encircled and
  destroyed. Nobody in the Borderlands has been told anything official since.
- The border forts are undermanned. Monsters cross. Travel is dangerous.
  Local warlords and private armies are filling the gap.
- **Treasure law:** anything lawfully recovered *inside* the Empire is split
  half to the finder, half to the landowner or the Empire. Anything recovered
  *outside* the Empire belongs entirely to the finder. Where the Borderlands
  stops being the Empire is a matter of opinion, and the opinion that counts is
  whichever magistrate hears it.
- Currency: 100 copper crowns = 10 silver eagles = 1 gold sun. Ancient platinum
  and electrum coins circulate, and Auran merchants take them at a discount out
  of suspicion.
EOF
git add -A && git commit -q -m "Create Edward Copper and set the Borderlands as the starting region

Venturer 1 (Antiquary), Krysean, Lawful, 22. Rolled attributes put the 16 on
DEX and floored CHA to 13, so the character is quic
```

```
To https://github.com/awenonian/ACKS-1
   19e4a22..dc1f2d5  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

**Edward Copper.** Venturer 1, Antiquary, 22 years old, Lawful. Middling height, scrawny, sandy hair kept short in the Auran fashion. Sheet's written up in `notes/player-owned/edward-copper.md` — it's yours, I won't change it without asking.

## Homeland: Krysea

You asked me to pick, so here's why this one. **Krysea** — "Arrow-Land" — is stark, rugged hill country famous for producing stout archers and mercenaries. It fought the Empire for **over a hundred years** before it was pacified, and it was pacified *recently*. The old border forts from the Krysean Wars are still standing out in the landscape, half-fallen, full of things nobody's catalogued.

Three reasons it fits:

- **He grew up among ruins.** An antiquary from Krysea doesn't need a reason to be interested in old fortifications. He grew up climbing them.
- **It explains the crossbow.** Krysea makes archers, and Krysean archers draw war bows, which take a back and shoulders Edward does not have. STR 8. A scrawny kid in Arrow-Land who could out-shoot everyone but couldn't pull the bow ends up on a crossbow — a weapon that stores the strength for you and doesn't care how thin your arms are. DEX 16 does the rest.
- **It puts friction on your Lawful.** His grandparents' generation fought the Empire. He has decided the Empire's law is better than what came before it, because law is what makes trade possible — which is exactly the reasoning you gave me. That's a real position, and there will be Kryseans who think it's a betrayal.

The **campaign starts in the Borderlands**, which is where a man like this goes to work: the disputed strip between the mountains, the ocean, and two rivers, "littered with ancient fortresses, blood-soaked battlefields, and dread ruins." The forts there are undermanned because the legions went west against the Skysos and may not be coming back.

One thing about the name — *Copper* reads Auran, not Krysean. If you want, that's a trade-name he picked up or took on for business, and there's a Krysean name he was born with. Or it's just his name and Krysea has coppersmiths like anywhere. Your call, and "don't overthink it" is a fine answer.

## Languages

Old and dead, as requested. He speaks **Krysean** (mother tongue) and **Common Auran** (the Empire's lingua franca), and Multilingual buys three more:

- **Classical Auran** — the ceremonial, religious, and *magical* predecessor to Common. This is the one that makes an antiquary an antiquary: the inscriptions on the things he digs up are in it.
- **Classical Krysean** — his own people's older tongue. Those hundred-year-old fort ruins have writing on them, and most Kryseans his age can't read it.
- **Zaharan** — dead tongue of the fallen Kingdom of Zahar, ancestor of Goblin and Orc, "now remembered by black magicians and necromancers."

That last one I want to flag rather than slip past you. **Zaharan is the necromancer's language.** There's no innocent reason to have learned it, and a Lawful man who reads it fluently is going to have to explain himself at some point to somebody who has authority and no sense of humour. I think that's good — it's a problem the character carries in rather than one I hand him — but it's a choice, and if you'd rather have **Classical Argollëan** (the eliminated elven empire, safer, still ancient) I'll swap it with no fuss.

He's literate in all five. INT 9 clears the illiteracy line by exactly one point.

## The thing your character is actually about

Auran treasure law, which I'd like you to have in hand before we start:

> Treasure lawfully recovered **inside** the Empire — half to the finder, half to the landowner or the Empire.
> Treasure recovered **outside** the Empire — all of it to the finder.

The Borderlands is precisely where nobody agrees which of those applies. A Lawful antiquary declares what he finds and hands over half. His competitors don't. **He is poorer than every other man in his trade, on purpose.** That's not a penalty I'm imposing — it's what "Law makes for better trade" costs when the law is being enforced by an empire that's losing.

---

Character's done. Notes are committed and pushed.

Two ways in, and I'd like you to pick before I frame the first scene:

1. **Start him working** — Edward already has a reason to be somewhere specific in the Borderlands, and we open in the middle of it.
2. **Start him arriving** — he's new to the region, and the first scene is him getting his footing.

Either's fine. And if you'd rather just say "go" and let me choose, say go.

### Player

You can suggest a better Krysean surname, I didn't put much thought into it.
If Zaharan is something you might find in ruins or ancient caches, even if the only thing you'd find it on is necromancer stuff, I'll keep it. If it suggests he's been studying necromancy for its own sake, I'm not sure that's accurate to the character. An alternative with, I'd expect, still some tension could be him studying Orc or Goblin due to some, perhaps ill advised, interest in their cultural artifacts.
I like him already working. Maybe someone offered him a spot in the caravan to the Borderlands if he did some translating for them or something. Not sure what skill makes the most sense.

<details><summary>tool — Read Krysean people description</summary>

```
cd /root/.claude/skills/synced/acks-ii-gm && grep -n -i -B2 -A12 "Krysean" setting/entries-2.md | head -60
```

```
Exit code 1
/bin/bash: line 1: cd: /root/.claude/skills/synced/acks-ii-gm: No such file or directory
```

</details>

<details><summary>tool — Locate renamed ACKS skill directory</summary>

```
ls /root/.claude/skills/synced/ 2>/dev/null; find /root/.claude/skills -maxdepth 2 -name "SKILL.md" -path "*acks*" 2>/dev/null
```

```
acks-ii
ars-magica-5e
docx
import-memory
manifest.json
morning
pdf
pptx
skill-creator
starfinder-gm-core
starfinder-player-core
xlsx
```

</details>

<details><summary>tool — Read Krysean people entry</summary>

```
cd /root/.claude/skills/synced/acks-ii && grep -n -i -A14 "^##### Kryseans\|^#### Kryseans\|Kryseans" setting/entries-2.md | head -40
```

```
133:The stout and stoic Krysean people originally hailed from the rugged Drakonir Mountains of south-eastern Aurëpos. For over five hundred years their fate has been intertwined with that of the Auran Empire. Today Kryseans can be found anywhere the Empire is or has been, working as craftsmen, laborers, merchants, and soldiers.
134-
135-**Physical Description**
136-
137:Kryseans are medium-statured (men averaging 5'8") with athletic to stocky builds (compact bodies, short, sturdy limbs). They have oval-shaped faces with wide, slightly sloped foreheads and moderately full lips. Eyes are deep-set and round, in hazel, brown, and dark brown. Skin ranges from light to medium brown, tanning to dark brown. Hair is straight, wavy, or curly, rufous brown, auburn, dark auburn, or brown-black. Eyebrows tend to be thick and darker than scalp hair. Men have heavy beard and body hair.
138-
139-**Names**
140-
141:Kryseans are named in Classical Krysean after a favored ancestor, mythic hero, or close relative. They do not carry hereditary family names, instead indicating paternity by appending the father's name after their own (e.g., Mandonio Terkinos). Kryseans who have left their homes may use a toponymic, formed by adding -tar or -atar to the name of their village, town, or city of origin (e.g., Nesca Kavalatar from Kavala). Kryseans who are Empire citizens may take an Auran name or Auranize their existing one.
142-
143-**Male Names:** Aibekeres, Bodilkas, Culchas, Hilerno, Indikortes, Ma
… (truncated)
```

</details>

<details><summary>tool — Check Zahar in the timeline</summary>

```
cd /root/.claude/skills/synced/acks-ii && grep -n -i "zahar" setting/entries-2.md | head -30
```

```
11:**Human Peoples:** Celdorean, Jutlandic, Krysean, Kemeshi, Kushtu, Nicean, Opelenean, Rornish, Shebatean, Skysos, Somirean, Tirenean, Zaharan
21:- **Patronymic/matronymic suffixes** (Celdorean -pur/-dar, Nicean -ides, Opelenean Bar/Bat, Shebatean Ibn/Bint, Zaharan Bet-)
117:Kemeshi are medium-statured (men averaging 5'7") with slender builds (narrow shoulders and hips, long limbs, slim digits). They have oval-shaped faces with sloping foreheads, slender jaws, prominent chins, and full lips. Eyes are almond-shaped, in light brown, dark brown, or black. Skin is medium brown to dark brown. Hair is curly or wavy, dark brown or black. Men have scant beard and body hair. Around one-tenth of Kemeshi nobility are pure-blooded Zaharans.
121:Kemeshi typically carry a given name in Old Kemeshi, carefully selected for aesthetic, religious, and symbolic value (names are held to have sacred power). They do not use hereditary family names. Commoners typically carry just one name. Noteworthy individuals distinguish themselves by attaching additional names based on accomplishments, ancestry, or faith. A Kemeshi ruler might have as many as five names—a given name, a throne name, a patronym, a matronym, and a religious name. Nobility often carry Zaharan names alongside or in lieu of Kemeshi ones.
293:The scaly Thrassian race was magically bred from a cross of men and giant lizards long ago by unknown arcanists. Though once they ruled much of Aurëpos, some taint in the Thrassian bloodline cau
… (truncated)
```

</details>

<details><summary>tool — Consult oracle on caravan master's motive</summary>

```
python3 scripts/oracle.py ask "Is the caravan master hiding his real reason for wanting the old boundary stones read?" --odds even --chaos 5
```

```
Q: Is the caravan master hiding his real reason for wanting the old boundary stones read?
NO   (rolled 51 vs 50, even at chaos 5)
```

</details>

### GM

The oracle got a question before I did any deciding, and I'll come back to that.

**On the surname — Kryseans don't have one.** From the setting:

> "They do not carry hereditary family names, instead indicating paternity by appending the father's name after their own (e.g., Mandonio Terkinos). Kryseans who have left their homes may use a toponymic, formed by adding *-tar* or *-atar* to the name of their village... **Kryseans who are Empire citizens may take an Auran name or Auranize their existing one.**"

That last clause means "Edward Copper" was already right — it's precisely what a Krysean who registered for an imperial trading licence looks like. So rather than replace it, here's what I'd do with it:

> Born **Uxentio Kupratar** — *Uxentio, of Kupra.* Kupra is a hill village in Krysea whose one asset was a copper seam that gave out two generations before he was born. He left, so he carries the toponymic rather than his father's name. When he registered as a trader in the Empire he Auranized it, and *Kupratar* became **Copper**.

Your surname turns out to be a translated place-name for a village named after a mine that's already empty. I'd keep it. Kryseans who knew him young would still call him Uxentio.

**On Zaharan — your instinct is right, and the setting backs it hard.** The Zaharan Empire ruled this region from 1,075 BE until it was sacked around 650 BE in the Empyrean War, and its last sorcerer-king was driven **into the Waste** — which is the far side of the Borderlands. So the dread ruins Edward will be working in are, substantially, *Zaharan* ruins. Zaharan platinum and electrum coins still turn up in hoards. It is simply the language the old things are written in.

The necromancers learn it for the same reason he did: that's where the texts are. He got there first and for duller motives. **Nobody will believe that**, which is the tension you wanted, and it doesn't require him to have any interest in necromancy at all.

**And your alternative isn't an alternative — it's a consequence.** Goblin and Orc are *descended from Ancient Zaharan*; the Zaharans bred the beastmen and gave them a debased form of their own tongue. A man who reads Zaharan is already halfway to reading Goblin.

So my recommendation is to **drop Classical Krysean and take Goblin**:

| | Why |
|---|---|
| **Classical Auran** | Imperial inscriptions, charters, boundary stones, and magical script |
| **Zaharan** | What the Borderlands ruins are actually written in |
| **Goblin** | Descends from Zaharan. Spoken by things currently living in those ruins |

Classical Krysean is the weak one — the Krysean War forts he grew up climbing are only a century old and would be inscribed in plain Krysean or Common Auran anyway. And Goblin is the only one of the three he could ever *speak to something* with; the other two are dead languages. That's your ill-advised interest in beastman artifacts, and it has an honest scholarly staircase leading up to it.

Say the word and I'll make the swap, or keep Classical Krysean if you'd rather he could read his own home.

---

## The job

Here's the version I like, and it's built out of what he actually has.

A caravan is going into the Borderlands. The problem with the Borderlands is that **nobody agrees where the Empire stops.** The line was drawn in Classical Auran on stone markers, some of them four hundred years old, and the tolls you owe, the courts you answer to, and — under treasure law — whether a find is yours or half the Empire's, all depend on which side of a given stone you're standing on. Half the caravan masters running that road are guessing.

Edward can read the stones. He can also **drive** — Expert Traveling gave him that, and it's worth six droving animals and double the road-movement bonus. A caravan master gets a boundary-scholar and a second driver in one scrawny package that eats very little.

There's no proficiency throw for translation, incidentally — in ACKS you either have the language or you don't. Multilingual *is* the qualification.

**And I asked the oracle whether the caravan master is hiding his real reason.** Its answer was **no** — by one point on a coin flip, but no is no, and I'll hold to it. He wants the stones read because he wants to know where he is. That's better than a setup, because it means whatever goes wrong is going to come out of what the stones *say*, and out of the Borderlands itself, rather than out of a man lying to Edward in the first scene.

---

Two things and I'll open on the road:

1. **Languages** — swap Classical Krysean for Goblin, or keep as-is?
2. **Uxentio Kupratar** — yes, or would you rather he just be Edward Copper with no back-name?

### Player

I like swapping for Goblin, and I like your original name suggestion. I think we're good to go!

<details><summary>tool — Get Tirenean and Rornish naming conventions</summary>

```
cd /root/.claude/skills/synced/acks-ii && grep -n -A16 "^### Tirenean" setting/entries-2.md | grep -i -A6 "names" | head -20; echo "=== RORNISH ==="; grep -n -A16 "^### Rornish" setting/entries-2.md | grep -i -A6 "names" | head -14
```

```
317-**Names**
318-
319-Tireneans are proudly traditional about names and take care to give every child a carefully-chosen Classical Auran name (though as fluency with Classical's complexities has slipped, many provincial Tireneans now carry vulgarized or hybridized versions of old names). Moreover, while elsewhere in Aurëpos only the upper classes have surnames, in Tirenea even commoners possess hereditary family names (e.g., Syrena Drakon). During the Auran League era it was often claimed that every Tirenean was descended from nobility, which may account for Tirenea's name itself—"land of crowns." Perhaps because commoners have two names, nobles often claim a third name or cognomen based on some characteristic or accomplishment (e.g., Audarius Valerian Tarkaun).
320-
321-**Male Names:** Aurëus, Celictor, Destrio, Gundus, Omus, Quellus, Tavus, Valen, Zelicus
322-
323-**Female Names:** Aurëlyn, Celena, Dalefa, Hyapsë, Istria, Nauriva, Riara, Syrena, Valanna, Zeodarë
324-
325-**Surnames:** Amadorus, Drakon, Hyatavië, Ionicus, Mennicus, Nuvicerres, Süromus, Tarcalus, Valerian
326-
327-*[Source: ACKSII_Revised_Rulebook_DIGITAL_FINAL_r10_2nd_Printing.pdf, p.504]*
328-
329----
=== RORNISH ===
219-**Names**
220-
221-Rornish folk are typically named in the Ivorean language for a famous hero, ancestor, or relative. Rornish commoners do not carry hereditary family names. Men indicate paternity by appending their father's name after their own (e.g., Owain Stuarry, "Owain, son of Stuarry
… (truncated)
```

</details>

<details><summary>tool — Read note templates</summary>

```
cat notes/gm/characters/TEMPLATE.md; echo "=== CLUES ==="; head -40 notes/gm/CLUES.md; echo "=== THREADS ==="; head -25 notes/gm/THREADS.md
```

```
# <Name>

<One line: who they are to the campaign.>

## VOICE

3–5 **verbatim** lines. Pick them for being characteristic, not for being good
— the flat, awkward, or repetitive line is often the more useful sample.

Never paraphrase a voice sample. A description of a voice is not a voice.

- ""
- ""
- ""

**Can't say:** what is outside this voice — the register they never reach for,
the admission they can't make, the word they'd never use. A voice is a ceiling
as much as a vocabulary.

## INTENTION

- **What they're for:** what this character does for the campaign.
- **What they want:**
- **What they'd never do:**

## POSITIONS

What they've committed to, to whom, and what it cost them. Cross-referenced
with `notes/player-facing/POSITIONS.md` when the table saw it.

## Knows, believes, lies

What this person can tell the player, and how reliable it is. Cross-referenced
with `notes/gm/CLUES.md`.

- **Knows:** true things they have, and would say if asked the right way.
- **Believes:** what they'd assert sincerely that isn't so.
- **Lies about:** what they'd knowingly misrepresent, and why.
- **Won't say:** true things they have and would withhold.

## Facts

What's true about them. Include what the player knows, and mark what they
don't.
=== CLUES ===
# Clues

The mystery as a graph, not a trail. Nodes are places, people, and events; the
edges are what one points at another with.

## Revelations

One block per conclusion the player needs to be able to reach. **At least three
i
… (truncated)
```

</details>

### GM

Locked. Let me update the sheet and lay in the prep.

<details><summary>tool — Update sheet with name and languages</summary>

```
python3 - <<'PY'
p='notes/player-owned/edward-copper.md'
s=open(p).read()
s=s.replace("""# Edward Copper

**Venturer 1**""","""# Edward Copper

Born **Uxentio Kupratar** — *Uxentio, of Kupra*, a hill village in Krysea whose one
asset was a copper seam that gave out two generations before he was born. He left, so
he carries the toponymic rather than his father's name. Registering as a trader in the
Empire, he Auranized it: *Kupratar* became **Copper**. Kryseans who knew him young
still call him Uxentio.

**Venturer 1**""")
s=s.replace("""Multilingual's three: **Classical Auran** · **Classical Krysean** · **Zaharan**.
Literate in all five (INT 9 clears the illiteracy line at 8).""","""Multilingual's three: **Classical Auran** · **Zaharan** · **Goblin**.
Literate in all five (INT 9 clears the illiteracy line at 8).

- **Classical Auran** — imperial inscriptions, charters, boundary stones, magical script.
- **Zaharan** — the Zaharan Empire ruled this region 1,075–660 BE and its ruins are what
  the Borderlands is made of. Also the parent tongue of Goblin and Orc. Necromancers
  learn it for the same reason he did; nobody believes that's why *he* did.
- **Goblin** — descended from Zaharan. The only one of the three he can speak *to*
  anything with; the other two are dead.""")
open(p,'w').write(s)
PY
head -14 notes/player-owned/edward-copper.md
```

```
# Edward Copper

Born **Uxentio Kupratar** — *Uxentio, of Kupra*, a hill village in Krysea whose one
asset was a copper seam that gave out two generations before he was born. He left, so
he carries the toponymic rather than his father's name. Registering as a trader in the
Empire, he Auranized it: *Kupratar* became **Copper**. Kryseans who knew him young
still call him Uxentio.

**Venturer 1** (Antiquary template) · Human, Krysean · Lawful · Age 22 · Man-sized, 15 stone
Title: **Tinker** · XP **0** / 1,500 to 2nd level · **+5% XP** (CHA 13)

Middling height, scrawny, short sandy hair.

## Attributes
```

</details>

<details><summary>tool — Write NPC files</summary>

```
cat > notes/gm/characters/destrio-mennicus.md <<'EOF'
# Destrio Mennicus

Tirenean caravan master. Hired Edward to read boundary stones on the Borderlands
road. **He is not hiding anything** — the oracle was asked directly and said no.

## VOICE

- "I'm not asking what it means. I'm asking what it *says*."
- "Four times this year. Four. And every time the man has a different reason."
- "You'll get the rest at Mirmen Ford, and not before, and I'd think less of you if you took it now."
- "Read it again."

**Can't say:** anything about the past that isn't a grievance about money. He does
not reminisce, does not speculate, and cannot manage a compliment that isn't
phrased as a complaint about someone else. He will never say he is frightened.

## INTENTION

- **What they're for:** the honest man who brings the problem in. He is the proof
  that the toll operation is bleeding ordinary traders, and he is the reason Edward
  is standing at the stone at all.
- **What they want:** to know which side of the imperial line his wagons are on,
  because he has paid the Empire's half four times this year on cargo he believes
  was recovered outside it, and he cannot dispute a toll he cannot read.
- **What they'd never do:** run the border at night to dodge a toll. He is a
  grumbler, not a smuggler, and he thinks smugglers get people killed.

## POSITIONS

Nothing committed in play yet.

## Knows, believes, lies

- **Knows:** he has been tolled four times this year at the Mirmen crossing by men
  who produced a commission and a seal. He knows the toll-taker's name: Quellus
  Tarcalus. He knows the tolls got heavier after the legions went west.
- **Believes:** that the tolls are legal and merely greedy. He has no idea the
  stones have been moved. He thinks he is being gouged, not defrauded.
- **Lies about:** nothing. He is blunt to his own cost.
- **Won't say:** what the cargo actually is, unless pressed — not because it's
  illegal, but because he thinks it's nobody's business. (I
```

```
ok
```

</details>

<details><summary>tool — Record the boundary stone truth, clocks, rulings</summary>

```
python3 - <<'PY'
p='notes/gm/STATE.md'
s=open(p).read()
s=s.replace("""| Clock | Segments | Filled | What happens when it completes |
|---|---|---|---|
| | | | |""","""| Clock | Segments | Filled | What happens when it completes |
|---|---|---|---|
| Quellus learns someone has read the stone properly | 4 | 0 | He stops being a toll problem and starts being a man protecting a secret. He will not kill over it at first; he will confiscate, detain, and produce paperwork. |
| The Mirmen crossing stops being tolled at all | 6 | 1 | Quellus's men give up on him. The strip becomes open ground, and something worse than a fraudulent customs officer moves onto the road. |""")
s=s.replace("""| Situation | Ruling | When |
|---|---|---|
| | | |""","""| Situation | Ruling | When |
|---|---|---|
| Translation between known languages | No proficiency throw. In ACKS you have the language or you don't; Multilingual *is* the qualification. A throw may govern how long a long document takes or what else is noticed, never whether it can be read. | Session 1, chargen |
| Edward's literacy | INT 9 clears the illiteracy line (8 or less is illiterate per the Language proficiency text). He reads and writes all five of his languages. INT +0 grants no additional ones. | Session 1, chargen |
| Bribing Quellus Tarcalus | His Bribery-resistance is not a mechanical immunity — it's that he cannot recognise a bribe as a bribe. Offered as a fee, tariff, duty, or fine, the power works normally. Offered as a bribe, it insults him. | Prepped, not yet in play |""")
s=s.replace("""## Chaos factor

**5**""","""## Chaos factor

**5**  *(unchanged through chargen; first move it after the opening scene resolves)*""")
s += """
---

## The boundary stone on the Mirmen road

**Resolved on establishment. None of this has reached play.**

The marker Edward is being asked to read is a genuine Auran boundary stone,
Classical Auran, cut in the reign of Ulkyreus about three hundred and eighty
years ago. The inscription 
```

```
ok
   does not match the road. **(core)**

Any one of these gets him to "moved." All three are free to a character who looks
at the stone — never gated behind a throw. A throw governs only how fast, and what
else he notices while he's down there.
```

</details>

<details><summary>tool — Populate clues and threads</summary>

```
python3 - <<'PY'
p='notes/gm/CLUES.md'
s=open(p).read()
s=s.replace("""### <Conclusion the player should be able to reach>

| Clue | Where it lives | Core? | Status |
|---|---|---|---|
| | | | undelivered |
| | | | undelivered |
| | | | undelivered |""","""### The boundary stone has been moved outward from where it was cut for

| Clue | Where it lives | Core? | Status |
|---|---|---|---|
| Weathering band on the stone below the current ground line — it stood at a different depth elsewhere | The stone itself, visible to anyone who crouches | **core** | undelivered |
| The socket is darker rock than the marker, carrying effaced angular carving — Zaharan, which Edward reads | The stone's base | **core** | undelivered |
| The inscription's cited distance to the next marker does not match the road | The inscription, readable in Classical Auran | **core** | undelivered |
| Destrio has been tolled four times this year and says the tolls got heavier after the legions went west | Destrio Mennicus, if asked about the tolls | no | undelivered |

### Quellus Tarcalus's commission expired three years ago

| Clue | Where it lives | Core? | Status |
|---|---|---|---|
| He will show the commission on demand and cover the term-date line with his thumb | Quellus, in person | **core** | undelivered |
| His men are unpaid in coin and paid in the toll take; some are no longer soldiers in any sense | The crossing camp, observable | no | undelivered |
| No imperial officer has been through the crossing in four years, and he forwards a share to an office that never replies | Quellus if he is treated as legitimate; his ledger | no | undelivered |
| He substitutes "unrelieved" for "abandoned" every single time, without exception | His speech | no | undelivered |""")
s=s.replace("""| Person | Knows | Believes (may be false) | Will lie about |
|---|---|---|---|
| | | | |""","""| Person | Knows | Believes (may be false) | Will lie about |
|---|---|---|---|
| Destrio Mennicus | He has been tolle
```

```
ok
```

</details>

<details><summary>tool — Update ledger and record, commit and push</summary>

```
python3 - <<'PY'
p='notes/player-facing/STATE.md'
s=open(p).read()
s=s.replace("- **Where:** the Borderlands. Exact location not yet established in play.","""- **Where:** the Borderlands road, a day or so short of Mirmen Ford, with Destrio
  Mennicus's caravan — four wagons, eleven people, two of them armed.
- **Employment:** hired at Kavala to read boundary stones on the road-legs to
  Mirmen Ford. Half the fee paid up front, half on arrival.""")
open(p,'w').write(s)
PY
cat > notes/player-facing/RECORD.md <<'EOF'
# Record

What happened, in play order. Append-only. Never tidied, never summarised down.
Only what came from play goes here.

---

## Session 1

**Character creation.** Edward Copper — born Uxentio Kupratar, of Kupra in Krysea —
Venturer 1 on the Antiquary template, Lawful, 22 years old. Attributes rolled with
the 5d6 on Charisma and 4d6 on Intellect and Dexterity; Charisma came up 12 and was
floored to 13, Dexterity came up 16, so he ended quicker than he is charming. Hit
points rolled 3, raised to 4 by the minimum. Four hit points.

Lines and veils settled before play: no violence to children, no body horror,
torture veiled. The player was told about the stop/skip/rewind lever.

The Antiquary template was taken by choice rather than rolled, at the player's
request, as a one-time chargen exception.
EOF
git add -A && git commit -q -m "Finalize Edward Copper and prep the opening scene

Adds the Krysean birth name, swaps Classical Krysean for Goblin, and lays in
the Borderlands prep: Destrio Mennicus, Quellus Tarcalus, the moved boundary
stone with its three core clues, two clocks, and three rulings." && git push -u origin claude/acks-character-creation-izgrz2 2>&1 | tail -3
```

```
To https://github.com/awenonian/ACKS-1
   dc1f2d5..419ae47  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

Everything's committed. Prep is in `notes/gm/` — the stone, the two people, the clocks, three rulings.

---

# The Mirmen Road

Late in the day, and the light has gone long and orange across the scrub. You have read four boundary stones since morning, Edward, and four boundary stones is a great deal of kneeling in gravel for eight gold pieces. The first three were exactly what they should have been: imperial markers, Classical Auran, the standard formula, *thus far and no further, by the will of the Tarkaun*, with the road-distance to the next one cut underneath. You wrote each into the collector's journal because you write everything into the collector's journal.

Destrio Mennicus has stopped the wagons for this one. He does not stop the wagons for anything, so the drivers are already unhitching and grumbling about it, and the woman on the second wagon — Nauriva, who has said perhaps nine words to you in six days and eight of them were about the fish sauce — is looking at the sky in a way that means she thinks this is going to cost them the ford crossing tomorrow.

The stone stands where the road bends around a spur of grey rock. Waist-high. Granite, pale, the colour of a dirty tooth. Lichen up the north face.

You crouch.

The inscription is Classical Auran and it is in beautiful condition — better than the last three, the cuts still crisp under your thumb. The reign is Ulkyreus. That puts it around three hundred and eighty years old. The formula is correct, word for word, the same one you have copied out four times today.

At the bottom, where the road-distance goes, it says **eleven leagues to the marker at Casra Nuvicerre.**

You have been walking since dawn and you passed Casra Nuvicerre yesterday morning.

Destrio is standing over you with his arms folded, blocking what's left of the sun.

> "Well? Same as the others?"

He wants a yes. He has four wagons and eleven people and a ford to make tomorrow, and what he wants is for you to say *yes, same as the others,* so everyone can get moving.

One other thing, and I'm telling you because you're kneeling right beside it: the stone isn't sitting on the ground. It's set into a socket — a squared block, mostly buried, that it stands in. And the socket is a different rock. Darker. Almost black where the dirt's rubbed off it.

The marker is granite. Whatever it's standing in isn't.

What do you do?

### Player

So I think I have the picture, but just to clarify, it says Casra Nuvicerre is 11 leagues forward, but it's behind us? 
And just to corroborate my suspicions, the others, which were in worse condition, were they older than this one, or newer (in terms of reign, since I don't know if Edward knows geology enough to date the stone)? By how much?

### GM

Good questions, and both are things Edward would know cold — he's got them in the journal. No roll; this is reading, which is the thing he does.

Let me firm up the prep to match.

<details><summary>tool — Resolve stone condition, update clues, push</summary>

```
python3 - <<'PY'
p='notes/gm/STATE.md'
s=open(p).read()
s=s.replace("""**It is not standing where it was cut for.** Quellus Tarcalus had it pulled and
re-seated roughly three miles further out, in the second year after the legions
went west, using six men and a sledge. He set it into the nearest available
socket, which was not an Auran one — it is the base of a much older Zaharan
marker, its carving nearly effaced.""","""**It is not standing where it was cut for.** It had *fallen*, face-down, and lain
that way long enough that the buried inscription was protected while its fellows
weathered upright for three and a half centuries. That is why it is the crispest
stone on the road and the newest-looking, despite being of the same reign and the
same cutting program as the other four. Quellus Tarcalus found it down, and in the
second year after the legions went west he had it carried roughly one league — three
miles — further out and stood back up, with six men and a sledge. He set it into the
nearest socket that would take it, which was not an Auran one: it is the base of a
much older Zaharan marker, its carving nearly effaced.

This matters for how Quellus reads himself. He did not deface a boundary; he
*re-erected a fallen imperial marker*, which is very nearly a pious act, and then
put it where it suited him. He has never let himself finish that second thought.""")
s=s.replace("""1. A weathering band on the stone *below* the current ground line. It stood at a
   different depth somewhere else. **(core)**""","""1. **Condition.** All five markers on this road are of the reign of Ulkyreus — same
   formula, same hand, one cutting program, all about 380 years old. The other four
   are weathered as 380 years of standing upright will weather a stone. This one is
   crisp. Something protected it for most of that time. **(core)**""")
s=s.replace("""3. The inscription cites a distance to the next marker down the line. That figure
   does not match the road. **(core)**""","""
```

```
419ae47..4a6b53c  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

**On the distance:** yes. The stone names Casra Nuvicerre at **eleven leagues**, and Casra Nuvicerre is *behind* you. That part isn't strange by itself — these markers cite the neighbouring stone in the line, and which side of you it falls on depends on which way you're walking. The four before it cited the one ahead; this one cites the one behind. Fine.

What's strange is the number. You've been keeping the journal, and you keep the road-legs in it because you always have. By your own notes it's nearer **twelve** leagues back to Casra Nuvicerre, not eleven.

One league out. Three miles.

That's the sort of error you could argue about — road-legs are reckoned by different men in different centuries and nobody's ever agreed what a league is to the pace — and any surveyor would tell you a league of slop over eleven is nothing worth writing home about.

*(One correction to something I said loosely: you passed Casra Nuvicerre the morning before last, not yesterday. The wagons don't move that fast.)*

**On the reigns — this is the better question.** You don't need geology. You need to read, and you've read all five today.

They are all **Ulkyreus.** Every one. Same reign, same formula word for word, and near enough the same hand that you'd bet the journal they came out of a single cutting program — one commission, one gang of masons, one summer, about three hundred and eighty years ago. That's how the Empire did boundaries: not stone by stone as needed, but a whole line at once.

So the four you read this morning are three hundred and eighty years old, and they look it. Lichen in the cuts. The Tarkaun's name gone soft at the edges. On the third one you had to go at a numeral with your thumbnail to be sure of it.

This one is the same age.

You can still feel the chisel marks.

---

Destrio shifts his weight. The sun's behind him and you can't see his face, only that he's stopped folding his arms.

> "Copper. You've gone quiet. I don't pay for quiet."

Behind him, the drivers have got the mules half-unhitched and are waiting to hear whether that was a waste of twenty minutes. Nauriva's still watching the sky.

The stone is at your knee. The socket it stands in is dark, and mostly buried, and you have not yet put a hand on it.

### Player

I want to talk to him, hushed enough that the others don't need to overhear, just in case he wants to handle this a specific way and needs deniability.
"There's something up with this stone. I think it might be fabricated somehow. The distance is wrong and it's not worn enough."
"The words are correct otherwise." I add, after a beat. In case he wants to just move on. That's not really my call.

### GM

He doesn't lower his voice. Not at first.

> "*Fabricated.*"

Loud enough that the nearest driver's head comes round, and Nauriva stops looking at the sky.

Then something moves behind Destrio's face, and he does a thing you have not seen him do in six days on the road: he gets down on his knees. In the gravel. In a good wool cloak, with his back squarely to the wagons, so that whatever's on his face is between him and you and the stone and nobody else.

For Destrio Mennicus, that is an act of enormous subtlety.

> "Say the rest of it. Quiet."

You've already said it. He works through it anyway, mouth moving slightly, the way he does over a tally.

Then, not to you — to the stone:

> "Four times this year I've paid at Mirmen Ford. *Four.* Man with a seal and a commission and eleven men behind him. Every time the sum's different and every time he's got a reason for it."

His thumb finds a cut in the granite and stays there.

> "The Empire's half. That's what he calls it. The Empire's half, on what I've carried out of the Empire and back into it, and I pay, because what am I going to do — argue Auran law with a man who's holding the paper when I can't read the paper?"

He looks up at you for the first time since he knelt. He is fifty and his eyes are not good and he has been squinting at this road for thirty years.

> "So tell me plain. That thing there. Is it telling me I'm inside the Empire, or outside it?"

And before you can answer, he's already gone past it, because he's a practical man and the answer is not the problem:

> "Because I can't walk up to that man at the ford and tell him my scholar had a *feeling* about a rock."

He's still on his knees. Behind him the mules are half-unhitched and going nowhere, and somebody has started a small fire without being told to, which means the drivers have decided this is a camp whether or not anyone said so.

> "How long. To be sure."

---

Here's what that costs, said out loud before you decide, because you should know it going in.

The socket is buried. Getting down to it properly — clearing the packed dirt from around the base, enough to see the whole block and whatever's on it — is the better part of an hour with a hammer and your hands, and you have a small hammer and no shovel. That hour is the light. And Nauriva, who has been watching that sky since noon and has not been wrong about weather once in six days, calls over without being asked:

> "You dig, we don't make the ford tomorrow. Water'll be up by second bell and we sit on the bank till it drops."

Destrio doesn't contradict her. He waits.

**So: an hour and the ford, to find out what's under the stone.** Or you tell him the words are correct and the road is long, and the caravan makes Mirmen Ford tomorrow morning, and you meet the man with the seal with nothing in your hands but a discrepancy of one league.

What do you do, Edward?

### Player

This is his profit on the line, not mine. Yet. So this is ultimately his decision. But I'll lay out what's wrong. 
"The stone has all the right words, but the others listed the next location going west, this one lists it east, and is off by a league. But the main thing is that the words say it's from Ulkyreus' reign, 380 years ago. But you can still feel the chisel marks. You can check that for yourself."
"It sounds like the guy's gonna take us for a ride. But Nauriva's right, checking costs us the Ford. So the question is whether his ride is more expensive than that."
"Though if proof gets you out of the con on later journeys, it could be worth it. Assuming it doesn't just make him cause you different trouble."

<details><summary>tool — Scene check for the dig</summary>

```
python3 scripts/oracle.py scene "Edward gets his hour at the stone and clears the socket undisturbed" --chaos 5
```

```
Expected: Edward gets his hour at the stone and clears the socket undisturbed
SCENE INTERRUPTED   (rolled 2 vs chaos 5)
  The expected scene does not happen. This does:

  RANDOM EVENT: something hidden becomes visible
  read as: betray / law
  This happened. Work out what it means before you narrate on.
```

</details>

### GM

The oracle interrupted the scene, and I'm taking it.

<details><summary>tool — Resolve the oracle interruption and record it</summary>

```
cat > notes/gm/characters/nauriva.md <<'EOF'
# Nauriva

Wagon-woman on Destrio Mennicus's caravan. **Paid by Quellus Tarcalus to ride ahead
and tell him what is coming down the road.** Established by an oracle interruption in
session 1 — the world did this, not the plan.

## VOICE

- "You dig, we don't make the ford tomorrow. Water'll be up by second bell and we sit on the bank till it drops."
- "It's the fish sauce that'll turn. Not the iron."

She has said perhaps nine words to Edward in six days and eight of them were about
the fish sauce. That is not shyness; it is a policy.

**Can't say:** anything about herself. She has no small talk and does not accept it.
She will never ask a question she does not need the answer to.

## INTENTION

- **What they're for:** the reason the toll is always different and the toll-taker
  always has a reason. She is why Quellus knows the cargo before it arrives. She also
  re-reads one line the player already heard, which is the best kind of reveal.
- **What they want:** the retainer. It is small and it is regular and regular is the
  rare thing on this road. She has been doing it four years and does not think of it
  as informing; she thinks of it as telling a customs officer what is in the wagons,
  which is what customs officers are for.
- **What they'd never do:** hurt anyone, or let anyone be hurt if she can help it.
  She rides ahead; she does not fight, and if it ever came to violence over a toll
  she would be the one arguing to pay.

## POSITIONS

- **Argued against the dig, in the open, in front of Destrio and Edward.** Framed as
  weather and the ford. The weather part was true. *(Session 1)*

## Knows, believes, lies

- **Knows:** Quellus pays her. She knows the cargo of every caravan she has ridden
  with for four years and has told him all of it.
- **Believes:** that this is legitimate and slightly clever, and that Destrio would
  be tolled anyway. She has never once tested that belief.
- **Lies about:** nothing, out 
```

```
4a6b53c..9b02be5  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

He listens to all of it without interrupting, which is not like him.

Then he does the thing you told him to do. He takes off his glove, puts his thumb into the deep cut of the **U** in *Ulkyreus*, and drags it down the stroke.

You watch him find the edge.

> "That's sharp."

> "That's *sharp*, Copper. Three hundred and eighty years and I've a splinter of it in my thumb."

He gets up off his knees, slowly, in the manner of a man of fifty who has been kneeling on gravel, and stands looking east down the road for a while — toward the ford, toward tomorrow, toward the man with the seal.

> "Different every time and always a reason." He says it to the road. "I've told myself that four times this year like it was a joke I was in on."

Then, to the drivers, at full volume and without any pretence of discretion at all:

> "We're camped. Get the mules off properly, we're not going anywhere. **Kest** — give the man your mattock and then keep away from him, he's working."

And to you, quieter again:

> "One hour. And you write it. Not in your own shorthand, in words a magistrate reads, with the day on it and my name under yours, because when I put this in front of somebody I want it to look like a document and not like two men complaining."

That's an hour, a mattock, and a commission. It's also, if you were counting, the first time anyone has asked Edward Copper for a professional opinion in writing.

---

The light goes copper, then red. You work.

Forty minutes in, you have the base cleared on three sides and you know several things with your hands rather than your eyes.

The socket is a **separate block**, squared, sunk deep, and it is not granite. Darker, denser, cold in a way the granite isn't even as the day heat comes out of the ground.

The Auran stone **does not fit it.** It is wedged. Packed rubble and broken tile hammered down all round the shaft to hold it plumb, and the tile is not old.

And on the upper face of the block, under where the granite overhangs it, where four hundred years of weather never reached — **carving.** Angular, deep, cut by someone who wanted it to last, and worn nearly to nothing all the same, which means it was standing in the open a very long time before the granite went on top of it.

You can read Zaharan. There is enough left to know two things and not a third: it is a **marker**, in the formal register, the kind of thing put up to say *this, and no further* —

— and the surviving characters are not a boundary formula.

You are still working out what they are when Destrio says your name in a voice you haven't heard him use.

> "Copper."

He's standing at the edge of the firelight with a tally-board in his hand, and he's not looking at you or at the stone. He's looking at the picket line.

> "Where's Nauriva."

The second wagon's mule is gone. So is Nauriva. So, when Kest checks, is her blanket roll and nothing else — not the fish sauce, not her share of the pot, nothing she'd have to explain carrying.

The road east is dark and empty and there's no dust hanging in it, which means she didn't leave in the last few minutes.

It's about eleven miles to Mirmen Ford.

What do you do?

### Player

"Was anyone friendly to her? Know why she was joining up besides a paycheck?"
It looks like she decided to go out alone rather than wait a couple days. That's... either a stupid move on her part, or an incredibly smart one.
It could be enemy action. She's cohort of the guy ahead, and was supposed to keep us moving, but now needs to warn him we're gonna find out. Or her eyes saw that the Ford is worse than we thought, and it'll be dangerous.
Or she's just impatient. But I'd think she's smarter than that.

### GM

Destrio's answer comes fast, because he's already been through it.

> "Friendly to her." He says it like the word's got a stone in it. "Nobody was friendly to her. She didn't take it. Kest tried, first week out, offered her a place at the fire and she said no thank you and sat with the mule. That's not a woman with a grievance, that's a woman with a *policy*."

He turns the tally-board over in his hands.

> "And she didn't join up. She came to me. At Kavala, in the yard, before I'd put word out I was hiring." A pause; his jaw works. "Asked for the Mirmen run. By name. Not work — *that* run."

> "I offered her four a week. She said three."

He looks at the board again, at his own handwriting.

> "Eleven days on here. Owed. She's left it."

**Kest** — who is nineteen, drives the third wagon, and has spent six days badly wanting to be useful in front of the master — is hovering close enough to hear and can't hold it in:

> "She never took her boots off."

Destrio looks at him.

> "She *didn't*, though. Slept in 'em. Every night. And the mule was saddled at dusk, always, I thought she was just —" He stops, because he was going to say *finicky*, and he can hear that it isn't the word. "She keeps her own mule. She paid for it herself. That's not usual for a hand."

Then, defensively, because he liked her:

> "She's not — look, she stopped us at the Vetch creek. Four days back, when it was up. Vardo wanted to run it and she said don't, and we didn't, and it took a Krysean drover's cart down that same afternoon. She's *right* about water. She's never once been wrong about water."

Nobody says anything for a moment. The fire pops. Out past the wagons the road east is a lighter grey line in a darker grey country, and there is no dust in it and no sound on it.

Destrio breaks it.

> "I don't know what she's doing. I'm not going to stand here and invent it." He puts the board down. "I know she's gone. I know she left eleven days' wages on my board rather than ask me for them. And I know a woman doesn't do that to save herself an argument."

He wipes his hands on his cloak.

> "It's eleven miles. She's got an hour and a half on us and a mule bred for it. If she wants to be at that ford by midnight she'll be at that ford by midnight, and there's nothing on this road that'll catch her but weather."

---

So. The state of things, Edward:

- It's full dark. The fire's lit and the camp is made, whether or not anyone meant to make it.
- **The socket is still half-buried**, and you have not finished reading what's cut into it. You know it's Zaharan, you know it's a marker, and you know the surviving characters aren't the boundary formula you'd expect. You put the mattock down when Destrio called your name.
- **The document isn't written.** Destrio asked for it in words a magistrate reads, with the date and his name under yours.
- Mirmen Ford is eleven miles east. The water will be up by second bell.
- You have four hit points, a crossbow, and no mule.

What do you do?

### Player

I mean, I'm not being paid to play reckless hero. I'm not sure why she left, but maybe she had some professional interest in the Ford, though who knows what and why it couldn't wait.
I think she's a lost cause, at this point, so since the costs been sunk, I may as well finish this work. Let's see what this stone is, because I'm not seeing how it adds up.

### GM

Reading the stone is what Edward *does* — no roll for that, and I won't gate it. But dating the thing is extra, so here's the stake before the die: **succeed and he can place what period of Zahar cut it. Fail and he can't, and he'll need a library or a paid scholar to tell him, which costs time and money he doesn't have.** Knowledge (history), 11+.

<details><summary>tool — Knowledge history throw</summary>

```
python3 scripts/roll.py '1d20' && echo "(Knowledge (history), target 11+, no modifiers — INT 9 is +0)"
```

```
18   1d20: [18]
(Knowledge (history), target 11+, no modifiers — INT 9 is +0)
```

</details>

<details><summary>tool — Resolve the Zaharan find, record, push</summary>

```
python3 - <<'PY'
p='notes/gm/STATE.md'
s=open(p).read()
s=s.replace("""**6**  *(raised from 5 after the stone scene: Nauriva's ride left Edward materially
less in control than he started it)*""","""**5**  *(6 after Nauriva's ride; back to 5 after the dig, which Edward finished on
his own terms and got exactly what he went for)*""")
s+="""
## What the Zaharan socket actually is — RESOLVED, mostly unrevealed

The block under the Auran marker is **in situ**. It has never been moved. The Zaharan
line runs through this spot and always has; Quellus simply found a ready-made hole.

It is not a property boundary. It is an **interdiction marker** — the register Zahar
used for sealing a place against entry, not for dividing land. It is one of a series
of **at least nine**. It carries a house-name in the Bet- patronymic form, of which
only `BET-ASHUR—` survives.

**What the nine stones fence** (not revealed, and Edward has no way to know it yet):
a **road**. A Zaharan processional way running from the Borderlands out into the
Waste. When the Empyrean War broke Zahar and the last sorcerer-king was driven into
the Waste — canon, 660–650 BE — his own people sealed the road behind him. Whether
to stop anyone following him, or to stop him coming back, is the question the
campaign is actually about, and **I do not get to keep that open**: it was to stop
him coming back. They were afraid of him, not loyal to him.

**Dating** (delivered — Edward made his Knowledge (history) throw, 18 vs 11+): the
form of the sealing-verb and the orthography of the house-name are last-generation
Zaharan, after the Empyrean War began. He can place it at roughly **655 BE, give or
take a decade.** About thirteen hundred years old.

So: two boundary markers in one socket, nine hundred years apart. The Auran one is
a lie about where the Empire stops. The Zaharan one is the truth about something
else entirely, and nobody has looked at it since Quellus dropped a rock on it.

**Threads this opens:** where the 
```

```
9b02be5..d0902ca  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

**18. Comfortably made.**

---

You go back to the hole.

Kest holds a torch for you without being asked and without saying anything, which is the most useful thing anyone has done for you today. The granite throws a hard shadow down onto the block, so you work by feel as much as sight, thumb into every groove, and copy as you go.

The block is limestone, dark, close-grained. Not local. The nearest bed of that is a long way from here and somebody carried it.

The carving runs along the sheltered upper face where the Auran stone overhangs it, and you get it all.

**First thing.** It is not a boundary formula. The Auran stones use the bounding-verb — *this land, thus far, by the will of.* This uses a different verb entirely, and you know the verb, because it is all over the funerary material and the sealed-place material and nothing else. It is the **sealing**-verb. *Closed. Forbidden. Not to be passed.*

This stone was never about who owns which side of it. It was put here to tell people not to go somewhere.

**Second thing.** It cites its own place in a series. You get the numeral clean, and it is not the first and not the last: this is one of at least **nine**.

**Third.** A house-name, in the Bet- patronymic Zahar used — *of the house of* — and it is nearly gone. What survives is:

> **BET-ASHUR—**

and then a fracture, and then nothing.

**Fourth, and this is the throw you just made.** The sealing-verb has a form to it, and the house-name has an orthography to it, and both of them belong to the *last generation* of Zahar — after the Empyrean War had already started. You can put the cutting inside a decade or so of **655 BE**.

Thirteen hundred years ago. Give or take.

And the block hasn't moved. Nothing about it has been disturbed except by the men who dropped a rock on it — it sits deep, it sits square, and the ground has closed around it the way ground does when it's had a very long time.

Which means: the Zaharan marker is where it has always been. The Auran one is the visitor.

Two boundary stones in one hole, and nine hundred years between them.

---

You write it up by the fire. Not the shorthand — proper hand, Common Auran, the day and the place at the head of it, the reign and the formula of the Auran marker transcribed in full, the road-league discrepancy, the condition of the cutting, the packed tile in the socket. You leave the Zaharan off it. It isn't evidence of anything a magistrate cares about, and Destrio wants a document that looks like a document.

He signs under your name. He writes slowly and he presses hard.

> "Right," he says, and looks at it a while. "Right."

Then he goes to bed, and the camp settles, and out past the wagons the road east is a grey line in a black country.

---

That's a good place to stop if you want one — everything's written up and pushed. But we don't have to.

Where you are, going into tomorrow: **the ford is a day's wait, the water's up, and there's a man at it with a seal.** You have a signed statement in the journal, a discrepancy of one league, and a thing under a rock that nobody in the Empire knows is there.

And **Nauriva has eleven miles' head start** and no reason you've been able to name.

### Player

That's... not really evidence, though is it? Do the other stones have Zaharan under them? Probably, if that's what these pits are for, so that doesn't mean much. But how would I present that the stone was faked? The best argument is the chisel marks, but that's hardly usable, since what proof can we bring of that? Are there any other discrepancies? Verbiage that's a century out of date, or chiseling techniques that produce more modern shapes than the classical masons would? e.g. rounded letters or something.

### GM

You're right that it isn't evidence, and Edward knows it — which is why he goes back out with the torch instead of sleeping.

So let's do this properly. You've named four tests, and they're the right four.

<details><summary>tool — Record forensic findings and push</summary>

```
python3 - <<'PY'
p='notes/gm/STATE.md'
s=open(p).read()
s+="""
## The forgery tests — every one comes back authentic

The player pushed on "was it newly carved," which is the wrong theory, and the
honest answer is that the stone survives every test an antiquary can put to it.
Do not soften this and do not hint. The world's answer is that the inscription
is genuinely 380 years old.

**Delivered, session 1, free (no throw — same examination he already made his
Knowledge throw on):**

- **Letterforms** — correct for the reign of Ulkyreus, including the flat-tailed
  R that went out of the imperial hand within two generations after. A forger
  working from a surviving stone could copy it; a forger working from a book
  would get it wrong; nobody would think to.
- **Orthography** — the formula carries an archaic doubled vowel in *Aurë* that
  was dropped from official use about three hundred years ago. Correct for the
  date, wrong for anyone writing it fresh.
- **Tooling** — one chisel, one hand, one width, no recutting, no second pass.
- **Groove patina** — the insides of the cuts are the same colour as the faces.
  A recut inscription shows fresh stone in the grooves. This shows none.

**What he finds instead — the two physical facts that are actually presentable:**

1. **The inscribed face is stained, not weathered.** An even earthy discolouration
   across the whole face, quite unlike the pitted, lichened exposure on the four
   stones read that morning. It is the staining of long ground contact.
2. **There is a soil line on the shaft, three hand-widths above the current
   ground.** A hard band of discolouration running right round the stone, with
   different growth above and below it. It is not at the height the stone now
   stands at.
3. **The tile in the packing is new.** Broken roof-tile hammered in around the
   shaft to wedge it plumb. Tile is manufactured, and Edward knows kiln-types
   well enough to say this is Borderlands work of the last decade or two. 
```

```
d0902ca..845769c  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

**Letterforms.** You look for the tell first, because it's the easiest to get wrong. The imperial hand moved over the centuries and an Ulkyreus stone has a particular treatment — the flat-tailed **R**, which dropped out of official cutting inside two generations after him. It's here. All four of them are here, and they're consistent.

**Verbiage.** The formula carries the doubled vowel in *Aurë*, which was archaic even when this was cut and has been out of chancery use for three hundred years. Nobody composing a fresh inscription would put it in. You'd have to *know* to put it in, and knowing to put it in is knowing more than the man who'd be forging it needs to.

**Tooling.** One chisel. One width. One hand, all the way through, no second pass, no place where a letter's been opened out or deepened.

**Patina in the cuts.** This is the one you actually expected to catch it on. Recut a weathered stone and the grooves come up pale — fresh stone, wrong colour, and you can see it across a courtyard. You get the torch right down into the strokes.

Same colour inside as out. All the way down.

Edward — the inscription is old. It is as old as it says it is. Whatever is wrong here, it is not that somebody carved this last year.

---

Which leaves you kneeling in the dark with a contradiction, so you stop looking for the forgery and start looking at the stone.

**The face is stained.** Not weathered — *stained*. An even, earthy discolouration right across the inscribed face, edge to edge, the colour of the ground. The four stones you read this morning are pitted and lichened and scoured on their faces the way a thing is when it has stood out in the weather for four hundred years.

This one has been *in contact with something*.

**And there's a line on it.** You nearly miss it because the granite's pale and the torchlight is orange. A hard band of discolouration running right round the shaft — soil line, the kind that takes decades to set — with different growth above it and below it.

It sits about three hand-widths above where the stone comes out of the ground now.

**And the packing.** You pull a piece of it out and turn it over in the light: broken roof-tile, hammered down hard around the shaft to hold it plumb. You know tile. You have spent a great deal of your life caring about how tile is made, because tile is what tells you when a ruin was last roofed.

This is Borderlands work. Coarse fabric, dark core, the wide flange they've been throwing here for — you'd say the last twenty years. Certainly not more.

---

You sit back on your heels.

Because *that* is the thing you can carry into a room. Not the chisel marks, which are a feeling in a thumb. Not the league, which any surveyor will argue you out of.

**A boundary stone of the reign of Ulkyreus, standing in packing tile that was fired within living memory.**

You can put a piece of that tile in your pocket. You can put a second piece in Destrio's hand. And you can ask, in front of whoever needs to hear it, why an imperial marker set down three hundred and eighty years ago has been wedged upright with roofing from the last twenty.

It's four hours to dawn. The tile's in your pocket. Destrio's asleep and the document's already signed, and it says nothing about any of this.

What do you do?

### Player

(Ok, out of character, I'm going to say where my heads at, which is close to where Edward's head is at, except he might know something I don't. 
So, the stone *is* 380 years old, but the chisel marks suggest it's... what? Been rechiseled for some reason?
It's been faked, still, anyway, maybe moved a league (or move 23 leagues, from 11 leagues before to 12 after)? Did we see a stand where there should've been a stone but wasn't? And why? Who cares if this stone is 3 miles further, unless there's someone who'd now be in its borders (but we didn't pass any such place between the last stone and here, did we?)
I have no idea how the Zaharan stone connects, except as a reason there was already a stand, which maybe lent some credibility?)

### GM

Answering this out of character, since that's how you asked.

<details><summary>tool — Resolve road legs and commit</summary>

```
python3 - <<'PY'
p='notes/gm/STATE.md'
s=open(p).read()
s+="""
## The road legs — Edward's journal, resolved

The boundary stones on this line are **not** evenly spaced; they were set at terrain
points (bends, ridge ends, dry crossings), so no one would notice a gap by eye. But
Edward records road legs as a matter of habit, and the day's page reads:

| Leg | Distance |
|---|---|
| Stone 1 → Stone 2 | 1 league |
| Stone 2 → Stone 3 | 1¼ leagues |
| Stone 3 → Stone 4 | 1 league |
| **Stone 4 → Stone 5 (this one)** | **2 leagues** |

One league too long, which is exactly the three miles it was carried. The
corresponding leg *ahead* — this stone to the next one east, which nobody has read —
is one league too short. That is a checkable prediction and it is the strongest
evidence on offer: a measurement, not a feeling in a thumb.

**Its original socket is still out there**, one league back west, empty, with a
stone-shaped depression in it. Nobody looked, because the caravan was moving and an
empty hole a few yards off the road looks like nothing at all.

**What lies in the moved strip:** nothing. No settlement, no farm, no holding — scrub,
a dry watercourse, a spur of grey rock. This is important and must stay true. The
strip is not valuable because anybody lives on it. It is valuable because of what
Auran treasure law says about ground that is outside the Empire, and because the
Borderlands is full of ruins. The player has the treasure law on the player-facing
ledger already. **Do not connect it for them.**
"""
open(p,'w').write(s)

p='notes/gm/CLUES.md'
s=open(p).read()
s=s.replace("""### Quellus prices each toll because he knows the cargo in advance""","""### (added) The road-leg gap

| Clue | Where it lives | Core? | Status |
|---|---|---|---|
| Stone 4 → Stone 5 is 2 leagues where every other leg that day was 1–1¼ | Edward's own journal | **core** | **delivered**, session 1, on request |
| The leg from this stone east to the next should therefore be 1 league short — 
```

```
845769c..31c7e46  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

### GM

**Ground rule first, so you know what you're getting from me.** I won't tell you whether a theory is right — not by saying so, and not by going quiet when you're wrong or producing a helpful detail when you're warm. You find out by acting on it and watching what the world does. So everything below is either a fact Edward has, or a correction to something I said badly.

**Three corrections, all mine:**

**1. Not rechiselled.** I gave you that one straight: one chisel, one hand, one width, no second pass, and — the decisive bit — the patina *inside* the grooves matches the faces. A recut shows pale fresh stone in the strokes. There is none. Whatever "sharp chisel marks on a 380-year-old stone" means, it does not mean somebody went over it.

**2. The arithmetic is one league, not twenty-three.** The stone *claims* eleven leagues to Casra Nuvicerre. Edward's road notes make it *twelve*. So the stone is standing one league further from Casra Nuvicerre than its own inscription says it should be. Casra Nuvicerre is west, behind you; you've been walking east. **One league east. Three miles.** That's the whole discrepancy.

**3. You passed nothing.** Between the fourth stone and this one: scrub, a dry watercourse, the spur of grey rock the road bends around. No settlement, no farm, no holding, no boundary wall, nobody's field. If your question is *whose land got moved* — nobody's. There is nobody out there.

**And one thing you asked for that Edward actually has.**

You didn't see an empty socket. You weren't looking, and a stone-shaped hole a few yards off a road looks like nothing.

But you *write the legs down.* You always have. Here's today's page:

| | |
|---|---|
| Stone 1 → Stone 2 | 1 league |
| Stone 2 → Stone 3 | 1¼ leagues |
| Stone 3 → Stone 4 | 1 league |
| **Stone 4 → this one** | **2 leagues** |

The line isn't evenly spaced — they were set at terrain points, bends and ridge-ends and dry crossings, so nobody would clock a gap by eye.

But you have it in your own hand, in ink, from this morning.

That's a measurement. It's not a feeling in a thumb and it's not a surveyor's argument about what a league is, because every one of those numbers was paced by the same man on the same day.

It also makes a prediction you can test tomorrow, on the road you're already going down.

### Player

Ok, with that, let's call it a session. I'll need to take some time to figure out what I and Edward think, and a break would be good. I'm excited to pick it up again next time! (go ahead and push it to main when you're done with your notes)

<details><summary>tool — Close session notes and plan session 2</summary>

```
cat >> notes/player-facing/RECORD.md <<'EOF'

**Testing the stone.** Edward went back out with a torch and put the four forgery
tests to it: letterforms, orthography, tooling, patina in the cuts. All four came
back authentic. The inscription is genuinely of the reign of Ulkyreus. What he found
instead was that the inscribed face is *stained* rather than weathered, that a soil
line runs round the shaft three hand-widths above the present ground, and that the
packing wedging the stone plumb is broken roof-tile of Borderlands make, fired within
the last twenty years. He put a piece of the tile in his pocket.

Going back through his own road notes, he found the day's legs ran 1 league, 1¼, 1,
and then **2** — the leg to this stone twice the length of any other that day.

Session ended here: four hours before dawn, the caravan camped a day short of Mirmen
Ford, the written statement signed and saying nothing about any of this.
EOF
python3 - <<'PY'
p='notes/player-facing/STATE.md'
s=open(p).read()
s=s.replace("""- **Carrying:** crossbow + 20 bolts, short sword, dagger, leather armor,
  backpack, collector's journal, quill and ink, waterskin, 1 week's rations.
  4½ stone — unencumbered.""","""- **Carrying:** crossbow + 20 bolts, short sword, dagger, leather armor,
  backpack, collector's journal, quill and ink, waterskin, 1 week's rations.
  4½ stone — unencumbered.
  Plus: **a piece of the packing tile**, and Kest's borrowed mattock.""")
s=s.replace("""- **Where:** the Borderlands road, a day or so short of Mirmen Ford, with Destrio
  Mennicus's caravan — four wagons, eleven people, two of them armed.""","""- **Where:** camped at the fifth boundary stone, a day short of Mirmen Ford. Four
  hours before dawn. Destrio Mennicus's caravan — four wagons, now ten people.""")
s+="""
## Open, as of the end of session 1

- **The signed statement** is in the journal: date, place, the Auran formula in full,
  the league discrepancy, the condition of the cutting, the tile in the sock
```

```
31c7e46..82ea682  claude/acks-character-creation-izgrz2 -> claude/acks-character-creation-izgrz2
branch 'claude/acks-character-creation-izgrz2' set up to track 'origin/claude/acks-character-creation-izgrz2'.
```

</details>

<details><summary>tool — Merge session branch to main and push</summary>

```
git fetch origin main 2>&1 | tail -2 && git checkout main 2>&1 | tail -1 && git merge --ff-only claude/acks-character-creation-izgrz2 2>&1 | tail -3 && git push origin main 2>&1 | tail -2 && git log --oneline -1
```

```
fatal: couldn't find remote ref main
error: pathspec 'main' did not match any file(s) known to git
Already up to date.
error: src refspec main does not match any
error: failed to push some refs to 'https://github.com/awenonian/ACKS-1'
82ea682 Close session 1 and plan session 2
```

</details>

<details><summary>tool — Check available branches</summary>

```
git branch -a && echo "--- remote HEAD ---" && git remote show origin 2>&1 | head -8
```

```
* claude/acks-character-creation-izgrz2
  claude/ttrpg-gm-system-prompt-122hux
  remotes/origin/claude/acks-character-creation-izgrz2
  remotes/origin/claude/ttrpg-gm-system-prompt-122hux
--- remote HEAD ---
* remote origin
  Fetch URL: https://github.com/awenonian/ACKS-1
  Push  URL: https://github.com/awenonian/ACKS-1
  HEAD branch: claude/ttrpg-gm-system-prompt-122hux
  Remote branches:
    claude/acks-character-creation-izgrz2 tracked
    claude/ttrpg-gm-system-prompt-122hux  tracked
  Local branches configured for 'git pull':
```

</details>

<details><summary>tool — Check if trunk can fast-forward</summary>

```
git log --oneline origin/claude/ttrpg-gm-system-prompt-122hux -1 && echo "--- is trunk an ancestor of my branch? ---" && git merge-base --is-ancestor origin/claude/ttrpg-gm-system-prompt-122hux claude/acks-character-creation-izgrz2 && echo "YES: clean fast-forward" || echo "NO: diverged"; echo "--- commits my branch adds ---" && git log --oneline origin/claude/ttrpg-gm-system-prompt-122hux..claude/acks-character-creation-izgrz2 | wc -l
```

```
d9771ff Initial commit
--- is trunk an ancestor of my branch? ---
YES: clean fast-forward
--- commits my branch adds ---
10
```

</details>

<details><summary>tool — Fast-forward the default branch</summary>

```
git push origin claude/acks-character-creation-izgrz2:claude/ttrpg-gm-system-prompt-122hux 2>&1 | tail -3
```

```
To https://github.com/awenonian/ACKS-1
   d9771ff..82ea682  claude/acks-character-creation-izgrz2 -> claude/ttrpg-gm-system-prompt-122hux
```

</details>

### GM

Pushed. One thing to flag: **this repo has no `main`.** The default branch is `claude/ttrpg-gm-system-prompt-122hux`, and it was still sitting on the initial commit. My branch was a clean descendant of it, so I fast-forwarded it — all ten commits are now on the default branch as well as on `claude/acks-character-creation-izgrz2`. If you meant something else by "main", say so and I'll move it.

---

## Session 1, closed

**Edward Copper** — born Uxentio Kupratar, of Kupra — Venturer 1, Antiquary, Krysean, Lawful, 22. Four hit points, AC 4, sixteen Dexterity and a crossbow, and three dead languages plus one that isn't.

He read five boundary stones, found that the fifth was telling the truth about everything except where it was standing, and spent his employer's ford crossing proving it. He came out of it with a signed statement, a piece of roof-tile, and a two-league leg in his own handwriting.

And under the imperial marker, thirteen hundred years older and never once moved, a Zaharan interdiction stone — one of at least nine — with a house-name worn down to `BET-ASHUR—`.

**What's in the notes for next time:**

- `notes/gm/plans/SESSION-02.md` — where we stopped, what's prepped, and an explicit instruction to my next self not to open by summarising your options or steering you toward a reading. You said you want time to work it out; the notes say to let you move first.
- `notes/player-facing/STATE.md` — the ledger, with everything open listed at the bottom, so you can reread it cold.
- `notes/player-facing/RECORD.md` — what actually happened, in order.
- `notes/gm/` — the truth, the two clocks, the three rulings, and the people.

The rulings that'll hold: translation needs no throw, Edward is literate in all five languages, and chargen was the only place dice got fudged.

Bring me a recap next time, however lossy — the notes can't hold what you thought mattered, and where you and they disagree, you're right.

### Player

Can I get you to upload your transcript into the repo? Make sure it's marked as session 1.

### GM

Found it. Let me look at the structure and convert it to something readable.

### GM

Two problems: some harness blocks survived, and system content is being labelled as the player. The jsonl marks human turns explicitly — let me use that.

### GM

The tail was recursive — tool results echoing the transcript file back into itself. Let me exclude the export apparatus.
