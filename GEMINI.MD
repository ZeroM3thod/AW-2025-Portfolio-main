

**Placeholders to fill everywhere:**
- `YOUR_NAME` — RAKIBUL HASAN
- `YOUR_INITIALS` — RH
- `YOUR_EMAIL` — rakib.404.dev@gmail.com
- `YOUR_ROLE` — Full Stack Developer
- `YOUR_LOCATION` — DHAKA, BANGLADESH
- `YOUR_LINKEDIN_URL` — https://www.linkedin.com/in/rakibul-hasan-36a776414

## 1. `src/pages/index.astro` — Meta & SEO

Replace the `<title>` and meta tags inside `<head>`:

```html
<title>YOUR_NAME – WEB DEVELOPER</title>

<meta
  name="description"
  content="YOUR_ROLE based in YOUR_LOCATION. Building fast, accessible web products." />
<meta name="viewport" content="width=device-width" />
<meta name="generator" content={Astro.generator} />

<meta name="robots" content="index, follow" />
<link rel="canonical" href="https://yoursite.com/" />

<meta name="theme-color" content="#f40c3f" />
<meta name="msapplication-navbutton-color" content="#f40c3f" />
<meta name="apple-mobile-web-app-status-bar-style" content="#f40c3f" />

<meta property="og:locale" content="en_GB" />
<meta property="og:type" content="website" />
<meta property="og:title" content="YOUR_NAME – Portfolio" />
<meta property="og:description" content="YOUR_ROLE based in YOUR_LOCATION. Building fast, accessible web products." />
<meta property="og:url" content="https://yoursite.com/" />
<meta property="og:site_name" content="YOUR_NAME – Portfolio" />
<meta property="og:image" content="https://yoursite.com/images/og-image.png" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="675" />
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:image" content="https://yoursite.com/images/og-image.png" />
```

---

## 2. `src/components/SiteHead.astro`

### Logo

Find `<div class="sb-logo">` and replace its `<a>` inner content.

**Option A — you have an SVG/PNG logo** (place it at `/public/images/logo.svg`):

```html
<div class="sb-logo">
  <a href="/">
    <img
      class="js-logo"
      src="/images/logo.svg"
      alt="YOUR_NAME"
      style="display:block; width:3rem; height:3rem; object-fit:contain;"
    />
    <span class="u-sr-only">YOUR_NAME</span>
  </a>
</div>
```

**Option B — text initials, no image file needed:**

```html
<div class="sb-logo">
  <a href="/">
    <span
      class="js-logo"
      style="display:flex; align-items:center; justify-content:center; width:3rem; height:3rem; background:var(--color-secondary); color:var(--color-primary); font:700 1.1rem/1 var(--font-family-fraktion); letter-spacing:0.05em;"
    >
      YOUR_INITIALS
    </span>
    <span class="u-sr-only">YOUR_NAME</span>
  </a>
</div>
```

### Availability text

Find `<aside class="sb-availability">` and replace its `<p>`:

```html
<aside class="sb-availability">
  <p>
    <span class="sb__line">
      <span class="sb__text">YOUR_ROLE based in YOUR_LOCATION.</span>
    </span>

    <span class="sb__line">
      <span class="sb__text">Available for freelance work →</span>
      <a href="mailto:YOUR_EMAIL" class="sb__link">Hire me</a>
    </span>
  </p>
</aside>
```

### Social links

Find `<ul class="sb-socials">` and update the two `href` attributes. Keep all inner `<span>` elements exactly as-is, only touch the `href`:

```html
<a href="YOUR_CODEPEN_URL" target="_blank" rel="noopener">
<a href="YOUR_LINKEDIN_URL" target="_blank" rel="noopener">
```

### Email — global find & replace

Do a find-all for `hello@wodniack.dev` in this file (2 occurrences — the availability link and the QR code `href`) and replace both with `YOUR_EMAIL`.

For the QR code: either generate one at `qr.io` pointing to `mailto:YOUR_EMAIL` and save it at `/public/images/qr-code.svg`, or just delete the entire `<a class="sb-qr-code js-qr-code">` block.

