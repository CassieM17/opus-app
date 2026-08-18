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

- **Discover** — a searchable feed of 9 live opportunities (up from 4), every one of them
  clickable into a full Gig Detail page. A search bar sits at the top with a filter button
  beside it (opens a full-screen popup for narrowing results by instrument, number of players,
  and location); below that, an **In-Network / Public** toggle switches the whole feed between
  opportunities surfaced through your connections (with mutual-connection trust signals) and
  the general public board. Each card has a bookmark icon in the corner to save it for later
  without opening it. Tapping "Apply" on a gig posts an application straight away (no messaging
  step) and confirms with a native-style alert naming the actual organizer for that gig.
- **Gig Detail** — fully data-driven now, so every one of the 9 opportunities has its own real
  posting info (instruments needed, dress code, repertoire, performance length, parking,
  payment), a "why this feels safe" network-trust section when the gig has one, rate and apply
  deadline, an Apply button labeled for the right applicant (an ensemble like "Mezza Quartet"
  or "Grieg Duo" when the gig calls for one, otherwise your own name), and a "Save for later"
  button that mirrors the bookmark on the card.
- **Events** — its own tab between Discover and My Network. An "Organize an Event" row at the
  top opens the Organize Event form. Below it, **Events You're Organizing** lists your posted
  events with a check mark or an X next to each title — check means musicians are confirmed,
  X means it's still open — and a "past" count that's clickable and opens a dedicated Past
  Events screen showing who performed at each one. Tapping into any organized event shows
  either its confirmed musicians, its list of applicants (if nobody's confirmed yet), or who
  performed (if it already happened) — tapping any of those people opens their profile, gated
  by the same network rule as everywhere else. Below that, a **My Events** section lists gigs
  you're booked to perform at, and a **Saved** section lists opportunities you bookmarked on
  Discover to consider later, each removable with a small X.
- **Organize Event** — opens as a full-screen popup modal over whatever screen you're on (the
  "Organize an Event" row at the top of the Events tab is the only entry point now — the
  duplicate pill button that used to sit on the Profile screen has been removed) — it slides up
  like a native sheet rather than navigating you to a new page, and can be dismissed with the
  X, by tapping outside it, or by posting the event. The form covers title, location, date
  &amp; time, type of gig (wedding, funeral, corporate event, recital, religious service,
  fundraiser, private party, other), desired musicians/instruments (multi-select), compensation
  expectations, and an optional notes box at the bottom for anything else musicians should
  know. Posting adds it to the Events tab and your profile's Events Organized section (as an
  unconfirmed, X-marked event with no applicants yet), and takes you to the Events tab to see
  it.
- **My Network** — a search bar up top lets you look up anyone by name or phone number
  against a small mock directory (typing hides the two sections below and shows live results;
  tapping a result opens that person's profile). Below the search bar, a **Connections**
  section lists your closest connections with a clickable "X total" label that opens a full
  scrolling list of everyone in your network — every connection row is clickable into a profile
  page. Below that, an **Ensembles** section shows the ensembles you're a part of (Mezza
  Quartet, Grieg Duo — both tap through to full ensemble profiles with member rosters), with
  its own "+ Create/Join" link.
- **Person profiles, gated by network status** — clicking anyone who isn't one of the four
  featured Mezza Quartet / Grieg Duo members (a network search result, a connection from the
  full list, or an applicant/confirmed musician on one of your organized events) opens a
  profile screen built from the same rule everywhere: the top half — photo, name, tagline — and
  a Contact card with email and phone are always visible, because contact info is public for
  everyone on Opus. Biography, genres, and reviews stay locked behind a "Connect to see more"
  panel until that person is actually in your network, at which point the full profile unlocks
  in place. The locked panel has its own "+ Add to Network" button, so you can send a connect
  request straight from a stranger's profile — useful for sizing someone up before confirming
  them for a gig you organized. Once connected, revisiting that profile (from anywhere) shows
  the full version automatically.
- **Ensemble profiles** — bio, availability, media, and a clickable member list; each seeded
  member has their own bio page with a back arrow to the ensemble.
