# Unforged

A gear-crafting calculator and character sheet for the **Unforged** tabletop system. It runs in the browser, works offline
once opened, and can be installed on a phone or computer like an app. Everything is stored on your own device; there is no
account and no server.

- [Getting started](#getting-started)
- [Profiles](#profiles)
- [Smithy](#smithy): weapons, bows and arrows, armor, shields
- [Stats](#stats): calculator, actions, passives, character sheet, damage, skills
- [Saving, sharing and moving data](#saving-sharing-and-moving-data)
- [Plugins](#plugins) and the [Plugin builder](#plugin-builder)
- [Installing and offline use](#installing-and-offline-use)
- [Files in this repository](#files-in-this-repository)

## Getting started

1. Open `index.html` (or the hosted page). On the first visit you see the **Profiles** screen.
2. Create a profile (or use **Default**) and press **Open**.
3. The home page offers three tools: **Smithy**, **Stats** and **Plugins**. The **Tools** button in the header returns to this
   page, and **Profile: name** returns to the profile list.
4. **Text size** (A- / A+) in the header changes the size of all text. It is remembered.
5. The app follows your device's light or dark setting.

## Profiles

A profile is one character. Each profile keeps its own:

- Stats calculator values (race, stats, health points)
- Purchased actions and passives, and the chosen fighting style
- Character sheet (equipment, inventory, notes, gold, luck, bleed, ticks, injuries)
- Learned skills
- Saved Smithy items (weapons, bows, arrows, armor, shields)

The list shows how much each profile has spent in thousands of gold (stat and health points, purchases, learned skills and every
saved item). Per profile you can **Open**, **Rename**, **Duplicate**, **Export** and **Delete**. The Default profile always
exists, is always first, and cannot be renamed or deleted. Names are unique (a clash gets a number added) and limited to 40
characters. The profile that was open last opens again next time.

Plugins are **not** part of a profile: they are stored on the device and apply to every profile.

## Smithy

The Smithy calculates what a piece of gear is, what it costs, and what you can put on it. It has four tabs: **Weapons**,
**Bows** (which includes arrows and bolts), **Armor** and **Shields**. Every result updates as you change a setting, and each
result card has **Show the math**, which lists the steps behind the numbers.

### Common ideas

- **Metal.** Eleven metals: Mithril, Iron, Malachite, Steel, Silver, Platinum, Cobalt, Palladium, Tungsten, Dwarven Steel and
  Black Steel. Each has its own price, mod cost, speed and strength changes, extra mod slots and special effects, all listed
  under *Metal effects* on the screen. Examples: Iron gives a bonus for every full 5,000 gold of cost; Steel has an extra mod
  slot; Tungsten and Silver change weapon speed; Cobalt gives base damage reduction on any armor type.
- **Blacksmith level** (1 to 5). Mod slots are the level minus 2 (so levels 1 and 2 give none), plus any base slots (armor) or extra slot a metal grants (for example Steel).
- **Upgrades.** You buy upgrades with ingots. Each further upgrade is worth less than the one before (diminishing returns).
- **Mods.** Each mod has levels that unlock at set levels, and costs ingots per level. Mod values are scaled by the metal
  (whole-number values round with 0.5 up; percentage values keep decimals), except armor mods, which are never scaled.
  The mod list shows how many slots are used, and **Browse all mods** lists every mod and its levels.
- **Automatic clean-up.** If a change makes part of the build illegal (too many mods, a mod the metal or type cannot use, an
  ability that is no longer unlocked), the app removes it and tells you in a popup what was removed.
- **Cost.** Shown as total ingots and total gold.

### Weapons

Fourteen melee weapons: Dagger, Rapier, Shortsword, Broadsword, Axe, Mace, War Pick, Spear, Longsword, Flail, Polearm, Waraxe,
Claymore and Maul. Settings: weapon, metal, blacksmith level, **base damage upgrades** and **pierce upgrades**, and mods.

The result card shows base damage, pierce, speed (lower is faster), strength requirement (wield with this or less), the chosen
mods, the abilities, total ingots and total cost.

- **Mods** for weapons: Speed Strike, Combo Suited, Well Balanced, Enchantable, Unblockable, Serration, Blockable, Injurious,
  Weighted, Unparryable, Armor Cracker, Versatile, Maneuverable, Sharpened Tip and Defensible. Some change the numbers
  (Speed Strike lowers speed, Well Balanced eases the strength requirement); the rest are text effects.
- **Abilities.** Every weapon has 4 ability levels with 2 choices each. You earn one pick per fixed amount of gold spent
  (15,000 by default, set per metal). An ability level is locked until you have picked an ability from the level before it.
- **Thrown ranges.** One-handed weapons show the hexes at which a thrown weapon is Close, in the Sweet Spot or Far (Versatile
  extends them). Two-handed weapons cannot be thrown.
- **Copy description** puts a plain-text description of the weapon on the clipboard to paste into notes or chat.

### Bows

Crossbow, Shortbow and Longbow. Bows upgrade **base damage only**; their pierce comes from the metal (the crossbow gets a
bonus). Bow mods: Well Balanced, Enchantable, Injurious, Recurve, Double Strung, Bow Sight, Tightened String, Refined Grip and
Compact (crossbow only). The Bows screen also shows each range band (Close, Sweet Spot, Far) with its effects, and Bow Sight and the
Precise and Lightweight arrow types adjust the ranges.

**Arrows and bolts** are crafted in sets of 3 with their own metal, level, mods and settings. Arrows upgrade **pierce only**.
An optional **arrow type** (Concussive, Fragmentary, Tracer, Screaming and others) adds an effect; the screen shows what adding
a type would cost. Arrow mods are Serration and Armor Cracker. Tips on the page cover breakage and upkeep.

### Armor

One piece of armor, assumed worn as a **set of 4** of the same metal and type, so effects that need several pieces always count.

- **Types:** Light, Medium and Heavy. Heavy armor and Cobalt give base damage reduction.
- **Player STR** is read from the open profile's stats. The strength requirement (a higher number is easier) feeds the
  **agility nerf**, so armor heavier than you can handle is shown as a larger nerf.
- Results include armor %, strength requirement, agility and sneak nerfs, base damage reduction and cost.
- **Mods:** Unstoppable, Immunity, Deflective, Enchantable, Deductive, Lighten, Strengthen, Folded Metal, Pugilist's Design,
  Thermal Protection, Heated Padding, Non Conductive, Bleed Protection, Poison Protection, Articulated, Jointed Couters,
  Rennzeug, Crumpling Plates, Scale Mail, Laminar, Heavily Reinforced, Ornamental and Stechzeug. Some are limited to certain
  armor types, and only some can be stacked (taken more than once).

### Shields

Buckler, Kite and Tower. Settings: shield, metal, level, **HP upgrades** and mods. Results include HP, armor %, weight, strength
requirement and an agility nerf (the Buckler has none). Shield mods: Swordbreaker, Bulwark, Guige, Ornamental, Reinforced
Lining, Serrated Edges and Bottom Spikes (Tower only). Shield mods use the same slots as weapon mods, scale with the metal,
and nothing stacks on shields.

### Saved items

Each Smithy screen has a **Name** field and a **Save** button. Saved items belong to the open profile and are listed below the
calculator. For each you can **load** it back into the calculator, **delete** it, or **send it to another
profile** (move it or send a copy). Saved items are stored as the *choices* you made, not the results, so they are recalculated
with the current rules (including plugins) whenever they are shown. **Export** and **Import** on a screen save or load a single
item as a `.json` file.

## Stats

The Stats screen has seven tabs. Everything on it saves automatically into the open profile.

### Calculator

Pick a **race**, then spend or gain points on the ten stats: Strength, Melee, Agility, Combat Skill, Ranged, Mana, Toughness,
Charisma, Sneak and Intelligence/Perception. The range is -1000 to 24. For each stat you see the current value, the cost of the
next point and the points spent. A **lower number is better**: "+" worsens a stat and "-" improves it. Improving a stat costs points, and the cost per point depends on how low the stat already is. Changing the race resets every stat to that race's starting values.

- **HP skill points** are put into health. Every full step of points is worth less than the one before (diminishing value),
  and the screen shows the **adjusted HP**.
- **Total health** and the **toughness modifier** are shown at the top.
- **Points spent** and **total cost** (300 gold per point) are shown, with **Show the math**.
- **Points between two levels** works out the points and cost of moving a stat from one level to another.

### Purchasable Actions and Passives

- **Actions** are bought level by level, each level on top of the previous ones, at costs in thousands of gold (k).
- **Passives** are always active. A level costs more the higher you already are. The passive's text updates with the level you
  have. Passives include Block Skill, Bladed Skill, Dual Wield, Shieldmaster, Hunter, Poisoner, Protector, Vengeful, Accurate
  and more.
- **Fighting styles** (The Finishing Touch and Commander) are passives that unlock a whole set of actions. A character can own
  only one; the others are locked while one is owned, and its actions get their own sub-tab of the Actions tab.
- Gold spent here counts toward the profile's total.

### Character Sheet

One sheet per profile:

- Name, background, notes, status and **gold**.
- **Luck** (0 to 5), **bleed ticks**, and **current HP** (it follows max health until you set it).
- **Ticks** and **injury ticks** per stat. The current value of a stat is base + ticks + injury ticks.
- **Equipment:** armor, left hand and right hand pick from your saved Smithy items (two-handed items fill both hands), plus
  free-text ring (x2) and neck slots. The sheet warns when equipped gear needs more strength than you have.
- **Inventory:** 10 slots holding free text, links to saved Smithy items (armor sets and two-handed items take 2 slots), or sets
  of arrows (3 per set, with a count you can reduce as you shoot).
- **Bleed:** X ticks deal X% of max HP at the end of a turn, then the ticks are halved (a single tick just ends).

### Actions

A read-only list of the actions you can use now: the default actions everyone has, your purchased actions, grappling actions
and any fighting-style actions. Speeds that depend on the weapon ("x", "x-3", "x+20") are filled in from the weapons equipped on
the Character Sheet, shown per held weapon (never below 1, or 0 with Maneuverable). A search box filters by action name.

### Damage

Works out **damage received** and **damage dealt**:

> (base damage - base damage reduction, at least 0) x (1 + (pierce % - armor %) / 100, at least 0), rounded to the nearest
> whole number (0.5 up)

Armor, base damage reduction, damage and pierce can be filled in from the gear on the Character Sheet, or typed by hand.

### Learned Skills

Free-text skills for anything the rules do not cover. Write the skill and its level (for example "Blacksmithing skill 3"), the
gold you spent and what it does. The gold counts toward the character's total.

### Side by side

On screens at least 900 pixels wide, **Side by side** shows two Stats tabs next to each other (for example the Calculator and the Character Sheet).

## Saving, sharing and moving data

All data lives in your browser's storage on this device. The app asks the browser to keep it permanently, but clearing site data
or switching browsers removes it, so **export anything you care about**. If saving is not available (for example some private
windows) the app warns you that profiles will be lost when the page closes.

| What | Where | Result |
| --- | --- | --- |
| A whole profile | Profiles > **Export** / **Import profile** | One `.json` named like `Name 42k.json` (name and thousands spent). Importing asks whether to **Replace** a profile with the same name or **Keep both**. |
| All saved Smithy items | Smithy > **Export Smithy** / **Import Smithy** | **Add to existing** or **Replace all**. |
| Stats, sheet, skills and purchases | Stats > **Export Stats** / **Import Stats** | Replaces the profile's stats data after confirmation. |
| One item | Name field on a Smithy screen > **Export** / **Import** | A single weapon, bow, arrow set, armor or shield. |
| A plugin | Plugins page or Plugin builder | See below. |

Imports are checked, and anything damaged or unknown is dropped rather than breaking the app. On phones the file buttons are
hidden because phones cannot use files in a helpful way; there, use **Save** and **Copy description**.

## Plugins

A plugin adds your own content to the built-in rules: weapon types, armor types, shield types, the four kinds of mods, and
races. Open a profile and choose **Plugins** on the home page. There you can **Import plugin** (a `.json` file), paste plugin
text, **Download example**, turn a plugin on or off, export it, edit it in the builder, or remove it.

- Adding, removing or switching a plugin **reloads the page**.
- Plugins **never replace** anything. A name that already exists (built in or from an earlier plugin) is skipped, and the
  Plugins page lists what was skipped and why.
- Items saved with a plugin's type stay in your profile and work again when the plugin is on.
- If a bad plugin ever stops the app from working, open the app with `?noplugins` on the address to start without plugins, then
  turn off or remove the one that caused it.

### Plugin builder

Plugins page > **Plugin builder** makes a plugin with forms instead of editing JSON. It covers everything a plugin can hold:

- **Details:** name (required), version and description, with a summary of what is inside.
- **Weapon types:** speed, base damage, base pierce, base strength requirement, damage type, hands and the 4 x 2 abilities.
- **Armor types:** armor and nerf multipliers, strength change and the heavy base-damage option.
- **Shield types:** HP, HP metal divisor, weight, increment multiplier, strength requirement and agility divisor (or **No agility
  nerf**).
- **Weapon, bow, armor and shield mods:** levels with text, up to 4 values per level (whole or percent) with **Insert {n}**
  buttons and a live preview of the finished text; which value feeds each calculator effect; armor mods can be stackable; bow,
  armor and shield mods can be limited to chosen bows, armor types (including your own) or shield types.
- **Races:** tick only the stats that differ; the rest use the default.
- **JSON:** the file as it will be saved. You can edit it and press **Apply to builder**, or copy it.

Entries can start blank or **from a built-in one** (a copy to change). Everything is checked live with the same rules the importer
uses; problems are shown on the entry and marked with ! on the tab, and a name that already exists gets a warning because it would be
skipped. You can **Open file**, **Edit an installed plugin**, **Load example**, **Download file**, or **Install plugin**
(installing under an existing name updates it). A file with mistakes still opens so you can fix it. Your work is kept as a draft
on the device.

### Plugin file format

Open a profile, then **Plugins** on the home page. A plugin is a `.json` file that adds custom
weapon types, armor types, shield types, mods and races. **Download example** gives a file to start from.

```json
{
  "app": "unforged-smithing", "kind": "plugin",
  "name": "My plugin", "version": "1.0", "description": "optional",
  "weaponTypes": [ { "name", "speed", "baseDamage", "basePierce", "strengthBase", "damageType": "PRC|BLNT", "hands": 1|2, "abilities": [4 levels x 2 choices of { "text" }] } ],
  "armorTypes":  [ { "name", "armorMultiplier", "nerfMultiplier", "strengthChange", "heavyBdmg": true|false } ],
  "shieldTypes": [ { "name", "baseHp", "hpMetalDivisor", "weight", "incrementMultiplier", "strengthBase", "agilityDivisor": number|null } ],
  "weaponMods":  [ { "name", "levels": [ { "level", "text": "... {0} ...", "values": [ { "value", "kind": "int|pct" } ] } ], "effects": { "speed": 0 } } ],
  "bowMods":     [ same, plus optional "weapons": ["Crossbow"] ],
  "armorMods":   [ same, plus optional "stackable": true, "types": ["Light"] ],
  "shieldMods":  [ same, plus optional "shields": ["Kite"] ],
  "races":       [ { "name", "start": { "strength": 17, "agility": 13 } } ]
}
```

- Every list is optional, but a plugin must add something. Unknown keys (like `_help`) are ignored.
- Mod `effects` point at a value of the level (0 is the first). Allowed keys: weaponMods `speed`, `strength`, `throwRange`;
  bowMods `strength`, `speed`, `sweetRange`, `farRange`, `strengthHarder`; armorMods `agility`, `armorMultiplier`,
  `strengthRequirement`, `sneak`, `bdmgMultiplier`; shieldMods `agility`, `armor`. A mod without effects is a text-only mod.
- A race lists only the stats that differ; the rest start at the first built-in race's values.
- Plugins never replace anything. An entry whose name already exists (built in or from an earlier plugin) is skipped, and the
  Plugins page lists what was skipped.
- Plugins are stored on the device, apply to every profile, and reload the page when changed.
  If a bad plugin ever stops the app from working, open it with `?noplugins` on the address to start without plugins.

## Installing and offline use

The app is a progressive web app. Host the files on any static web server (for example GitHub Pages) and open the address:

- **Phone or tablet:** use *Add to Home Screen* (iOS: Share menu; Android: browser menu / *Install app*).
- **Computer:** use the install icon in the address bar of Chrome or Edge.
- **Offline:** after the first visit over `http(s)`, the files are cached. Online it always uses the newest files; offline it
  uses the saved copy.
- **Updating:** `sw.js` has a `VERSION` string. Change it whenever you change the app so devices fetch the new files.

Opening `index.html` straight from disk works for everything except installing and offline caching.

## Files in this repository

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: page, styles, calculation rules and screens in one file. |
| `sw.js` | Service worker for offline use. Bump `VERSION` on every change. |
| `manifest.webmanifest` | Install details: name, colours, icons. |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | App icons. |