---

## 3. `src/components/SiteFoot.astro`

Find `<div class="site-foot__logo">` and replace its `<a>` content with whichever logo option you chose above:

**Option A:**
```html
<div class="site-foot__logo">
  <a href="/">
    <img
      src="/images/logo.svg"
      alt="YOUR_NAME"
      style="display:block; width:3rem; height:3rem; object-fit:contain;"
    />
    <span class="u-sr-only">YOUR_NAME</span>
  </a>
</div>
```

**Option B:**
```html
<div class="site-foot__logo">
  <a href="/">
    <span
      style="display:flex; align-items:center; justify-content:center; width:3rem; height:3rem; background:var(--color-secondary); color:var(--color-primary); font:700 1.1rem/1 var(--font-family-fraktion); letter-spacing:0.05em;"
    >
      YOUR_INITIALS
    </span>
    <span class="u-sr-only">YOUR_NAME</span>
  </a>
</div>
```

---

## 4. `src/components/SHero.astro`

### Name separator

Find the first `<ASeparator>` component (around line 14) and change `strings` to spell your name in 2–3 character chunks:

```astro
<ASeparator
  class="s__separator js-separator"
  strings={['Ra', 'ki', 'b', 'Ho', 'ss', 'ain']}
/>
```

Any split works — the strings animate as scrolling binary, so chunking is purely visual preference.

### Hero title (optional)

The `<h1>` currently reads "Creative Developer". If you want to change it, find these two `<span>` elements inside `.s__title`:

```html
<span class="s__title__word js-word">Creative</span>
<span class="s__title__word js-word">Developer</span>
```

Replace the text content only — keep the class names exactly as-is since the intro animation targets them.

---

## 5. `src/components/SAbout.astro` — Main change

Four steps inside this one file.

### Step A — Replace frontmatter data

Find the entire `const awards = { ... }` block at the top of the `---` section and replace with:

```js
const profile = {
  counters: {
    frontend: ['React / Next.js', 'Vue / Astro'],
    backend: ['Node.js / Python', 'REST / GraphQL'],
  },
  texts: {
    headline: 'Full Stack Developer<br/>&amp; Creative Coder',
    statement: 'Building fast, accessible products — from idea to deployment',
    stack: 'TypeScript · JavaScript · HTML · CSS',
    mobile: 'Flutter &amp; React Native<br/>for Mobile',
    design: 'UI/UX Design<br/>&amp; Prototyping',
    ai: 'AI Integration<br/>&amp; Automation',
    experience: '3+<br/>Years Building',
    available: 'Open to Freelance<br/>&amp; Remote Work',
  },
}
```

Adjust every string to match your actual stack and experience.

### Step B — About text

Find `<div class="s__content">` and replace all `<p>` tags:

```html
<div class="s__content">
  <p>
    I build things for the web — from fast, accessible interfaces to backend systems and AI-powered tools. Clean code and thoughtful design aren't opposites. I care about both.
  </p>

  <p>
    My work spans e-commerce platforms, POS systems, mobile apps, and everything in between. Each project sharpens something new.
  </p>

  <p>
    I learn by doing. I break things, fix them, and ship. That process never gets old.
  </p>

  <p>
    Looking to build something?
    <a href="mailto:YOUR_EMAIL">Let's talk.</a>
  </p>
</div>
```

### Step C — Skills grid HTML

Find the entire `<div class="s__block s__block--awards">` block and replace it with this. The blank decorative cell is preserved exactly:

