# Vacuum Window Thickness Calculator

Online calculator for the minimum thickness of an optical window under a uniform
pressure load — vacuum chambers, cryostats and pressure cells.

**https://seankung.ca/Vacuum-Windows/**

Pick a material, choose clamped or unclamped mounting, set a safety factor, and enter
the window geometry and pressure difference. Round and rectangular windows are both
supported, and a reverse check reports the safety factor actually realised by a
thickness you already have in stock.

## Equations

The maximum stress on a uniformly loaded window, held below the apparent elastic limit
`Fa` by a safety factor `SF`:

```
Smax = K·D²·P / (4·T²)          Smax = Fa / SF
```

Solved for thickness:

```
Circular      T = D · √(SF·K/4) · √( P / Fa )
Rectangular   T = L · √(SF·K/2) · √( P / (Fa·(1+R²)) ),   R = L/W
```

The safety factor is a live input rather than a baked-in constant, so this is the
general form and not the pre-simplified `SF = 4` shortcuts. The support constant
follows the mounting choice — the empirical `K = 0.75` clamped, and 50% greater at
`K = 1.125` unclamped.

## Source

Equations, support constants and apparent elastic limits are taken from
*The Design of Pressure Windows*, Crystran Ltd, October 2014.

Five of the six worked examples in that document reproduce exactly. The sixth,
sapphire, does not — and shouldn't: the document's table lists sapphire as
"276 MPa = 45000 psi", but 276 MPa is 40030 psi. Every other material in the table is
self-consistent. This calculator uses **276 MPa**, matching Crystran's own sapphire
datasheet and giving the more conservative (thicker) result, so the printed sapphire
example of 7.7 / 6.3 mm comes out as 8.17 / 6.67 mm here. Enter 45000 psi via the
*Custom…* material option to reproduce the printed figures.

| Worked example | Calculated (unclamped / clamped) | Published |
|---|---|---|
| CaF₂ 50 mm ⌀, 1 atm, SF = 4 | 2.79 / 2.28 mm | 2.8 / 2.3 mm |
| CaF₂ 52 × 20 mm, 1 atm, SF = 4 | 1.48 / 1.20 mm | 1.5 / 1.2 mm |
| KRS-5 40 mm ⌀, 1 atm, SF = 4 | 2.64 / 2.15 mm | 2.6 / 2.2 mm |
| Fused silica 100 mm ⌀, 1000 kPa, SF = 10 | 22.61 / 18.46 mm | 22.6 / 18.5 mm |
| ZnSe 80 mm ⌀, 1 atm, SF = 4 | 3.64 / 2.97 mm | 3.6 / 3.0 mm |
| Sapphire 25 mm ⌀, 3800 psi, SF = 4 | 8.17 / 6.67 mm | 7.7 / 6.3 mm (see above) |

Atmospheric pressure is taken as 101324 Pa, following the same document.

## Caveats

Published elastic limits are not always reliable, crystals vary, and a correctly sized
window can still fail if the mounting introduces localised stress. Clamped constants
assume no flexure at the wall — if the window seats on a soft gasket or O-ring, use the
unclamped figure. Verify any safety-critical design independently.

## Licence

MIT. Single self-contained `index.html`, no build step and no dependencies.
