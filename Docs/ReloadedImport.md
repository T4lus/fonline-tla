# Importing World Map / Locations / Maps from FOnline Reloaded

Reference for porting content from the old-SDK **FOnline Reloaded** server
(`D:\FOnline\FOnlineReloaded Tools\Server`) into this TLA project. For TLA's own
authoritative data, prefer the **TLA SDK** (`D:\FOnline\FOnline-SDK-master`); use Reloaded
only when TLA lacks the content.

This is a conversion **project**, not a copy — the formats diverged years ago and there is
**no built-in old→new importer** in the engine, so a custom converter is required.

## Format gap

| | Reloaded (old SDK r412) | TLA (new engine) |
| --- | --- | --- |
| Map header | `[Header]` — `MaxHexX/Y`, `ScriptModule`+`ScriptFunc`, `DayColor0-3` | `[ProtoMap]` — `Size`, `WorkHex`, `InitScript = NS::Func`, `DayColor` (one line) |
| Objects | `[Objects]` — `MapObjType` + **numeric `ProtoId`** (e.g. `4012`) + `MapX/MapY` | `[Critter]`/`[Item]` — **`$Proto = name`** + `Hex = x y` |
| Tiles | `tile <hex> <layer> art\tiles\xxx.frm` | new tile section |
| Protos | numeric PIDs (`data/ItemNames.lst`, `proto/critters`, `proto/items`) | named protos (`Items/*.foitem`, `Critters/*.focr`) |
| Locations | `maps/Locations.cfg` + `maps/GenerateWorld.cfg` | `.foloc` protos + `Main.fos GenerateWorld()` |
| Map scripts | `map_redding::map_init` (old API) | `MapReddingOuter::MapInit` (new, incompatible API) |

## Procedure

### Phase 0 — Scope & dependencies
Pick the locations/maps to import. List everything each map references — items, critters,
dialogs, bags, scripts — because those must already exist in TLA (or be imported too). Do
not import a map whose critters/items don't resolve to TLA protos.

### Phase 1 — Build the PID → proto-name table (the crux)
Map every Reloaded numeric `ProtoId` to a TLA proto name:
- Items: `data/ItemNames.lst` gives `242 → PID_COMBAT_SHOTGUN`; map `PID_COMBAT_SHOTGUN → combat_shotgun`.
- Critters: same via critter PIDs / `data/CritterTypes.cfg`.
- Output a `pid → tla_proto` lookup (CSV/JSON). Partly automatable by name/sprite matching;
  the misses are manual. Protos that don't exist in TLA must be substituted or imported.

### Phase 2 — Map converter
A script that, per old `.fomap`:
- `[Header]` → `[ProtoMap]` (rename/combine fields; `DayColor0-3` → `DayColor`;
  `ScriptModule/Func` → `InitScript`, or drop).
- `[Objects]` → `[Critter]`/`[Item]` (translate `ProtoId` via the Phase-1 table; `MapX/MapY` → `Hex`).
- `[Tiles]` → new tile format.
- **Validate the hex coordinate system** (origin/orientation; `MaxHexX/Y` vs `Size`) on one
  map first — this is the most likely thing to be silently wrong.

### Phase 3 — Locations
Convert `Locations.cfg` entries → `.foloc` protos (name, maps, entrances), and add
`CreateLocation(Content::Location::x, ipos(wx, wy), …)` to `GenerateWorld()`. World
coordinates come from `GenerateWorld.cfg`.

### Phase 4 — World map
- Terrain tiles: the `art/intrface/GlobalMap/Terrain/WRLDMP*` set (already imported).
- Relief/passability: convert Reloaded's relief (land vs water, used by `GetGlobalMapRelief`)
  into TLA's `relief_tla.png` scheme.
- Location world coordinates (Phase 3).

### Phase 5 — Scripts / content
- Map-init scripts must be **rewritten** for the new API (or stubbed to a minimal init).
- Dialogs / bags / protos the maps reference must exist (import/convert as needed — same
  approach used to restore missing bags from `data/Bags.cfg`).

### Phase 6 — Bake & validate
Open each converted map in **`TLA_Mapper`** to check tiles/objects/coords, then test in-game.
Fix and iterate.

## Recommendation: pilot one map end-to-end first
Before batch-converting, convert a single simple map (e.g. a small Redding interior) fully —
header, a handful of objects via the PID table, coordinates — bake it, and open it in the
Mapper. That validates the converter, the coordinate system, and the PID mapping on a small
surface before scaling to hundreds of maps. Most of the risk (silent coordinate/PID errors)
surfaces there.
