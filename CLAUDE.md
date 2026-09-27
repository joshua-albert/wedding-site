# Anna & Joshua wedding site: brief for Claude Code

## What this is
Wedding website for Anna & Joshua, June 4-6, 2027 (wedding Sat June 5 at Bok, Philadelphia).
Live domain: annaandjoshuasayido.com (registered at GoDaddy; DNS stays at GoDaddy).
Hosting: GitHub Pages, same setup as Joshua's cowdog.studio site. Hand-written static HTML,
no framework, no build step. Pushing to `main` deploys.

## The design
- `index.html` = "Anna & Joshua 2027" (Draft 2, the bold posters design). Joshua picked this one. This is the site.
- `reference/dinner-club/` and `reference/the-mix/` = other concepts. Reference only. Never deploy them.
- Do not redesign. Keep the look, fonts, animations, and hand-inked disco ball exactly as they are.
  Mobile first: test at 390px wide before anything else.
- The page has a "Draft switch (preview only)" with two color sets: A Plum (default) and B Blue.
  Joshua chose B Blue. Remove the switch buttons and its script, and make B Blue the site's
  permanent colors (move the B values into :root). Keep the A Plum values in the CSS, commented,
  so it could be flipped back with one change.
  Once the switch is gone, the page must not use localStorage at all.

## Rules
- Every RSVP and registry link goes to Zola. Never build an RSVP form or collect guest data here.
- No analytics, no tracking, no cookies.
- Add `<meta name="robots" content="noindex,nofollow">` and a robots.txt that disallows all.
  Guests get the link from the invitation; the site should not show up in Google.
- Never invent facts. Anything not confirmed stays as a visible placeholder `[TBD: ...]`
  and gets listed in LAUNCH-CHECKLIST.md.
- Don't touch DNS or GoDaddy. Joshua does that by hand.
- Explain what you did in plain English, short. Joshua directs and reviews; you do the building.

## Phase 1: repo + preview (do this first)
1. `git init`, add a `.gitignore` (.DS_Store etc.), add `.nojekyll`.
2. Create a PRIVATE GitHub repo named `wedding-site` with `gh` and push to `main`.
   If `gh` isn't installed or logged in, walk Joshua through `brew install gh` and `gh auth login`.
3. Turn on GitHub Pages from `main`, folder `/` (use `gh api`).
   If GitHub refuses because the repo is private (Pages on private repos needs a paid plan),
   STOP and tell Joshua. Options: upgrade to GitHub Pro, or make the repo public. His call.
4. Remove the draft switch (see above) and lock to B Blue.
5. Add: noindex tags + robots.txt, a favicon (a small disco ball), page title and a
   description, and an Open Graph share image (1200x630, made from the hero) so the
   link looks good when texted.
6. Check Google Fonts load and there are no console errors.
7. Write LAUNCH-CHECKLIST.md listing every placeholder and open item.
8. Give Joshua the github.io preview URL. Stop here.

## Phase 2: connect the domain (only after Joshua says the GoDaddy DNS is done)
1. Add a `CNAME` file containing `annaandjoshuasayido.com`, commit, push.
2. Set the custom domain on the Pages site via `gh api`.
3. Run `dig annaandjoshuasayido.com +noall +answer -t A` and
   `dig www.annaandjoshuasayido.com +noall +answer -t CNAME` and report what you see.
   Expected A records: 185.199.108.153, .109.153, .110.153, .111.153.
4. Once GitHub has issued the certificate, turn on Enforce HTTPS. If it isn't ready,
   say so; it can take up to 24 hours.
5. Confirm https://annaandjoshuasayido.com and https://www. both load.

## Phase 3: content (ongoing)
Fill placeholders as Joshua confirms them. Known open items:
- Real Zola wedding-site URL (buttons currently go to zola.com)
- Event times for Fri June 4 / Sat June 5 / Sun June 6
- Caterer: confirm Party Girl = Mallory Valvano's Party Girl (partygirlworldwide.com)
- Hotel options beyond The Deacon
- Ceremony location within Bok
- Anna's approval and the designer's sign-off before the link goes out
