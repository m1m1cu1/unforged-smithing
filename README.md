# unforged-smithing

## Plugins

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
