# Total War

A single-file grand strategy game. Six continents, twelve banners, one winner.

Open `index.html` in a browser. That's the whole install.

## The world

Six continents, arranged so every campaign plays differently:

| Theatre | Continents | Character |
|---|---|---|
| Supercontinent | Karrow, Meridia, Sund | Land war. Seven factions, no water needed. |
| The strait | Ivory, Wrack | Short crossing, cheap transports, constant skirmishing. |
| The far shore | Ostrava | Isolated by open ocean. Safe early, dangerous late. |

You are **Ashkar**. Eleven AI factions want what you have.

## Units

| Unit | Role |
|---|---|
| Infantry | Cheap. Weight 1. The only thing that can fly. |
| Armour | Expensive, weight 2, breaks lines. Cannot be air-dropped. |
| Transport | Naval. Carries 8. The only way to land armour at scale. |
| Destroyer | Naval escort and transport hunter. |
| Air Lift | Carries 4 infantry, ignores terrain, interceptable. |
| Fighter | Air superiority. Strikes from range and intercepts enemy aircraft within 3 tiles. |
| Bomber | Damages ships and armies every strike. Vulnerable to fighter cover. |

No single branch wins. Air takes the port with infantry, sea lands the armour
behind it.

## Mechanics

- **Amphibious assault** — attack from a loaded transport at −25%
- **Airborne assault** — drop infantry at −40%; armour is too heavy to fly
- **Air strikes** — bombers and fighters hit any enemy stack within range and
  stay where they are; each strike reports the units it destroyed
- **Interception** — a fighter within 3 tiles of a strike or airdrop has a 45%
  chance to engage; a successful pass shoots the attacker down
- **Supply** — landings without a port in range lose a unit per turn
- **Terrain** — defence multipliers from 1.0 (plains) to 1.8 (mountains)
- **Diplomacy** — non-aggression pacts cost 120 gold and can be broken at any
  time, at the price of immediate war
- **Research** — four branches at your capital: arms, economy, naval, air
- **Fog of war** — you see two tiles from your territory, three from aircraft

## Controls

| Input | Action |
|---|---|
| Left click | Select a tile, or move/attack to a highlighted tile |
| Right click | Cancel selection |
| Mouse wheel | Zoom |
| Space | End turn |
| `Shift+G` | Toggle god mode (unlimited gold) |

Select your capital for recruiting, shipyards, airbases and research.
Select a loaded transport for its landing options.
Select a bomber or fighter, then click an enemy stack in range to strike it.

## Victory

- **Conquest** — hold 60% of all land
- **Elimination** — every rival banner is gone
- **Defeat** — you lose your last territory

## God mode

`Shift+G` reveals an infinity chip in the top bar and makes gold unlimited.
Costs are never checked or deducted while it is on. Your real balance keeps
accruing income and is restored exactly when you switch it off.

## Technical notes

- One file, no dependencies, no build step
- Vanilla JS and canvas, ~2,100 lines
- Saves to `localStorage` each turn
- `index.html#selftest200` runs a headless 200-turn stress test and reports
  invariant violations, AI timing and stalls

The AI is built around explicit state machines rather than emergent behaviour,
because single-file strategy games usually fail by drowning their armies at sea.
Each AI turn runs in about 1–2 ms across twelve factions.
