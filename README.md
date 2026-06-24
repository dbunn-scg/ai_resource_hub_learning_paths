# Stockbridge AI Learning Path Finder

A static GitHub Pages site that helps Stockbridge employees find free AI training matched to their role, experience level, and tool focus.

**Stack:** Pure HTML + CSS + JavaScript. No build step, no backend, no dependencies. Works offline.

---

## How to add or update a resource

Edit `courses.js`. Each resource is an object in the `window.COURSES` array.

Copy this template and fill in the fields:

```js
{
  id: "unique-kebab-case-id",
  title: "Full Resource Title",
  provider: "Platform or Organization Name",
  url: "https://direct-link-to-resource",
  description: "One sentence: what the learner will be able to DO after this resource.",
  levels: ["beginner"],              // see Level values below
  roles: ["all"],                    // see Role slugs below
  tools: ["copilot"],                // see Tool values below
  time: "quick",                     // see Time values below
  duration: "45 min",                // human-readable string
  format: "course",                  // see Format values below
  free: true,
  licenseNote: "",                   // optional: note about access or license requirements
  pathPosition: null,                // 1–4 if part of a suggested path sequence, else null
  pathGroup: "",                     // path group ID (e.g. "copilot-beginner"), else ""
},
```

---

## Field reference

### `levels` — array, one or more of:
| Value | Shown as |
|-------|----------|
| `"beginner"` | ● Beginner (gold dot) |
| `"intermediate"` | ● Intermediate (blue dot) |
| `"advanced"` | ● Advanced (red dot) |

### `roles` — array, one or more of:
| Slug | Filter label | Departments |
|------|-------------|-------------|
| `"investment"` | Investment & Asset Mgmt | Asset Management, Portfolio Management, Acquisitions, Capital Markets, Strategic Legacy Assets, Alternative Investment Strategies |
| `"finance-accounting"` | Finance & Accounting | Client Finance & Accounting, Corporate Accounting, Corporate Finance |
| `"client-wealth"` | Client & Wealth Services | Private Wealth, Client Service & Product Solutions, Sales & Capital Formation |
| `"ops-admin"` | Operations & Admin | Administration, Operations & Sustainability, Information Technology |
| `"strategy-compliance"` | Strategy & Compliance | Investment Strategy & Research, Compliance & Controls, Executive Management |
| `"people-comms"` | People & HR | People Team |
| `"all"` | All roles | Everyone |

A resource can be tagged for multiple roles, e.g. `roles: ["investment", "finance-accounting"]`.

### `tools` — array, one or more of:
| Value | Card accent color |
|-------|------------------|
| `"copilot"` | Steel blue (#5591B5) |
| `"chatgpt"` | Emerald (#498C6D) |
| `"claude"` | Plum (#8C4A82) |
| `"all"` | Aegean (#2F4157) |

### `time`:
| Value | Meaning |
|-------|---------|
| `"quick"` | Under 2 hours |
| `"half-day"` | 2–4 hours |
| `"multi-day"` | More than half a day |

### `format` — drives the badge on the card:
| Value | Badge |
|-------|-------|
| `"course"` | Course (sky blue) |
| `"learning-path"` | Learning Path (sky blue) |
| `"video"` | ▶ Video (red) |
| `"github-repo"` | GitHub (dark) |
| `"guide"` | Guide (sky blue) |

### Suggested paths (`pathPosition` + `pathGroup`)
If a resource belongs to a curated learning sequence, set `pathPosition` (1–4) and `pathGroup` (a shared string ID). When at least 2 resources in the same `pathGroup` survive the active filters, a "Suggested Learning Path" strip appears above the card grid showing the sequence in order.

Current path group IDs:
- `"copilot-beginner"` — 3-step Copilot onboarding (all roles)
- `"investment-copilot"` — Copilot for investment & finance roles
- `"investment-deep-dive"` — CRE financial modeling with AI (YouTube + A.CRE)
- `"chatgpt-beginner"` — OpenAI Academy 3-course progression
- `"claude-beginner"` — Claude 101 → Claude for Work
- `"ai-foundations"` — Vendor-neutral AI foundations (DeepLearning.AI)
- `"copilot-intermediate"` — Full 10-module Copilot use-case path

---

## GitHub Pages setup

1. Push this repo to the Stockbridge GitHub org as a **public** repository
2. Go to **Settings → Pages**
3. Source: **Deploy from branch → `main` → `/` (root)**
4. Click Save — site will be live at `https://<org>.github.io/<repo-name>/`

**Custom domain (optional):** To serve from `ai.stockbridge.com`, create a file named `CNAME` in the repo root containing just the domain name:
```
ai.stockbridge.com
```
Then configure the DNS CNAME record to point to `<org>.github.io`.

---

## Local preview

Open `index.html` directly in your browser — no server required.

---

## File structure

```
ai_resource_hub_learning_paths/
├── index.html    ← Application (HTML + CSS + JS, self-contained)
├── courses.js    ← Resource data — the only file you need to edit
└── README.md     ← This file
```