```html
<div class="s__block s__block--awards">
  <h2 class="s__title">Stack</h2>

  <ul class="s__awards">
    {
      Object.entries(profile.counters).map(([skill, items]) => (
        <li
          class={`s__award s__award--counter s__award--${skill} js-award`}
        >
          <span class="s__award__inner">
            <span class="s__award__name">{skill}</span>
            {items.map((item) => (
              <span class="s__award__counter">({item})</span>
            ))}
          </span>
          <span class="s__award__mask" />
        </li>
      ))
    }

    {
      Object.entries(profile.texts).map(([key, text]) => (
        <li class={`s__award s__award--text s__award--${key} js-award`}>
          <span class="s__award__inner">
            <span class="s__award__text" set:html={text} />
          </span>
          <span class="s__award__mask" />
        </li>
      ))
    }

    <li class="s__award s__award--blank">
      <svg width="101" height="113" viewBox="0 0 101 113" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M80.05 107.398c-21.944 12.67-52.875.18-69.085-27.896m69.086 27.896c21.945-12.67 26.594-45.702 10.384-73.778M80.05 107.398c-19.686 11.366-48.786-2.181-64.996-30.258C-1.155 49.063 1.663 17.09 21.35 5.723m58.702 101.675c19.686-11.366 22.504-43.34 6.293-71.417C70.134 7.904 41.034-5.642 21.35 5.723m58.702 101.675c-10.973 6.335-33.009-11.29-49.219-39.367-16.21-28.077-20.456-55.973-9.483-62.308m58.702 101.675c10.972-6.335 6.726-34.231-9.484-62.308C54.357 17.013 32.322-.612 21.35 5.723m58.702 101.675c3.74-2.159-6.262-26.77-22.456-54.818S25.089 3.564 21.349 5.723m58.702 101.675c-3.74 2.159-20.053-18.808-36.246-46.856C27.61 32.493 17.609 7.882 21.349 5.723M10.965 79.502C-5.245 51.425-.596 18.393 21.349 5.723M10.965 79.502c11.366 19.686 38.37 25.373 60.314 12.703 21.946-12.67 30.522-38.9 19.156-58.585m-79.47 45.882C-.401 59.816 8.175 33.586 30.121 20.916c21.945-12.67 48.948-6.982 60.314 12.704m-79.47 45.882c6.335 10.972 29.26 9.596 51.206-3.074C84.115 63.758 96.77 44.592 90.434 33.62m-79.47 45.882C4.63 68.529 17.285 49.363 39.23 36.693c21.945-12.67 44.87-14.046 51.205-3.073M21.349 5.723c21.945-12.67 52.876-.18 69.086 27.897M54.749 63.573C32.778 76.258 13.192 83.358 11.033 79.618c-2.16-3.74 13.783-17.15 35.754-29.836 21.97-12.685 41.557-19.785 43.716-16.045 2.159 3.74-13.783 17.15-35.754 29.836Z"></path>
      </svg>
      <svg width="49" height="49" viewBox="0 0 49 49" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill="#160000" d="m24.5 0 3.3 21.2L49 24.5l-21.2 3.3L24.5 49l-3.3-21.2L0 24.5l21.2-3.3L24.5 0z"></path>
      </svg>
      <svg width="49" height="49" viewBox="0 0 49 49" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill="#160000" d="m24.5 0 3.3 21.2L49 24.5l-21.2 3.3L24.5 49l-3.3-21.2L0 24.5l21.2-3.3L24.5 0z"></path>
      </svg>
      <svg width="49" height="49" viewBox="0 0 49 49" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill="#160000" d="m24.5 0 3.3 21.2L49 24.5l-21.2 3.3L24.5 49l-3.3-21.2L0 24.5l21.2-3.3L24.5 0z"></path>
      </svg>
      <svg width="49" height="49" viewBox="0 0 49 49" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill="#160000" d="m24.5 0 3.3 21.2L49 24.5l-21.2 3.3L24.5 49l-3.3-21.2L0 24.5l21.2-3.3L24.5 0z"></path>
      </svg>
    </li>
  </ul>
</div>
```

### Step D — SCSS grid positions

Inside the `<style lang="scss">` block, find the `.s__awards` section. Keep everything (the base `.s__award` block, all `&--counter`, `&--text`, `&--blank` base styles, and the `&.is-active` / `&.is-revealed` states) exactly as-is.

Delete only these named position blocks:

