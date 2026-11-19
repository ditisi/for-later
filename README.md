# For Later

A two-player co-op puzzle game about one place in two different years.

A father in 1995 and his daughter in 2026 are on the same floor of the same building. He can leave things and change things; she can only use what survived the thirty-one years in between. Somehow they can hear each other over an old radio, and that's all they have.

Concept by Lisa and Tomaz. The past-and-present idea, the parent and child, and the child having to explain what's blocking her are Lisa's.

## Play

Open `index.html` in a browser. There's no build step and no dependencies (fonts load from Google Fonts). To host it, turn on GitHub Pages for `main`.

**One screen** — both years side by side. Share a keyboard, or play both yourself.

| | Move | Act |
|---|---|---|
| Jan · 1995 | `W` `A` `S` `D` | `E` |
| Mira · 2026 | arrow keys | `Enter` |

You can also click anywhere to walk there, and click things to use them. `H` gives a hint (press again for a bigger one), `P` pauses.

**Two screens** — each player picks a year and sees only that year, so you have to tell each other what you see. Either year moves with WASD or the arrows and acts with `E` or `Enter`.

- On claude.ai (the published version of this page) two screens link up across two computers, through claude.ai's live room for people viewing the same page.
- Opened from this repo, two screens only link windows of the same browser. Playing across two computers from here needs a small relay; see *Next* below.
- Jan's screen runs the game. Keep that tab in front: browsers slow down background tabs, and reloading Jan's tab restarts the level.

## Level one: Vrbna 7

The third floor of a tenement. A gas main has gone in 2026 and the building has twelve minutes left. The flat was renovated in 2004, and that's the rule of the level: anything replaced, bricked up or cleared out in 2004 is gone; anything left alone is still there.

<details>
<summary>The four puzzles (spoilers)</summary>

1. **The flat door.** Mira needs a crowbar. Jan's is behind the drying-room door. Behind the radiator doesn't work (replaced), the meter cupboard doesn't work (bricked up), under the loose top step does.
2. **The roof key.** Jan's kitchen was ripped out, but the chimney breast is in the same place in both years. Key on a nail up the flue.
3. **The hall.** The hall ceiling is down in 2026 and already cracked in 1995. Wedge the spare timber from the back room under the crack.
4. **The fire escape.** It has rusted off in 2026. Oil and paint don't last thirty-one years; refitting the cracked downpipe collar that drips on it does (the wrench is in the kitchen drawer).

</details>

## Code

Everything is in `index.html`, split into sections by banner comments:

- **WORLD** — the two map grids (`MAPS['95']`, `MAPS['26']`) and room regions.
- **ITEMS & SPOTS** — the places Jan can leave things, and whether each survives to 2026 (`good`, `fate`).
- **STATE** — `G`, the whole game state, and `newGame()`.
- **AUDIO**, **TALK** — sounds, the radio log, and the rings that show what changed.
- **JAN'S ACTIONS**, **MIRA'S ACTIONS**, **ENTITIES** — every interactable thing in each year: `ent(era, tiles, {block, act, draw})`.
- **MOVEMENT**, **LOOP** — grid movement, pathfinding, the game tick.
- **DRAW** — all art is drawn on canvas in code; there are no image files.
- **HUD & UI**, **TWO SCREENS**, **INPUT**.

## Next

- Move the level data (maps, spots, entities, text) out of `index.html` into its own file, so levels can be written without touching the engine.
- Two-computer play outside claude.ai: swap the `Net` transport (`setP` and `peers`) for a small WebSocket relay or a hosted realtime service. The sync on top of it doesn't need to change.
- Level two.

## Prototypes

`prototypes/the-quiet-machine.html` is the first concept: a handler and an operative routing a courier through a patrolled city. Kept for history; the game moved on to the version above.

## License

None yet.
