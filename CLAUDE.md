# isitjaimesbirthday.com — source of truth

A single-serving birthday-gift microsite for Jaime, a working brand/product designer
(studio: jkk.studio). This file is the single source of truth: brand, voice, flow,
motion, and open questions. Update it whenever a decision changes.

---

## 1. The thesis (read this first)

**The interface falls in love in real time.**

The site behaves like a piece of deadpan internet infrastructure — a status-checker
that exists to answer one dumb question, *is it Jaime's birthday?* — and over the
course of the experience it loses its composure: a cold machine with an obvious,
poorly-hidden, entirely manageable crush. **Early-dating tone — light and witty, never
a love confession.**

The arc **machine → alive** is the whole design system:
- **Early** = mechanical: mono type, scramble, hard snaps, no easing, no warmth.
- **Late** = organic: serif, elastic settles, parallax drift, a breathing circle, the dog.
- Every scene must sit *further along that line* than the one before it.
- After the verdict, **nothing is ever fully at rest.**

This is what fixes the "vanilla" problem: motion has a reason to exist. The UI itself
is the character.

The recipient is a brand designer, so **brand fidelity and typographic craft are not
nice-to-haves.** Sloppiness (especially OS emoji, wrong fonts, lazy contrast) will read
as carelessness and break the gift.

---

## 2. Brand system (non-negotiable — extracted from jkk.studio)

### Palette — ONE accent only. This discipline is why her work looks expensive.
| Token            | Hex       | Use |
|------------------|-----------|-----|
| `--cobalt`       | `#240BE2` | the one hero accent |
| `--cobalt-deep`  | `#1700DA` | offset shadows, pressed states |
| `--beige`        | `#F1E1D5` | the ground |
| `--ink`          | `#231F20` | text, borders (warm near-black) |
| `--white`        | `#FFFFFF` | cards |
| `--periwinkle`   | `#7B9FE5` | secondary blue — **rings, sparkles, large only. NEVER body copy (fails contrast on beige).** |

No gradients. No second accent. No rainbow confetti. No AI-purple anything.

### Type
- **Display / headlines:** `JKK` = **Faffin Medium** (commercial face by Paul Henry Robb).
  Embed as base64 for a self-contained file. Graceful serif fallback for public hosting.
- **Body + emphasis:** **Old Standard TT** (Google). Her signature move:
  **exactly one italicized word per headline** ("is it *Jaime's* birthday", "a *sophisticated* dinner"). Enforce this everywhere.
- **UI / labels / buttons:** **Roboto** (Google). Tracked, uppercase for system labels only.

### Motifs
- The **cobalt circle** is her hero shape; a **dashed periwinkle ring** orbits it; photos sit *inside* the circle.
- The **crab** is the ONE sanctioned piece of "creative mischief" (her phrase). It is a
  **hand-drawn cobalt line mark**, never the 🦀 emoji. Lives in the cursor + the celebration.
- Iconography is **drawn cobalt line marks** (taco, wine glass). **No OS emoji anywhere.**

### Voice
- Deadpan single-serving-site that can't stay deadpan — tips into tenderness. Dry wit.
- **lowercase / sentence case, never Title Case.** Uppercase only for mono system readouts.
- **Early-dating register: jovial, dry, witty — NOT a love confession.** They just started
  dating. No "I love you," no *j'aime*, no declarations. The machine plays it cool and fails
  (e.g. `STATUS: a normal amount of excited` → `that was a lie.`). Warmth lives in the effort
  and the deadpan humor, not in saying the big thing.
- **The couple are women. Pronoun for the gift-giver is "her" — "let her know," never "him."**

---

## 3. The flow / storyboard (v2 — current)

Six acts. The verdict gates everything: the celebration is *withheld* on every day that
isn't her birthday, which is what makes it land on the day that is.

