# Transet Global Logistics (TNGL) — Website

A modern, animated, multi-page marketing website for **Transet Global Logistics LLC**, a Dubai-based freight-forwarding and supply-chain company. Built in the brand's orange-and-white identity, with HD logistics photography and an interactive 3D globe of the company's trade lanes.

### What's new in this version
- **Premium "futuristic tech" pass** — added depth and motion throughout while keeping all content and branding: a hero **particle constellation** (canvas) + animated tech-grid + pointer parallax, **glassmorphism** nav and hero chips, **3D tilt** on service and testimonial cards, drifting **glow orbs** behind sections, an **animated gradient border** on the Active Lanes panel, a **cursor spotlight**, button **sheen/glow**, and a top **scroll-progress bar**.
- **Performance-first** — every effect is GPU-cheap: animations use only `transform`/`opacity`, glows are soft radial-gradients (no heavy blur on scrolling content), the particle canvas is capped and **pauses when off-screen or the tab is hidden**, and all pointer/scroll handlers are throttled with `requestAnimationFrame`. Smooth-scroll is tuned for a snappy, high-framerate feel. Everything collapses gracefully under `prefers-reduced-motion`.
- **Video-style hero** — the home background plays the cargo journey as a cinematic cross-fading sequence: warehouse → truck → cargo plane → container ship → terminal transfer → warehouse, each with a slow Ken-Burns zoom.
- **Animated "Active Lanes" panel** — the *One partner accountable for the whole journey* section shows a live schematic of trade lanes with orange pulses travelling each route.
- **Floating WhatsApp button** — on every page, bottom-right, opens a chat to +971 52 375 9520 with a pre-filled message.

---

## 1. Pages

| File | Page | Purpose |
|------|------|---------|
| `index.html` | Home | Hero, stats, services, capabilities, **3D network globe**, process, testimonials, CTA |
| `about.html` | About Us | Company story, what we do, why choose us, stats |
| `services.html` | Services | Overview grid linking to every service + process |
| `air-freight.html` | Air Freight | Service detail: overview, inclusions, highlights |
| `sea-freight.html` | Sea Freight | Service detail |
| `land-transport.html` | Land Transport | Service detail |
| `warehousing.html` | Warehousing | Service detail |
| `customs-clearance.html` | Customs Clearance | Service detail |
| `contact.html` | Contact | Contact details, socials, quote-request form |

Every page shares the same header, footer, styling and animation system, so the site feels consistent end-to-end.

---

## 2. Brand & design system

**Theme:** "Orange & White" — built from the TNGL logo.

| Token | Value | Use |
|-------|-------|-----|
| Brand orange | `#FF6501` | Primary accent, CTAs, highlights (sampled from your logo) |
| Orange (hover) | `#E85800` | Button/link hover |
| Orange tint | `#FFF3EC` | Icon chips, soft backgrounds |
| Ink | `#15181D` | Headings & primary text |
| Body | `#3B424C` | Body text |
| Dark sections | `#0F1420` | Footer + 3D network band |
| Surface | `#FFFFFF` / `#F6F7F9` | Page & alternating section backgrounds |

**Typography:** Space Grotesk (headings), Inter (body), Space Mono (labels/UI) — loaded from Google Fonts.

**Logo:** embedded directly in every page as a transparent PNG (data URI) so it always renders. Standalone copies are included: `tngl-logo.png` (full res) and `tngl-logo-200.png`.

---

## 3. The 3D element

The **home page** includes an interactive WebGL globe (Three.js) showing TNGL's trade lanes radiating from **Dubai (DXB)** to 14 global hubs — Singapore, Rotterdam, London, Shanghai, Mumbai, New York, and more. Animated pulses travel along each route. Drag to spin it. It sits in a dark "Global Network" band so the orange arcs pop.

It's decorative *and* narrative: it tells the "global network" story rather than just spinning for effect. It pauses when the tab is hidden and respects reduced-motion settings.

---

## 4. Animation system

- **GSAP + ScrollTrigger** — scroll reveals, animated stat counters, hero split-line reveal, hero image parallax.
- **Lenis** — smooth inertia scrolling.
- **CSS** — hover lifts on cards, marquee, animated route tickers, magnetic buttons.
- **Accessibility** — full `prefers-reduced-motion` support (all motion disabled, content shown immediately), 44px+ touch targets, 4.5:1 contrast, keyboard-navigable, semantic headings, image `alt` text.

All libraries load from CDNs (Three.js, GSAP, Lenis). If a CDN ever fails, the site degrades gracefully — content stays visible, counters jump to final values, the globe is simply skipped.

---

## 5. Images & licensing

Photography is served from the **Unsplash CDN** (`images.unsplash.com`).
All images used are under the **Unsplash License** — free for commercial use, no attribution required.

- Hero: cargo ship at sea
- Air Freight: cargo jet
- Sea Freight: container ship
- Land Transport: highway freight truck
- Warehousing: warehouse interior
- Customs / About: container terminal

To swap any photo, replace the `photo-XXXX` ID in the relevant `<img src>` (or in `build.py`).

---

## 6. Viewing the site

Just open **`index.html`** in any modern browser (double-click). All pages link to each other with relative paths, so the whole folder works locally with no build step or server.

An internet connection is needed for the photos, fonts and 3D libraries (they load from CDNs). The logo is embedded and works offline.

---

## 7. Editing common things

- **Contact details / social links** — edit the footer and `contact.html`, or change the constants at the top of `build.py` and re-run it.
- **Text / copy** — edit directly in the HTML, or in `build.py` (the source of truth) then run `python3 build.py`.
- **Stats** — the `5,731 / 476t / 123+ / 24-7` figures live in the `stats_block()` function in `build.py` and in each page's stats section. Update if any are out of date.
- **Quote form** — currently validates inline and opens the visitor's email app pre-addressed to `info@tngl.ae`. To capture leads into a CRM/database instead, point the form's submit handler at your backend endpoint (about a 30-minute change).

Regenerate all pages after editing `build.py`:
```bash
python3 build.py
```

---

## 8. Deployment

It's a static site — host it anywhere:

- **Netlify / Vercel / Cloudflare Pages** — drag-and-drop the folder, or connect a repo.
- **Traditional hosting / cPanel** — upload the files to `public_html`.
- **GitHub Pages** — push to a repo and enable Pages.

No server, database or build pipeline required.

---

## 9. SEO

Each page ships with a unique `<title>`, meta description, Open Graph tags, semantic headings, descriptive `alt` text and a favicon. Consider adding a `sitemap.xml`, `robots.txt` and Google Business/Analytics when you go live.

---

## 10. Company details used

- **Phone:** +971 4 250 5668 · +971 52 375 9520
- **Email:** info@tngl.ae
- **Address:** Office 201-10, Al Masood Tower, Riga Al Buteen, Dubai, UAE
- **Social:** LinkedIn, Facebook, X, Instagram

*Testimonials (ET, Meraki, Vision, IDL) and statistics were carried over from the existing site. Please confirm they're current before publishing.*