```
&--webby2025 { ... }
&--awwwards { ... }
&--netMag2016 { ... }
&--commArt2017 { ... }
&--fwa { ... }
&--gsapOct2024 { ... }
&--gsapNov2024 { ... }
&--cssda { ... }
&--CSSDA2016 { ... }
&--CSSDA2015 { ... }
```

And add these in their place. The `&--blank` block stays unchanged:

```scss
&--headline {
  grid-column: 1 / 5;
  grid-row: 1 / 2;
}

&--frontend {
  grid-column: 1 / 3;
  grid-row: 2 / 4;

  @include mq(tablet-sm) {
    grid-column: 1 / 3;
    grid-row: 2 / 4;
  }

  .s__award__name {
    font-size: 8.625rem;

    @include mq(desktop-xs) {
      font-size: 6.5rem;
    }

    @include mq(tablet-sm) {
      font-size: 5.5rem;
    }

    @include mq(phone) {
      font-size: 4rem;
    }

    @include mq(phone-sm) {
      font-size: 3.5rem;
    }
  }
}

&--stack {
  grid-column: 3 / 5;
  grid-row: 2 / 3;

  @include mq(tablet-sm) {
    grid-column: 3 / 5;
    grid-row: 2 / 3;
  }
}

&--mobile {
  grid-column: 4 / 5;
  grid-row: 3 / 4;

  @include mq(tablet-sm) {
    grid-column: 3 / 5;
    grid-row: 4 / 6;
  }
}

&--statement {
  grid-column: 1 / 5;
  grid-row: 4 / 5;

  @include mq(tablet-sm) {
    grid-column: 1 / 5;
    grid-row: 8 / 9;
  }
}

&--backend {
  grid-column: 2 / 4;
  grid-row: 5 / 6;

  @include mq(tablet-sm) {
    grid-column: 1 / 3;
    grid-row: 6 / 8;
  }
}

&--design {
  grid-column: 1 / 3;
  grid-row: 6 / 7;

  @include mq(tablet-sm) {
    grid-column: 1 / 3;
    grid-row: 4 / 5;
  }
}

&--ai {
  grid-column: 3 / 5;
  grid-row: 6 / 7;

  @include mq(tablet-sm) {
    grid-column: 3 / 5;
    grid-row: 6 / 7;
  }
}

&--experience {
  grid-column: 2 / 5;
  grid-row: 7 / 8;

  @include mq(tablet-sm) {
    grid-column: 1 / 4;
    grid-row: 9 / 10;
  }
}

&--available {
  grid-column: 1 / 4;
  grid-row: 8 / 9;

  @include mq(tablet-sm) {
    grid-column: 2 / 5;
    grid-row: 10 / 11;
  }

  &:before {
    bottom: -1px;
  }
}
```

All animations — the hover smiley throw, the mask wipe reveal, and the `is-revealed` slide-in — run off the shared `js-award` class and existing base styles. None of that needs touching.

---

## 6. `src/components/SCTA.astro`

### Email

Find `href="mailto:hello@wodniack.dev"` and `hello@wodniack.dev` text inside the `.s__cta__link` anchor and replace with your email.

### "Let's Rock" text (optional)

The big CTA text is defined at the top of the file:

```js
const lines = [
  ['L', 'e', 't<span class="sup">\'</span>', 's'],
  ['R', 'o', 'c', 'k'],
]
```

You can change this to anything two-line and short, e.g. `Let's Build` or `Let's Talk`. Each character must be its own array element. Keep `<span class="sup">` around apostrophes.

---

## 7. `src/components/SMyWay.astro` — Watermark text (optional)

The big distorted text in this section says "Remember not to steal this." Find both occurrences of that string inside `.s__catcher__text` and replace with anything — your name, a tagline, a phrase.

---

## Quick checklist

```
[ ] index.astro          — title, description, OG tags, canonical URL
[ ] SiteHead.astro       — logo, availability text, social hrefs, email x2, QR code
[ ] SiteFoot.astro       — logo
[ ] SHero.astro          — name in separator strings, h1 title if desired
[ ] SAbout.astro         — profile data, about text, skills grid HTML, SCSS positions
[ ] SCTA.astro           — email, optional CTA text
[ ] SMyWay.astro         — optional watermark text
[ ] /public/images/      — add your logo.svg and og-image.png
```