| # | Scene | What happens | Motion register |
|---|-------|--------------|-----------------|
| 00 | **BOOT** | mono label "consulting the calendar_", blinking cursor, dashed ring draws on, crab cursor wakes. Cold, ~1.5s max, unmistakably deliberate (not "broken"). | most mechanical |
| 01 | **THE QUESTION** | today's **live date** scrambles like a split-flap board and snaps to today. Headline "is it *Jaime's* birthday?" | mechanical |
| 02 | **THE VERDICT** | date-gated. **Birthday → "oui." (the French turn, not "yes")** in 3 sequenced beats: (1) stamp lands ALONE on empty cobalt; (2) +0.4s dog rains + shapes drift in *behind* it; (3) +1.2s copy settles, ring orbits, circle breathes. **Non-birthday → deadpan "no." + dry countdown** ("N days. the universe is very precise."), stays cold. | break point |
| 03 | **THE TURN** | the deadpan machine cracks: **"it's official."** then a mono STATUS line types "a normal amount of excited" → backspaces → "that was a lie." Playful, never a confession. CTA "open your present →". | warming |
| 04 | **THE INVITATION** | dog-rain wipe → "you're cordially invited / to come to *my apartment*". Headline lands first, then the choice rises. | organic |
| 05 | **THE CHOICE** | two **equal-weight** cards (matched frame, shadow, label length — neither is the "right" answer): **white trash tacos** (paper plates · hot sauce · zero pretense) vs **a sophisticated bay ridge dinner** (cloth napkins · a reservation · a wine list). Drawn cobalt line icons. Tilt toward cursor on hover, press in on tap. | organic |
| 06 | **THE CONFIRMATION** | names her pick in display type + a dry tailored line, then **"let her know 🦀"** (drawn crab) sends the choice to the giver. P.S. closes dry: "i like you a normal, reasonable amount. ✓ verified." | fully alive |

Tailored confirmation lines:
- tacos → "paper plates, maximum hot sauce, zero pretense."
- dinner → "cloth napkins, a real reservation, an actual wine list — wear something nice, i will too."

---

## 4. Motion law (anime.js v4)
- Vendored at `assets/vendor/anime.umd.min.js` (global `anime`; for final deploy, inline it).
- Timelines, not setTimeout chains. Stagger reveals. Elastic/spring settles late; hard snaps early.
- Pointer-parallax on the hero circle (wrap circle+ring; parallax the wrapper, keep CSS breathe/spin on children to avoid transform conflicts).
- Magnetic tilt on choice cards. Particle sparks on pointerdown. Physics-ish dog-rain (varied size, rotation, easing) on every scene change.
- **`prefers-reduced-motion`: a calm static twin.** Skip scramble/burst/rain; jump to final states. Must never break or hide content.

---

## 5. Asset inventory
| Asset | Status | Notes |
|-------|--------|-------|
| `assets/cursors/crab-open.svg` | ✅ recreated | cursor default; hotspot ~6,4 |
| `assets/cursors/crab-pinch.svg` | ✅ recreated | active/click state |
| `assets/vendor/anime.umd.min.js` | ✅ vendored | v4.4.1, 115KB |
| `assets/img/dog-placeholder.svg` | ✅ placeholder | cobalt dachshund-in-circle, swap for real photo |
| **Faffin Medium .ttf** | ❌ NEEDED | prior session's embedded copy was lost; re-source + base64. Public-host = licensing note / free fallback. |
| **Dog photo (IMG_5031.heic cutout)** | ❌ NEEDED | re-upload; transparent dachshund cutout for the dog-rain. |
| Optional: a photo of the two of them | ⬜ nice-to-have | sits inside the cobalt circle. |

---

## 6. Config (lives in index.html `CONFIG`)
`herName` · `birthday {month:5, day:30}` · `yourEmail` (for the notification) · `dogPhoto`.

---

## 7. Tech baseline
Vanilla HTML/CSS/JS, single deployable static site, mobile-first (she opens on her phone —
must be flawless at ~390px). Tokens as CSS custom properties. No framework.
Deploy: rename to `index.html` → Netlify drop → point the domain.

---

## 8. Open questions (resolve during build)
1. **Touch-native crab** — the cursor is the signature delight and it does NOT exist on
   mobile, her primary device. Design a finger-driven crab (rides touch, pinches on tap,
   scuttles to taps). HIGHEST-leverage open problem.
2. **The "no." path** — dead-end, or a soft "come back on the 30th / peek anyway"? Decide.
3. **Reduced-motion twin** — define the calm static version of each scene.
4. Notification mechanism — `mailto` (works everywhere, needs her mail set up) vs Formspree
   (instant ping regardless). Pick before ship.
