# Opus — A Trusted Marketplace for Live Musicians

An interactive prototype for Opus, a mobile app that helps musicians discover, secure,
manage, and get paid for live performance opportunities — combining professional profiles,
ensemble booking, and trust-through-network features in one place.

This repo contains a self-contained, front-end-only HTML/CSS/JS prototype (no build step,
no dependencies) meant as a living design artifact you can keep iterating on, separate from
the case study write-up on your portfolio.

## Running it locally

No install required — it's a single static file.

1. Clone this repo.
2. Open `index.html` directly in a browser, **or** serve it locally so relative paths and
   fonts behave exactly like they would on the web:
   ```bash
   python3 -m http.server 8000
   # then visit http://localhost:8000
   ```

## Deploying it (free, via GitHub Pages)

1. Create a new repo on GitHub (e.g. `opus-app`).
2. Push these files to it:
   ```bash
   git init
   git add .
   git commit -m "Initial Opus prototype"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/opus-app.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**, set Source to **Deploy from a branch**,
   branch **main**, folder **/ (root)**, then Save.
4. Your prototype will be live at `https://YOUR-USERNAME.github.io/opus-app/`.

## What's in the prototype right now

- **Discover** — a matched gig feed with filters and mutual-connection trust signals.
- **Gig Detail** — full posting info, "why this feels safe" network context, and an apply flow.
- **Network** — your ensembles (Mezza Quartet, Grieg Duo — both tap through to full
  ensemble profiles with member rosters), mutual connections, and recommendations.
- **Ensemble profiles** — bio, availability, media, and a clickable member list; each member
  has their own bio page with a back arrow to the ensemble.
- **Messages** — a thread list and one live conversation thread with system status messages
  (applied, hired, payment pending).
- **Profile** — your own bio, genres, an editable "Available For" chip list (weddings,
  funerals, corporate events, etc. — click to toggle, "+ More" reveals additional options),
  media, linked ensembles, and reviews. "Share profile" opens a share sheet (Text / Email /
  Copy Link — currently visual only, no real send).
- **Settings** — reached via the gear icon on your Profile screen. Lists every profile tied
  to your phone number (with a one-tap switcher), plus placeholder rows for payment,
  notifications, privacy, and help.
- **New Profile wizard** — "New Profile" in Settings (or the "+" avatar in the profile
  switcher strip) launches a full-screen, 10-step onboarding flow: phone number → 6-digit
  verification code → name & instrument → experience & location → genres → availability →
  typical rate → bio → optional photo → review → confirmation. Finishing the flow generates
  a brand-new profile object (with correct empty states for a musician who has no gigs,
  reviews, ensembles, or media yet) and switches you into it. You can flip between profiles
  anytime from the avatar strip at the top of Profile, or from Settings.

Navigation keeps a lightweight history stack (`navHistory` in the `<script>` at the bottom
of `index.html`), so back arrows always return to wherever you actually came from, even
across ensemble → member → back chains. The Profile screen itself is now data-driven — it's
rendered from a `profiles` array via `renderActiveProfile()`, so any profile (seeded or
wizard-created) reuses the exact same layout and empty states.

## Where this could go next

Straight from the case study's own "if I continued developing Opus" list:

- **Built-in payment processing** — Stripe Connect is the standard choice for marketplace
  apps with multiple payees (organizer pays, musicians get split payouts).
- **Real phone verification** — the wizard's OTP step is currently a visual mock (any
  6 digits pass); a real build would wire this to Twilio Verify or similar.
- **Verified professional references** — a lightweight endorsement/verification flow between
  users who've actually worked together.
- **Calendar sync** — read/write integration with Google Calendar and Apple Calendar (iCal)
  so accepted gigs show up automatically.
- **Contract generation** — auto-filled, e-signable gig agreements from the posting details.
- **AI-powered musician recommendations** — matching organizers to musicians based on
  instrument, genre, availability, and network trust signals.
- **Reputation scoring** — a computed score from completed gigs, reviews, and response time,
  surfaced instead of (or alongside) the simple star rating currently shown.

### If you want to turn this into a real, data-backed app

The current file is intentionally framework-free so it's easy to read and modify by hand.
When you're ready to add real accounts, a real database, and real screens instead of
hard-coded mock content, reasonable next steps (not implemented here) would be:

- **Frontend**: migrate the screens into React (or React Native/Expo if you want an actual
  installable mobile app rather than a mobile web page).
- **Backend/data**: Supabase or Firebase are both good fits for a fast solo build — they
  give you auth, a database, and file storage without standing up your own server.
- **Design system**: the current CSS custom properties at the top of `index.html`
  (`--ink`, `--parchment`, `--brass`, `--crimson`, `--sage`, etc.) are already effectively a
  design token file — carry those over as-is into whatever framework you pick.

## License / attribution

Personal project by Cassandra May. No affiliation with any real musician booking platform.
