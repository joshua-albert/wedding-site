# Launch checklist — annaandjoshuasayido.com

Everything on this list is either a placeholder on the page or a fact nobody has
confirmed to me yet. Nothing here is invented; where the page doesn't know
something it says so out loud ("Times are coming soon", "more hotel options
coming soon!") rather than guessing.

Last updated: 2026-09-27 (after the flash-safety pass)

---

## 1. Blockers — the link should not go out until these are done

- [ ] **Real Zola URL.** Every RSVP/registry button currently points at
      `https://www.zola.com/` (the company homepage, not your wedding page).
      There are **6** of them in `index.html`: top bar, hero, RSVP section (RSVP),
      RSVP section (Registry), footer, and they all need swapping.
      Two URLs needed: the RSVP page and the registry page.
- [ ] **Anna's approval** on the copy and the colours.
- [ ] **The designer's sign-off** on the final build.
- [ ] **Phase 2: DNS.** Joshua adds the records at GoDaddy by hand, then tells me
      and I do the CNAME file, custom domain, and HTTPS.

## 2. Placeholders visible on the page

| Where | What it says now | What it needs |
|---|---|---|
| Weekend section | "Times are coming soon." | Real start times for Fri June 4, Sat June 5, Sun June 6 |
| Friday poster | "More times and details to be announced." | Friday start time and the rest of the Deacon details |
| Stay section | "more hotel options coming soon!" | Hotel options beyond The Deacon (names, addresses, any room block) |
| FAQ, "What do I wear?" | "More inspiration to come." | Links to add — there's a commented-out `<a class="ilink">` line in `index.html` right after that sentence showing the exact pattern |

**Resolved:** the ceremony location. Joshua confirmed the ceremony and cocktails
are up on the roof at Bok and dinner stays in the gym, so the illustration reads
"ceremony + cocktails up here!" and the Saturday poster and dinner menu are
unchanged.

## 3. Facts already on the page that I have NOT verified

These were written before I got here. I have left every one of them exactly as
found — please confirm or correct each before launch.

**Food / Friday**
- [ ] Party Girl is the caterer, and it is Mallory Valvano's Party Girl
      (partygirlworldwide.com) — the brief flags this as unconfirmed
- [ ] Party Girl started in 2021 as "Party Girl Bake Club"
- [ ] Daniel Daley is executive chef
- [ ] Friday tacos are by Mission Taqueria
- [ ] Sunday is coffee and pastries at The Deacon

**The weekend**
- [ ] Friday welcome party is at The Deacon, 1600 Christian St
- [ ] Saturday: cocktail hour on the roof, family-style dinner in the gym, dancing
- [ ] Sunday coffee is at The Deacon

**FAQ answers**
- [ ] Wedding is adults only
- [ ] Childcare at The Deacon on Saturday night
- [ ] The ceremony is unplugged
- [ ] Open bar all night
- [ ] Dress code is "fancy funky"

**Bok history + addresses**
- [ ] 1935 construction starts / 1938 opens / 1986 National Register / 2013 closes
      / 2014 Scout buys it
- [ ] "more than 200 artists, makers and small businesses" inside
- [ ] There is a rooftop bar
- [ ] Bok address: 1901 S. 9th St, Philadelphia, PA 19148
- [ ] The Deacon address: 1600 Christian St, Philadelphia, PA 19146
- [ ] The Deacon is a 1906 church in Graduate Hospital

## 4. Done in Phase 1

- [x] Git repo, `.gitignore`, `.nojekyll`
- [x] GitHub repo, pushed to `main`; Pages building from `main` / `/`
- [x] Preview live at https://joshua-albert.github.io/wedding-site/
- [x] Draft switch removed; **B Blue** locked in as the site's colours
      (A Plum kept commented in the CSS — see `:root` and the four lines marked
      `palette A` — so it can be flipped back)
- [x] No `localStorage` anywhere on the page; no analytics, no cookies, no tracking
- [x] `<meta name="robots" content="noindex,nofollow">` + `robots.txt` disallowing all
- [x] Title, description, favicon (disco ball), apple-touch-icon
- [x] Open Graph share image `og.png`, 1200×630, made from the hero
- [x] All four Google Fonts load; zero console errors; no horizontal scroll at 390px
- [x] Vendor Instagram links (Party Girl, The Deacon, Bok), all open in a new tab
- [x] Works with iOS **Reduce Motion** switched on: the ball still spins when you
      swipe it and both tickers keep crawling. Tested in real WebKit (iPhone
      emulation) at 390px and 402px, with Reduce Motion both on and off.
- [x] Ten small bumblebees spread from the hero down to the footer, all tucked
      inside illustrations so they can't cover text or buttons (checked
      automatically against every link, button and text node at 390px and 402px)
- [x] The "give it a spin!" note stays visible at all times
- [x] **Flash safety (WCAG 2.3.1, no more than 3 flashes/second).** Measured after
      the hardest possible flick: glints 1.99/s, ink-line jitter 2.5/s (was 5.6/s),
      ball capped at ~1.5 turns/sec (was 3.2). With Reduce Motion on, the glint
      layer drops to 25% and the ink lines stop boiling, while both tickers crawl.
- [x] "website built by Joshua" in the footer

## 5. Things to know

- **The repo is public.** GitHub's free plan won't serve Pages from a private
  repo, and Joshua chose public over a $4/month Pro upgrade. There's no guest
  data and no secrets in here, but the source is browsable at
  github.com/joshua-albert/wedding-site by anyone who looks. Upgrading to Pro
  later and flipping it back to private is a two-minute change.
- **On the github.io preview URL, `robots.txt` does nothing.** Crawlers only
  read `joshua-albert.github.io/robots.txt`, which is GitHub's, not ours. The
  `noindex,nofollow` meta tag is doing the work for now; our robots.txt starts
  applying in Phase 2 once the site is at its own domain.
- **The share image won't preview until the domain is live.** `og:image` and
  `og:url` point at `https://annaandjoshuasayido.com/`, because that's the link
  guests will actually be texted. On the temporary github.io preview URL, the
  image won't show in iMessage. That's expected and fixes itself in Phase 2.
- **`reference/dinner-club/` and `reference/the-mix/` are in the repo** so the
  other two concepts aren't lost. They're never linked from the site, and
  robots.txt blocks everything, but they *are* reachable by anyone who guesses
  the URL. Say the word and I'll pull them out of the deployed folder.
- **`tools/`** holds the two source files the share image and app icon were
  rendered from. Not part of the site; kept so they can be regenerated.
- The countdown in the hero is computed live in the browser from June 5, 2027.
  Nothing to maintain.

## 6. After the domain is connected (Phase 2)

- [ ] `CNAME` file committed
- [ ] Custom domain set on the Pages site
- [ ] A records resolve to 185.199.108.153 / .109.153 / .110.153 / .111.153
- [ ] `www` CNAME resolves
- [ ] Certificate issued, **Enforce HTTPS** turned on
- [ ] `https://annaandjoshuasayido.com` and `https://www.` both load
- [ ] Re-check the share image in an actual iMessage before sending the link out
