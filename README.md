# Clear

```
        .-""""-.
      /  o    o  \        a face,
     |      ∪      |       waiting
      \  ________  /        to be drawn
       '-.______.-'
         |      |
        /|      |\
       ' |      | `
```

The starting foundation for a ReSelf avatar — a procedural, animatable face that can express itself without depending on hand-drawn art.

## What it is

`clear` is an early-stage repo: right now it **is** the open-source [Bible Strong Avatar Lab](https://github.com/smontlouis/bible-strong-avatar-lab) codebase, imported wholesale as the base to build a ReSelf-specific avatar on top of. Nothing in `src/` has diverged from the upstream project yet — this repo is the jumping-off point, not a finished product.

Bible Strong Avatar Lab itself is a browser-based studio for building procedural, SVG-rendered avatars: construct a body from 3D-inspired primitives, define a neutral face, author expressions, compose them into timed animations, and export the result as a portable `.avatar.json` definition usable from React or framework-free JavaScript. It was built by Stéphane Montlouis-Calixte and is licensed AGPL-3.0; see `LICENSE` and [the upstream repo](https://github.com/smontlouis/bible-strong-avatar-lab) for the original project and its full documentation.

## Why it's here

ReSelf needs an avatar that can carry expression and personality procedurally — no sprite sheets, no hand-animated states — and this studio already solves that problem generally: body geometry, expressions, animation timelines, and clean export formats for both React and plain JS. Starting from it rather than from scratch means the geometry, playback, and export pipeline arrive already built and tested; what's left is shaping it into ReSelf's own character.

## Current state

Unmodified foundation. The Studio UI, the avatar/expression/animation data model, the React and JS export packages, the standalone engine generator, and the test suite are all exactly as imported. Treat this repo as a checkpoint to build from, not as ReSelf's shipped avatar yet.

## Stack

React 19, TypeScript (strict), Vite 8, Motion for frame-by-frame playback, SVG for rendering, Tailwind CSS 4 for the Studio UI, Vitest for tests, pnpm workspaces for the `avatar-core` / `avatar-react` / `avatar-web` packages.

## Run locally

Requires Node.js 22.12+ and pnpm 10.34.

```bash
pnpm install
pnpm dev
```

Open the local URL Vite prints (defaults to `http://localhost:5173`).

Other commands:

```bash
pnpm typecheck   # TypeScript, strict, no-emit
pnpm test        # Vitest suite
pnpm build        # regenerate the engine + production build
pnpm check        # engine freshness, format, typecheck, tests, build — the full local gate
```

## Map

```
src/features/avatar/        body geometry, neutral appearance, expressions
src/features/animation/     timeline playback, framework-independent
src/features/rendering/     SVG scene + canvas preview
src/features/export/        .avatar.json, React/JS packages, standalone engine
src/features/studio/        the Studio controller and composed UI
packages/avatar-core/       framework-independent runtime (validation, playback, geometry)
packages/avatar-react/      React renderer, depends on avatar-core
packages/avatar-web/        DOM renderer without React, depends on avatar-core
legacy/                     self-contained HTML prototypes that preceded the React app
docs/adr/                   accepted architecture decisions
CONTEXT.md                  domain vocabulary and invariants for the data model
```

## License

AGPL-3.0, inherited from the upstream project. See `LICENSE`.
