# GOAT Academy — New Member Onboarding

A single-file interactive onboarding app for new GOAT Academy members. It combines
the "best of both worlds" the academy asked for:

1. **Your first steps** — a 6-step checklist trail (set up → watch all Academy
   Modules → book an assessment call → start the FastTrack Roadmap → join your
   first live class → plug into the community). Checkboxes persist per device,
   with a progress bar and a small celebration at 100%.
2. **Know your way around** — a new-member orientation: every sidebar space
   (Start Here, Coaching & Support, Community Channels, Felix's Resources) with
   what it is, when to use it, and a direct link. Opened spaces get marked
   "Explored".

## Files

- `index.html` — the whole app. No build step, no external dependencies,
  works offline, supports light and dark mode.

## How progress is saved

Progress is stored in the browser's `localStorage` under the key
`goat-onboarding-v1` (task checkboxes + explored spaces). It is per device /
per browser. "Reset my progress" in the footer clears it.

## Editing the content

Everything editable lives in three plain data blocks near the top of the
`<script>` in `index.html`:

- `SPACE_URL` — the real space URLs (friends.goatacademy.org space IDs).
- `STEPS` — the six steps: title, time estimate, "why" text, tasks, link chips.
- `GROUPS` — the orientation map: groups, space names, descriptions, emoji.

Change the text there; the page renders itself from that data.

## Using it in the community

Host `index.html` anywhere (GitHub Pages, Netlify, any static host) and embed
it in a Circle space via an iframe / custom HTML block, or link to it directly
from the "Step 1: Welcome & Set Up" space. All space links open in a new tab,
so it works fine inside an iframe.
