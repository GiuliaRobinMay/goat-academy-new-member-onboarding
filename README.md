# GOAT Academy — New Member Onboarding

A single-file interactive onboarding app for new GOAT Academy members. It combines
the "best of both worlds" the academy asked for:

1. **Your first steps** — an 8-step checklist trail (set up → money-back
   guarantee rules → meet your Student Success Manager & community tour →
   watch all Academy Modules → book an assessment call → start the FastTrack
   Roadmap → join your first live class → plug into the community). Checkboxes
   persist per device, with a progress bar and a small celebration at 100%.
   The guarantee tasks are highlighted as REQUIRED, and the SSM step links to
   each team member's "Meet …" post plus the daily Live Onboarding Q&A.
2. **Know your way around** — a new-member orientation of the spaces beyond
   the Start Here steps (Coaching & Support, Community Channels, Felix's
   Resources) as flip cards: tap a card to reveal what the space is for, when
   to use it, and a direct link. Opened spaces get marked "Explored". Cards
   glow neon teal on hover.

The design matches the GOAT Academy Trading Roadmap app: green→teal→blue
gradient band, deep-blue uppercase display type, mint "From Felix & the team"
welcome card, uppercase tabs, a sticky "Next up" + "Your progress" sidebar,
a lime progress pill, and a circular light/dark/auto theme toggle (top
right, persisted per device). Interactive elements keep the neon teal hover
glow.

## Files

- `index.html` — the whole app. No build step, no external dependencies,
  works offline, supports light and dark mode.

## How progress is saved

Progress is stored in the browser's `localStorage` under the key
`goat-onboarding-v1` (task checkboxes + explored spaces); the theme choice is
stored under `goat-theme`. Both are per device / per browser. "Reset my
progress" in the footer clears the progress (the theme choice stays).

## Editing the content

Everything editable lives in three plain data blocks near the top of the
`<script>` in `index.html`:

- `SPACE_URL` / `GUARANTEE_URL` — the real space and post URLs
  (friends.goatacademy.org).
- `TEAM` — the Student Success team names and their "Meet …" post links.
- `STEPS` — the eight steps: title, time estimate, "why" text, tasks
  (`important: true` renders the gold REQUIRED treatment), link chips.
- `GROUPS` — the orientation flip cards: groups, space names, descriptions,
  emoji.

Change the text there; the page renders itself from that data.

## Using it in the community

Host `index.html` anywhere (GitHub Pages, Netlify, any static host) and embed
it in a Circle space via an iframe / custom HTML block, or link to it directly
from the "Step 1: Welcome & Set Up" space. All space links open in a new tab,
so it works fine inside an iframe.