## Part 1 — Color Themes

The single most impactful change. Everything on the site — lines, text, interactive elements, grid — derives from two variables.

**File:** `src/styles/variables-scss/_colors.scss`

Replace the entire file with one of the five palettes below. After changing, also find `background: #F40C3F` inside the `.site-intro` div in `index.astro` and replace with your new `secondary` hex color.

---

**Option 1 — Midnight (dark navy + electric blue)**

```scss
$theme-colors: (
  default: (
    primary: #080c14,
    secondary: #00b4d8,
    shadow: #0a1628,
    white: #e0f4ff,
  ),
  contrasted: (
    primary: #e0f4ff,
    secondary: #080c14,
    shadow: #3a5070,
    white: #ffffff,
  ),
);
```

---

**Option 2 — Terminal (black + neon green)**

```scss
$theme-colors: (
  default: (
    primary: #0d0d0d,
    secondary: #00ff41,
    shadow: #001a00,
    white: #e8ffe8,
  ),
  contrasted: (
    primary: #f0fff0,
    secondary: #0d0d0d,
    shadow: #3a4a3a,
    white: #ffffff,
  ),
);
```

---

**Option 3 — Dusk (deep purple + warm parchment)**

```scss
$theme-colors: (
  default: (
    primary: #1c1028,
    secondary: #e8d5b7,
    shadow: #2e1a44,
    white: #fff5e8,
  ),
  contrasted: (
    primary: #fff5e8,
    secondary: #1c1028,
    shadow: #6a5a7a,
    white: #ffffff,
  ),
);
```

---

**Option 4 — Copper (dark warm brown + burnt orange)**

```scss
$theme-colors: (
  default: (
    primary: #1a1410,
    secondary: #e07b39,
    shadow: #2e2418,
    white: #fff4ec,
  ),
  contrasted: (
    primary: #fff4ec,
    secondary: #1a1410,
    shadow: #6a5040,
    white: #ffffff,
  ),
);
```

---

**Option 5 — Monochrome (near black + off white)**

```scss
$theme-colors: (
  default: (
    primary: #111111,
    secondary: #f0f0f0,
    shadow: #1f1f1f,
    white: #ffffff,
  ),
  contrasted: (
    primary: #f5f5f5,
    secondary: #111111,
    shadow: #888888,
    white: #ffffff,
  ),
);
```

---

## Part 2 — Page Border Frame

The thick border around the entire page is controlled in two places. Changing these two values together makes the site feel noticeably different — or removes the frame entirely.

**File:** `src/styles/site/_base.scss`

Find `body { padding: 1rem; }` and change the padding value.

**File:** `src/components/SiteScrollbar.astro`

Inside the `<style>` block, find `--border-width: 1rem` and match it to your body padding.

**File:** `src/pages/index.astro`

Inside the `<style>` block, find `.site-mount { border: 1rem solid color(secondary); }` and match it.

Three options:

**Thin frame (0.375rem)**
```scss
// _base.scss
body { padding: 0.375rem; }

// SiteScrollbar.astro
.site-scrollbar { --border-width: 0.375rem; }

// index.astro
.site-mount { border: 0.375rem solid color(secondary); }
```

**No frame at all**
```scss
// _base.scss
body { padding: 0; }

// index.astro — add this
.site-mount { display: none; }

// SiteScrollbar.astro
.site-scrollbar { display: none; }
```

**Thick frame (2rem)**
```scss
// _base.scss
body { padding: 2rem; }

// SiteScrollbar.astro
.site-scrollbar { --border-width: 2rem; }

// index.astro
.site-mount { border: 2rem solid color(secondary); }
```

---

## Part 3 — Film Grain Texture

Add this to the bottom of `src/styles/site/_base.scss`. It overlays a subtle noise texture across the entire site — completely invisible at a glance but adds depth that distinguishes the visual from a flat-color clone.

