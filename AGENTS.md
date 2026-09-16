# AGENTS.md — Engineering Guardrails

These guardrails are inherited by every agent and contributor working on this
repository. Read them before making any change. The identical guidance lives in
`CLAUDE.md`.

## What this project is

- A plain static site. No framework, no bundler, no build step.
- The entire layout is `index.html` plus the `/assets` directory.
- The site is the untouched v24 Krishna Companion prototype imported from a
  claude.ai artifact.

## Priorities (strict order)

Correct, then simple, then maintainable. Do not trade a lower priority for a
higher one.

## Fidelity contract — preserve pixel and behavior identity with artifact v24

Do not redesign. The following behaviors must remain identical to v24:

- Intro hands and dissolve.
- Cursor-lit drifting grid.
- Six figures and the figure picker.
- Warrior darshan loop.
- WhatsApp header CTA, plus the popup that appears 5 seconds after the intro,
  shown once per visitor.
- Install guide.
- Sound-toggle stub.

## Copy and typography

- Typography is Inter.
- No em dashes anywhere in copy.
- Preserve the Apple-like glass components.
- Existing copy stays unchanged except for approved queued content changes.

## Accessibility

- Keep existing aria labels.
- Give every new link an explicit aria label.

## Planned future tasks (not part of the bootstrap)

- Split inline image data URIs into real files under `/assets` during the later
  extraction task.
- Vendor ThreeJS r128 locally under `/assets/vendor/` with a content-hashed
  filename during the later extraction task; retain the existing timeout/bail
  behavior.
- `vercel.json` will later configure caching for assets and no-cache for
  `index.html`.

## Repository layout

```
.
├── index.html          # the entire page
├── assets/             # images, animation frames, inline JSON, media
├── .gitignore
├── AGENTS.md           # these guardrails
├── CLAUDE.md           # identical guardrails
└── README.md
```

## Local preview and deploy

- Static preview: `python3 -m http.server 8000`, then open
  `http://localhost:8000`.
- Deploy preview: `vercel deploy --yes`.
- Never run `vercel --prod` without owner (Deep) approval.

## Branching and pull requests

- Every later outcome uses its own branch and a pull request into `main`.
- No force pushes.
- During the production-v1 run the orchestrator may merge audited PRs; afterward
  Deep merges.
