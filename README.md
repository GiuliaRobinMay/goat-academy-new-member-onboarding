# GOAT Academy — New Member Onboarding

A single-file interactive onboarding app for new GOAT Academy members.

An onboarding checklist of 10 "checkpoints" (set up -> your SSM's welcome
phone call -> Felix's welcome video -> money-back guarantee rules -> join a
live welcome call -> watch all Academy Modules -> take the assessment test ->
start the FastTrack Roadmap -> submit your first weekly report -> plug into
the community). Checkboxes
persist per device, with a progress bar and a small celebration at 100%. The
first incomplete checkpoint carries a highlighted border and advances as
checkpoints complete. The guarantee tasks are marked REQUIRED. There is no
SSM booking step: since Aug 2026 every new student gets a short intro phone
call from their Student Success Manager the day after joining, so the
welcome-call checkpoint mentions that call and links the recurring daily
"Live Q&A for New Students" event page. Three of Felix's videos
(welcome, money-back guarantee, refer someone) are embedded via Google Drive
iframes — the Drive files must stay shared as "anyone with the link can view".
The cards are called "Checkpoints" (not "Steps") to avoid clashing with the
community's "Step 1/2/3" sidebar spaces — the word is the `STEP_LABEL`
constant in the script if you ever want to rename it.

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

## Ideas for next iterations (from Giulia's walkthrough for Vlad)

- **SSM intro call**: each new student now gets a 2-3 min phone call from
  their SSM the day after joining — if that ever becomes bookable again, the
  removed Calendly-card UI lives in git history (commit 617664f).
- **Headless API tracking**: use the community's headless API to see whether a
  member has completed their profile, enabled notifications and downloaded the
  app; notify the team when someone *disables* notifications so we can send a
  gentle nudge ("we noticed notifications are off — keeping them on matters
  for your progress"); follow up on whether the welcome/guarantee videos were
  watched, the rules confirmed, and the SSM call booked.
- **Upcoming-events calendar**: embed a small calendar of upcoming welcome
  calls / classes in the "Join a live welcome call" checkpoint (needs an
  events feed or a direct events-tab URL).
- **Assessment**: the level test is live in the Book an Assessment space;
  the checkpoint sends members there first, with an assessment call as the
  follow-up option for discussing results.