```scss
body::after {
  content: '';

  position: fixed;
  inset: 0;

  width: 100%;
  height: 100%;

  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)'/%3E%3C/svg%3E");

  opacity: 0.04;
  pointer-events: none;
  z-index: 9999;

  will-change: opacity;
}
```

Increase `opacity` toward `0.08` for heavier grain, lower toward `0.02` to make it more subtle.

---

## Part 4 — Loading Animation

Three complete replacements. Each requires changing three things in `src/pages/index.astro`:

1. The `.site-intro` HTML in the `<body>`
2. The `intro()` method in the Site class inside `<script>`
3. The `.site-intro` block inside `<style lang="scss">`

---

### Option A — Number Counter

A number climbs from `00` to `100` with a progress line, then the panel slides up to reveal the site.

**HTML** — replace the entire `<div class="site-intro js-intro" ...>` block:

```html
<div
  class="site-intro js-intro"
  style="opacity:1; position:fixed; top:0; left:0; z-index:50; width:100%; height:100%;"
>
  <div class="site-intro__counter js-counter">00</div>
  <div class="site-intro__progress js-progress"></div>
</div>
```

**`intro()` method** — replace the entire method inside the Site class:

```js
intro() {
  const wrapper = document.querySelector('.js-site-wrapper')
  const intro   = document.querySelector('.js-intro')
  const mount   = document.querySelector('.js-mount')
  const counter = intro.querySelector('.js-counter')
  const progress = intro.querySelector('.js-progress')

  const count = { value: 0 }

  const tl = gsap.timeline()

  tl.set(wrapper, { opacity: '' }, 0)

  // Progress bar grows
  tl.to(progress, {
    scaleX: 1,
    duration: 2.5,
    ease: 'power2.inOut',
  }, 0)

  // Counter counts up
  tl.to(count, {
    value: 100,
    duration: 2.5,
    ease: 'power2.inOut',
    onUpdate() {
      counter.textContent = String(Math.round(count.value)).padStart(2, '0')
    },
  }, 0)

  // Panel slides up
  tl.to(intro, {
    yPercent: -100,
    duration: 0.9,
    ease: 'power4.inOut',
  }, 2.6)

  // Trigger hero waves animation
  tl.call(() => {
    document.dispatchEvent(new CustomEvent('intro'))
  }, null, 2.1)

  // Cleanup
  tl.call(() => {
    mount.style.opacity = '1'
    intro.remove()
    document.documentElement.classList.remove('is-scroll-blocked')
    Ticker.nextTick(() => { Emitter.emit('updateViewport') })
  }, null, 3.6)
}
```

**SCSS** — replace the entire `.site-intro { ... }` block in the `<style lang="scss">` section:

```scss
.site-intro {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 50;

  width: 100%;
  height: 100%;

  background: color(secondary);

  &__counter {
    position: absolute;
    bottom: 2.5rem;
    left: 2.5rem;

    font: 700 12vw / 1 font-family(bigger);
    color: color(primary);
    letter-spacing: -0.02em;

    @include mq(phone) {
      font-size: 20vw;
      bottom: 1.5rem;
      left: 1.5rem;
    }
  }

  &__progress {
    position: absolute;
    bottom: 0;
    left: 0;

    width: 100%;
    height: 3px;

    background: color(primary);
    transform-origin: 0 50%;
    scale: 0 1;

    @include mq(phone) {
      height: 2px;
    }
  }
}
```

---

### Option B — Split Curtain with Name

Two panels split open from the center, revealing your name briefly, then exposing the site underneath.

**HTML** — replace the entire `.site-intro` div:

```html
<div
  class="site-intro js-intro"
  style="opacity:1; position:fixed; top:0; left:0; z-index:50; width:100%; height:100%;"
>
  <div class="site-intro__panel site-intro__panel--left js-panel-left"></div>
  <div class="site-intro__panel site-intro__panel--right js-panel-right"></div>
  <div class="site-intro__name js-intro-name">YOUR_NAME</div>
</div>
```

**`intro()` method:**

