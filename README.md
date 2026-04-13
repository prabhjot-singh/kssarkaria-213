# 213, 16A — *A House of Mathematics*

An interactive companion to K.S. Sarkaria's paper [*"213, 16A" and Mathematics*](https://kssarkaria.org/docs/213.pdf) (2010).

The paper is a guided tour through the author's house at 213, 16A in Chandigarh, in which each architectural feature embodies a piece of mathematics — the golden rectangle in the front-door mural, an icosahedron as three interlocking golden rectangles in the water pond, the five regular solids via the rooftop pyramid, Euler's *V − E + F* on the office-window painting, a driveway whose red bricks spell out `11010101` — the binary for 213 — and more.

This site rebuilds the tour as an interactive experience at [**213.kssarkaria.org**](https://213.kssarkaria.org).

## What's here

Ten pages. Every word his, every photo his.

| Page | Section | Interactive |
|------|---------|-------------|
| `index.html` | The tour map | 10 clickable stops |
| `mural.html` | §1 Perfectly proportioned | Click to delete squares, watch the golden spiral form; live length-to-breadth readout |
| `beesmukhi.html` | §2 Beesmukhi | 3D icosahedron built from three golden rectangles — drag to rotate, slide to explode |
| `pyramid.html` | §3 Pyramid | Variable pyramid with apex-height slider; (p−2)(q−2) < 4 grid showing the five Platonic solids |
| `eyes.html` | §4 Miss Universe | Click to subdivide faces/edges — *V − E + F* stays at 2 forever. Torus-vs-Klein-bottle glueing toy |
| `intermission.html` | Over a cuppa | His philosophy-of-mathematics passages |
| `fourhalfturns.html` | §5 Four half-turns | Drag a quadrilateral — any quadrilateral tiles the plane by half-turns at edge midpoints |
| `grecianorigami.html` | §6 Grecian origami | Two (a+b)² squares side-by-side — one with c² in the middle, the other with a² + b² in the corners |
| `amazingcurves.html` | §7 Amazing curves | The binary-213 bit-flipper: click any bit, watch the decimal change |
| `magiccarpet.html` | §8 Magic Carpet | Curved pentagon with curvature slider; iterated reflections tile the Poincaré halo |
| `tailpiece.html` | bing's ome | Bing's house with two rooms, a rotating Möbius strip, and the closing story |

## Stack

- Plain HTML + CSS + hand-rolled JavaScript. No frameworks, no build step, no package.json.
- No external asset loads — fonts are system serifs (Iowan Old Style, Palatino, Georgia). Works offline.
- All photographs extracted from the original PDF and served locally from `/assets/photos/`.
- All 3D geometry hand-rolled with simple SVG + back-to-front painting — no three.js, no WebGL.

## Development

Just open any HTML file in a browser. To preview the whole site locally:

```
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deployment

See [`DEPLOYMENT.md`](DEPLOYMENT.md) for the Cloudflare Pages + GoDaddy DNS setup for the `213.kssarkaria.org` subdomain.

## Credits

Interactive version by Prabhjot Singh, 2026. Paper and photographs © K.S. Sarkaria.

## License

Code is released under the [MIT License](LICENSE). Paper text and photographs are © K.S. Sarkaria and are included with permission; they are not covered by the MIT license and may not be reused without his permission.
