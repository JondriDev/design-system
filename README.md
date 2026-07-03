# XENO · JondriDev Design System

**The Earth seen from orbit, as an interface** — the visual foundation for every
JondriDev app.

JondriDev is an ecosystem of mobile-first apps built by a self-taught Indonesian
developer. Everything shares one account, one cloud, and this single design
system. It is bilingual (EN / ID) and ships both dark and light themes (dark
"Void" is the default).

> 🔭 **Reference implementation:** [**The Empire**](https://jondridev.github.io/empire/)
> — a 27-instrument web super-app that vendors these tokens 1:1 (token *names*
> are the stable contract; these are the canonical *values*). The
> [**Network** tab](#the-living-network) of this showcase links straight into it,
> and the **Home Widgets** section of the Kit documents the tile pattern behind
> The Empire's living home, **The Bridge**.

Two non-negotiables:

1. **Earth-from-Space palette** — a deep-space void with oceanic signals and
   warm planetary accents: shallow-cyan signal, aurora green, atmosphere blue,
   land green, desert sand, cloud white. The dominant feel is oceanic; everything
   else is a warm accent — the planet at night, seen from orbit.
2. **Liquid Glass** — near-zero fills, heavy backdrop blur, white directional
   edges (bright specular top-left, dim bottom-right), and a faint scanline
   texture beneath, as if the surface is being read by something.

## Structure

| File | Purpose |
|---|---|
| `index.html` | The single-page showcase — four tabs (System · Kit · Tokens · Network), language + theme toggles, the full component layer (including the **Home Widget** telemetry tile), a living constellation backdrop. Open it directly in a browser; no build step. |
| `colors_and_type.css` | The reusable foundation: design tokens (palette, glass, spacing, radius, opacity, z-index, motion, layout) + semantic type classes + the `.holo` recipe + local `@font-face`. **Copy this into every app** — The Empire vendors it verbatim. |
| `fonts/` | Sora (weights 100–800, local `.ttf`) + JetBrains Mono (variable `.woff2`, latin + latin-ext) + the SIL Open Font License. Fully local — the system renders identically offline. |

## Palette — Earth from Space

| Token | Role | Hex |
|---|---|---|
| `--signal` | Primary · shallow cyan | `#1A8CAA` |
| `--aurora` | Aurora green · success / life | `#66D9A0` |
| `--ion` | Atmosphere blue · secondary | `#5B8FB9` |
| `--plasma` | Land green · rare decorative accent | `#3C7A4A` |
| `--ember` | Desert sand · warm signal | `#C4A265` |
| `--xenon` | Cloud white · pale luminescence | `#E8EDF2` |
| `--void` | Deep-space backdrop | `#050A14` |
| `--abyss` | Earth-ocean navy · raised surface | `#0B1A2E` |

Backgrounds are multi-stop radial washes over `--void`, never flat color.
Token **names** never change — apps consume `--signal`/`--ion`/… and the whole
ecosystem re-skins by re-valuing this one file.

### App accents

| App | Role | Accent | Hex |
|---|---|---|---|
| **Keuangan** | Finance tracker | Aurora | `#66D9A0` |
| **Kamus** | Dictionary | Signal | `#1A8CAA` |
| **Kosakata** | Vocabulary trainer | Ember | `#C4A265` |
| **Pembaca** | Book reader | City lights | `#F0C94E` |
| **Mesin** | Terminal emulator | Pale atmosphere | `#8FB4D8` |
| **Cakra** | AI agent | Atmosphere | `#5B8FB9` |

## Typography

- **Sora** — everything display, heading, UI, body. Weight **800 is the heaviest
  local cut — never specify 900** (it triggers fake-bold synthesis). 800 for
  display/h1/h2; 700 for h3 / buttons; 500 for inputs; 400 for body.
- **JetBrains Mono** — telemetry, stat values, labels, tokens, glyph data, code,
  eyebrow micro-type. The instrument-readout voice. Vendored locally as a
  variable `.woff2` (latin + latin-ext), no CDN needed.
- Body line-height is `1.75` — generous, for relaxed mobile reading in the dark.

## Liquid Glass recipe

Every surface uses the `.holo` class, driven by `--holo-*` tokens:

1. **Near-zero fill** — the backdrop blur does the work, not opacity.
2. **White directional edges** — bright specular edge top-left, dim edge
   bottom-right; the top specular and bottom dark rim are baked into
   `--holo-shadow`.
3. **Scanline overlay** — a faint repeating-linear-gradient (`--scan`), so the
   glass reads as instrumented.

Navbar / bottom nav use a stronger blur than cards. **Never nest `.holo` inside
`.holo`** — compound glass looks muddy.

## Home Widgets — the Bridge tile

The Kit documents the **living-home telemetry tile** that powers The Empire's
home screen (the Bridge): an eyebrow label + glyph in the app's accent, a big
mono value, one live sub-line, and an optional progress track. Every tile is a
`<button>` — a portal into its owning app, fed by real app state, never by
placeholder copy.

## The living network

The showcase paints a constellation field behind everything — a starfield plus a
drifting node mesh that links up as nodes near each other. The **Network** tab
renders the ecosystem as one literal node-graph: a CORE identity wired to every
app. The interconnection, made visible.

## Accessibility

- **Visible focus.** Interactive controls get a 2px `:focus-visible` signal
  outline. Switches are real `<button role="switch">` with `aria-checked`.
- **`--text3` is decorative only** (eyebrow labels, chevrons) — use
  `--text2` / `--text` for readable prose.
- **Reduced motion** clamps CSS animation/transition to `0.01ms` **and** omits
  the SVG SMIL pulses on the network graph (CSS alone can't stop SMIL).
- **Token snippets keep their units**, so copy-paste examples are valid CSS.

## Voice & copy

Bilingual, confident, compact. Title Case for headings, UPPER CASE + wide
tracking for eyebrow / telemetry labels. Signature punctuation: middle dot `·`
as a connector, `→` after CTAs, em-dash `—` for asides. Emoji and a constructed
geometric **xeno-script** glyph set serve as the icon language. Write every
user-facing string in both EN and ID.

---

_One account. One mesh. Many instruments._