```js
intro() {
  const wrapper    = document.querySelector('.js-site-wrapper')
  const intro      = document.querySelector('.js-intro')
  const mount      = document.querySelector('.js-mount')
  const panelLeft  = intro.querySelector('.js-panel-left')
  const panelRight = intro.querySelector('.js-panel-right')
  const name       = intro.querySelector('.js-intro-name')

  const tl = gsap.timeline()

  tl.set(wrapper, { opacity: '' }, 0)

  // Name appears
  tl.to(name, {
    opacity: 1,
    y: 0,
    duration: 0.6,
    ease: 'power3.out',
  }, 0.3)

  // Panels split open
  tl.to(panelLeft, {
    scaleX: 0,
    duration: 1.1,
    ease: 'power4.inOut',
  }, 1.2)

  tl.to(panelRight, {
    scaleX: 0,
    duration: 1.1,
    ease: 'power4.inOut',
  }, 1.2)

  // Name fades as panels open
  tl.to(name, {
    opacity: 0,
    duration: 0.35,
    ease: 'power2.in',
  }, 1.3)

  // Trigger hero animation
  tl.call(() => {
    document.dispatchEvent(new CustomEvent('intro'))
  }, null, 1.5)

  // Cleanup
  tl.call(() => {
    mount.style.opacity = '1'
    intro.remove()
    document.documentElement.classList.remove('is-scroll-blocked')
    Ticker.nextTick(() => { Emitter.emit('updateViewport') })
  }, null, 2.8)
}
```

**SCSS:**

```scss
.site-intro {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 50;

  width: 100%;
  height: 100%;

  &__panel {
    position: absolute;
    top: 0;

    width: 50.1%; // slight overlap to prevent hairline gap
    height: 100%;

    background: color(secondary);

    &--left {
      left: 0;
      transform-origin: 0 50%;
    }

    &--right {
      right: 0;
      transform-origin: 100% 50%;
    }
  }

  &__name {
    position: absolute;
    top: 50%;
    left: 50%;
    z-index: 2;

    transform: translate(-50%, -50%);

    font: 700 7vw / 1 font-family(bigger);
    color: color(primary);
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    white-space: nowrap;

    opacity: 0;
    translate: 0 0.5em 0;

    pointer-events: none;

    @include mq(phone) {
      font-size: 10vw;
    }
  }
}
```

---

### Option C — Minimal Fade

No logo animation, no panels. Just a fast color wipe and go. Best for people who want to keep attention on the hero section.

**HTML:**

```html
<div
  class="site-intro js-intro"
  style="opacity:1; position:fixed; top:0; left:0; z-index:50; width:100%; height:100%;"
>
</div>
```

**`intro()` method:**

```js
intro() {
  const wrapper = document.querySelector('.js-site-wrapper')
  const intro   = document.querySelector('.js-intro')
  const mount   = document.querySelector('.js-mount')

  const tl = gsap.timeline()

  tl.set(wrapper, { opacity: '' }, 0)

  // Hold briefly then fade out
  tl.to(intro, {
    opacity: 0,
    duration: 0.7,
    ease: 'power2.inOut',
    delay: 0.3,
  }, 0)

  // Trigger hero animation early
  tl.call(() => {
    document.dispatchEvent(new CustomEvent('intro'))
  }, null, 0.4)

  // Cleanup
  tl.call(() => {
    mount.style.opacity = '1'
    intro.remove()
    document.documentElement.classList.remove('is-scroll-blocked')
    Ticker.nextTick(() => { Emitter.emit('updateViewport') })
  }, null, 1.2)
}
```

**SCSS:**

```scss
.site-intro {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 50;

  width: 100%;
  height: 100%;

  background: color(secondary);
}
```

---

## Quick reference — what each change does visually

```
Color palette        → entire site identity (highest impact)
Border frame width   → changes the "framed" feeling
Film grain           → subtle texture, hard to pinpoint but felt
Loading — Counter    → confident, numbered feel — dev portfolio vibe
Loading — Curtain    → elegant, branded, puts your name first
Loading — Minimal    → gets out of the way, hero animation shines
```