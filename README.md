# Kim Ket · Yoga, Reiki, Meditation & Tarot

One page, no build step: `index.html`.

## Filling it in

Everything Kim-specific is in the `SITE` block near the bottom of `index.html`.
Anything left empty stays hidden, so the page never shows placeholders.

| Setting | What it does |
| --- | --- |
| `email` | Contact form opens the visitor's email app addressed to this |
| `formspreeId` | Optional, free at formspree.io: sends messages without leaving the page |
| `bookingUrl` | Calendly / Acuity / Square link for "Open the calendar"; without it the button says "Request a time" and goes to the form |
| `instagram` | Shows the Instagram link in the footer |
| `portrait` | e.g. `photos/kim.jpg` (4:5 works best); otherwise a lotus mark shows |
| `photos` | `{ src, alt }` list: the Gallery section and its menu link appear once there's at least one |
| `testimonials` | `{ quote, who }` list of **real** client words: the "Kind words" section appears once there's at least one |

Put image files in `photos/`. Resize to ~1600px wide so the page stays fast.

## Booking with Google Calendar (free)

1. In Google Calendar (computer), **Create → Appointment schedule**.
2. Set the session length, the hours she's available, and a buffer between
   sessions; turn on email confirmations. Save.
3. Open the schedule → **Share** → copy the booking page link.
4. Paste it into `bookingUrl` in `index.html`. The "Request a time" button
   becomes "Open the calendar" and opens her booking page.

## Hosting at kimket.com (GitHub Pages + Cloudflare DNS)

kimket.com is registered at GoDaddy but its DNS is managed in **Cloudflare**,
so all record changes happen in Cloudflare. `CNAME` tells GitHub Pages the domain.

- Cloudflare → kimket.com → DNS → Records: delete the existing `A` records for
  `kimket.com` and `www`, then add (all **DNS only**, grey cloud):
  - `A` `@` → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
  - `AAAA` `@` → 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153
  - `CNAME` `www` → `jetech37.github.io`
- GitHub repo → Settings → Pages: deploy from `main` / root, custom domain
  `kimket.com`, then **Enforce HTTPS** once it's verified.
