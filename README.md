# Bernard Dzekashu — Portfolio (v2)

Single-page portfolio site framing self-hosted infrastructure as an enterprise simulation lab. Plain HTML/CSS, no build step, no JavaScript dependencies.

## Files

- `index.html` — the site (one file, inline styles, ~40 KB)
- `cv.pdf` — downloadable CV
- `fonts/` — self-hosted Space Grotesk + DM Sans + monospace fallback chain

## Sections (in order)

1. Hero
2. About
3. **Self-Hosted Infrastructure & Enterprise Simulation Lab** — 6 layer cards + ASCII architecture diagram
4. Experience (jobs)
5. **Projects & Case Studies** — 8 cards in Problem → Solution → Stack → Outcome format
6. **Homelab → Enterprise Skills Mapping** — the recruiter-facing translation table
7. Certifications
8. **Ecosystem & Lessons** — RootedInTech, ZeksMedia, and a placeholder for failure stories
9. Contact

## Placeholders to fill in before publishing

These are the things I would not invent for you. Search and replace in `index.html`:

| Token / location | What to replace with |
|---|---|
| `id="link-rooted"` `href="#"` | Real RootedInTech blog URL |
| `id="link-zeks"` `href="#"` | Real ZeksMedia URL (or remove the card if private) |
| ASCII diagram VLAN labels (`TRUSTED · SERVICES · IoT · GUEST · MGMT`) | Your actual VLAN names if different |
| Update Monitoring Tool — PRJ_007 stack | Real tool name + tech stack once finalized |
| Lessons Learned placeholder card | 2–3 real failure-and-fix stories (Ceph, networking, Docker, etc.) |

Tip: use VS Code's global search (Ctrl+Shift+F) for any `href="#"` and the literal token `[ TO BE FILLED ]` to find all spots.

## What I did NOT invent

- I described your Proxmox cluster as multi-node with HA + Ceph (you confirmed). I did not invent specific node counts, RAM, or hostnames.
- I described your network as "5-VLAN segmentation" with example purposes (TRUSTED, SERVICES, IoT, GUEST, MGMT) in the diagram. **Replace with your actual VLAN names** if you want this to be exact.
- I described ZeksMedia as Plex/Jellyfin + *arr stack + Overseerr behind reverse proxy and SSO. **Confirm or correct the specific tools you actually run.**
- I did not invent any failure stories. The "Lessons Learned" section is intentionally a placeholder.

## View locally

```bash
cd portfolio
python -m http.server 8000
# open http://localhost:8000
```

Local server is required for the `cv.pdf` download to work cleanly (`file://` URLs sometimes block downloads).

## Deploy

### GitHub Pages (recommended)

1. New repo (e.g., `bernard-dzekashu.github.io` for a root domain).
2. Copy `portfolio/` contents into the repo root.
3. Settings → Pages → Source: `main` / root.
4. Live in ~1 minute.

### Netlify drop

1. Go to [netlify.com/drop](https://app.netlify.com/drop).
2. Drag the `portfolio/` folder.
3. Get a `*.netlify.app` URL immediately.

## Roadmap (if you outgrow single-page)

When you have real architecture diagrams (draw.io / Excalidraw exports) and 3+ deep case-study writeups, splitting into multi-page makes sense:

- `/` — current home
- `/infrastructure/` — diagrams + architectural decisions
- `/projects/{slug}/` — full case studies (one page each)
- `/blog/` — links / RSS to RootedInTech

Same HTML/CSS, just split files. Easy migration when ready.