- **Create/Join Ensemble** — a "+ Create/Join" link on the Ensembles section (on both the
  My Network screen and the Profile screen) opens a full-screen popup with two tabs. **Create
  New** builds a brand-new ensemble from a name, type (string quartet, duo, band, choir,
  etc.), genres, and a bio — you're added as its first member, no approval needed since you're
  the founder. **Join Existing** searches a small mock directory of other Pittsburgh-area
  ensembles (by name or type). Tapping "Join" doesn't add you right away — it sends a request
  that every current member of that ensemble has to confirm. A live pill on the result row
  ("1/4 confirmed," "2/4 confirmed," …) ticks up as each member responds, simulated with
  staggered delays so it reads like real people weighing in one at a time. You're only added
  once every member has confirmed; if even one member declines, the request is denied outright
  (regardless of how many already said yes) and you're notified who declined — the pill resets
  and you're free to try again. Either way, once you're in, the ensemble immediately shows up
  on both the Profile and My Network screens and gets its own detail page (bio, media, member
  list) — the two seeded ensembles (Mezza Quartet, Grieg Duo) keep their existing dedicated
  pages, while every created/joined ensemble shares one data-driven detail screen.
- **Profile** — a "Contact" pill in the top-left corner of the header opens a small popover
  card with your email and phone number (tap the pill again or tap anywhere else to close it).
  Below the header: your own bio, genres, an editable "Available For" chip list (weddings,
  funerals, corporate events, etc. — click to toggle, "+ More" reveals additional options),
  media (with a "+ Add" button to add a new recording/reel with a caption), linked ensembles,
  an **Events Organized** section (tap through to a full list, then into any event's detail
  view — this mirrors what's on the Events tab), and reviews. "Share profile" opens a share
  sheet (Text / Email / Copy Link — currently visual only, no real send).
- **Settings** — reached via the gear icon on your Profile screen. Lists every profile tied
  to your phone number (with a one-tap switcher and a delete icon on each row — deleting is
  blocked with an explanatory alert if it's your only remaining profile), plus placeholder
  rows for payment, notifications, privacy, and help.
- **New Profile wizard** — "New Profile" in Settings (or the "+" avatar in the profile
  switcher strip) launches a full-screen, 10-step onboarding flow: phone number → 6-digit
  verification code → name & instrument(s) → experience & location → genres → availability →
  typical rate → bio → optional photo → review → confirmation. The instrument step supports
  picking more than one instrument, or toggling "I don't play an instrument — I'm an event
  organizer" to skip instruments entirely and register as an organizer instead. Finishing the
  flow generates a brand-new profile object (with correct empty states for a musician who has
  no gigs, reviews, ensembles, or media yet) and switches you into it. You can flip between
  profiles anytime from the avatar strip at the top of Profile, or from Settings.
- **Edit Profile** — "Edit profile" on the Profile screen opens a form (prefilled with the
  active profile's current data) covering name, instrument(s) or event-organizer status,
  experience, location, credential, genres, availability, rate, bio, and photo. Saving
  re-renders the profile from the same `profiles` data model the wizard writes to.
- **Connections, expanded** — the "X total" label next to Connections on the My Network
  screen is clickable and takes you to a full scrolling list of everyone in your network
  (seeded with the four ensemble co-members plus sixteen additional mock connections, growing
  as you add people via the search bar at the top of My Network).
- **Write a recommendation** — every connection row (in the My Network screen's preview list,
  the full connections list, and on each of the four ensemble members' own bio pages) has a
  small pencil-icon button that opens a recommendation composer. Posting a recommendation for
  Josh, Nathan, Elly, or Spencer appends it to a live Reviews section on their bio page,
  replacing the empty "No reviews yet" state. Each musician's bio page has a single "Share
  profile" button (no messaging).

Navigation keeps a lightweight history stack (`navHistory` in the `<script>` at the bottom
of `index.html`), so back arrows always return to wherever you actually came from, even
across ensemble → member → back chains. The Profile screen itself is now data-driven — it's
rendered from a `profiles` array via `renderActiveProfile()`, so any profile (seeded,
wizard-created, or edited) reuses the exact same layout and empty states. Network data lives
in a `CONNECTIONS` / `DIRECTORY` pair of arrays — both enriched with `instrument`, `location`,
`years`, `context`, and `phone` so any entry can render a real profile — feeding an inline
search (`renderNetworkSearch()`) that swaps the My Network screen between its normal
Connections/Ensembles view and live, clickable search results as you type. A generic
`showAlert()` modal (styled like a native iOS alert) is reused for every confirm/deny and
delete-confirmation moment in the app. The Discover feed is likewise data-driven from a
9-entry `GIGS` array (each tagged with a `scope` of `network` or `public`, `instruments`,
`numPlayers`, `location`, and a full `postedBy`/repertoire/dress-code/etc. detail set) rendered
by `renderDiscoverFeed()` and `gigCardHtml()`, filtered live against the search bar, the
In-Network/Public toggle (`setDiscoverScope()`), and whatever's set in the filter popup
(`discoverFilters`, applied via `applyDiscoverFilters()`); `openGigDetail()` / `renderGigDetail()`
populate the single data-driven Gig Detail screen for whichever card was tapped. Each profile
carries `savedGigIds` (toggled from either the card's bookmark icon or the detail screen's
"Save for later" button via `toggleSaveGig()`) feeding the Events tab's Saved section, an
`eventsOrganized` array (fed by the Organize Event form, each with a `status` of `upcoming` or
`past`, a `confirmed` list, an `applicants` list, and — once past — an `attendees` list) and a
`bookedGigs` array for gigs you're confirmed to perform at. `eventIsConfirmed()` and
`confirmMarkHtml()` compute the check/X shown next to each organized event's title, and
`renderEventDetail()` shows whichever of confirmed/applicants/attendees applies. Every person
in those lists, plus every non-featured connection and directory result, routes through the
same generic `openPersonProfile()` / `renderPersonProfile()` pair: `personIsConnected()` checks
`CONNECTIONS` by name to decide whether the full bio/genres/reviews block renders or the
locked panel does, while the Contact card (email via `personEmail()`, phone) always renders
regardless, since contact info is public for everyone. `requestAddPerson()` lets a locked
profile's "+ Add to Network" button push that person into `CONNECTIONS` and re-render in
place. Ensembles follow their own version of the same pattern: each profile's `ensembles`
array feeds both the My Network screen's cards (`renderNetworkEnsembles()`) and the Profile
screen's list, a shared `ensembleCardHtml()` renders the card markup either place, and every
created/joined ensemble (as opposed to the two seeded ones) opens the generic
`screen-ensemble-detail` populated by `renderEnsembleDetail()`.

## Mobile scaling

On a real phone (any viewport 520px wide or narrower), the app drops the decorative "phone
mockup in a frame" chrome entirely — no border, corner radius, drop shadow, or the 80% scale
transform — and stretches `.phone` to fill the full viewport (`100vw` / `100dvh`), so opening
the deployed `index.html` on your phone feels like a real installed app rather than a small
mockup floating on a dark background. The status bar and bottom nav bar pad themselves out
using `env(safe-area-inset-top/bottom)` so they sit correctly around a device's notch and
home indicator (this requires the `viewport-fit=cover` viewport meta tag, which is already
set). On desktop/tablet widths, the original framed 80%-scale mockup presentation is
unchanged.

## A note on `index.html` vs `opus-prototype.html`

`index.html` is the standalone build meant for deploying on its own (e.g. GitHub Pages) —
on desktop/tablet widths it's rendered at 80% scale (`transform:scale(0.8)` on `.phone`) so
the phone frame doesn't dominate a full browser tab (see "Mobile scaling" above for what
happens on an actual phone). `opus-prototype.html` is the same app always at 100% scale
(no mobile/desktop distinction), sized for embedding in an `<iframe>` inside the portfolio
case study page. Keep both in sync when you make changes — the only intentional differences
are the `<title>`, the studio label text, and that one `transform` rule.

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
