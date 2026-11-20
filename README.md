# unforged-smithing

## Plugins

**Plugin builder** (Plugins page): make a plugin with forms instead of editing JSON. It covers everything a plugin can hold:
weapon types (with the 4x2 abilities), armor types, shield types (including "no agility nerf"), weapon/bow/armor/shield mods
(levels, values, whole/percent, calculator effects, limiting to bows/armor types/shields, stackable) and races (per-stat overrides).
Entries can start blank or from a built-in one, and are checked live with the same rules the importer uses (name clashes are
flagged). You can open a file, edit an installed plugin, load the example, edit the JSON directly, download the file, or install it
(installing under an existing name updates it). Your work is kept as a draft on the device.

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
