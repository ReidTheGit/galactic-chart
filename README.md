# Vash-Karel Galactic Charter

An interactive 3D star chart built from a Stellaris save: It holds, 988 systems, 8,602 bodies,
25 territorial empires, 5 federations and 16 nebulae, with an orbital view of every system.

It is one self-contained `index.html`. There is no build step and nothing to install —
Three.js and the fonts load from public CDNs at runtime.

## Controls

| | |
|---|---|
| Drag | orbit the camera |
| Shift-drag, or right-drag | pan |
| Scroll, or pinch | zoom |
| `W` `A` `S` `D` | fly · `Q` / `E` up and down · `Shift` to sprint |
| Click a star | system details |
| Enter system | orbital view — click any body for detail |
| `Esc` | back to the galaxy |

**Focus** picks a single empire or federation. Choosing a federation dims the rest of the
galaxy and draws the member realms, their links and the bloc's extent.

**Linking to a system.** Entering a system writes `#s=<id>` to the address bar, so the URL
can be shared and opens straight into that system. A name works too:
`#s=Quentii%20Habitation%20Zone`.

## Data

Everything comes from the save itself, embedded in the page as two JSON blocks:

- System ownership is read from starbases, not planet owners.
- Capitals are each country's own seat of government, resolved through its colony id.
- Populations are mapped through colony ids to the correct planet.
- Moons carry their parent body, and asteroids are rolled into per-system belts.
- Empire borders are the Voronoi cells of the owned stars, merged per empire, so
  neighbours share an exact midline rather than overlapping.

Empires that hold no territory — the nomadic and wandering powers — are left out of the
empire menu, since there is nothing on the chart to point at.
