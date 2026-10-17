# StoryCast

An accessible three-page microsite for audio and video storytelling by **Divine Mutesi**. The stories come from visits to rural Rwanda (Isunzu Yacu Village in Burera, and Bigogwe) and the mission of bringing technology into education. Built with semantic HTML5, Sass and vanilla CSS. No frameworks and no JavaScript.

## Project structure
```
storycast/
├── index.html                  Home
├── about.html                  About & Access
├── story/where-learning-begins.html   Story detail
├── sass/
│   ├── _colors.scss            colour tokens
│   ├── _typography.scss        type tokens
│   ├── _spacing.scss           spacing, radius, breakpoints
│   ├── _base.scss              layer order, reset, base, utilities
│   ├── _layout.scss            header, footer, hero, page grids
│   ├── _components.scss        BEM components (incl. container query)
│   └── main.scss               entry file
├── css/main.css (+ .map)       compiled styles
├── assets/media/               photos, video, captions (.vtt), audio
├── assets/transcripts/         plain-text transcript
└── docs/                       Research Document and Documentation (PDF)
```

## Sass architecture
- Tokens live in `_colors`, `_typography` and `_spacing` and are shared with `@use ... as *`.
- **Cascade layers**: `reset, base, layout, components, utilities`, declared once in `_base.scss`.
- **BEM** naming throughout, e.g. `.media-card__heading`, `.btn--primary`.
- **Container query**: `.card-wrapper` is a `container: card / inline-size`; `.media-card` becomes a side-by-side card at 36rem and stacks when its container is narrower.

## Accessibility checklist (WCAG 2.1 AA)
- [x] Landmarks: header, nav, main, article, section, aside, figure/figcaption, footer; one `h1` per page, ordered headings
- [x] Skip link on every page; `aria-current="page"` on the active link; labelled navs
- [x] Video has a `<track kind="captions">` WebVTT file; audio and video have a full transcript plus a downloadable `.txt`
- [x] `figcaption` linked to each player with `aria-describedby`; fallback text inside media elements
- [x] Descriptive `alt` text on every informative image, with `width`/`height` set
- [x] Colour contrast 4.5:1 or higher (white on background 18.1:1, muted text 6.3:1 or higher, button 4.9:1, focus ring 6.5:1)
- [x] Visible `:focus-visible` outline; native controls; focusable scrollable transcript
- [x] Responsive layout, relative units, `prefers-reduced-motion` respected, no autoplay

## Run locally
```bash
git clone https://github.com/divine150-coder/storycast.git
cd storycast
# open index.html in a browser

Recompile Sass after editing:
```bash
npm install -g sass
sass sass/main.scss css/main.css --style=compressed
```

## Notes
- Photos and the library video were taken during visits to Isunzu Yacu Village and Bigogwe.
- The story audio is the author's own recording of the story. The transcript in `assets/transcripts/` should match what is said.
- Design files: Figma sitemap, wireframes and mockups: **https://www.figma.com/design/jxJdBJ9OUts7twpTzecKPd/StoryCast-%E2%80%94-IA---Mockups?node-id=0-1&t=8MjdGsho2GTTeErf-1**
