# GEMINI.md

## Project: TingTing Networks Landing Page

**Company:** TingTing Networks — Vietnam's #1 Shoppertainment Platform
**Tagline:** Content · Creator · Commerce — Where connection brings impact.
**Domain:** tingtingnetworks.asia
**Repo:** github.com/duonglx/tingting
**Stack:** Single-file HTML, Tailwind CSS CDN, Lucide Icons, vanilla JS
**Current version:** v5 (Apple-inspired bento grid, OLED dark mode, lime green accent)

## Folder Structure

```
/TingTing
├── tingtingnetworks/       # Production source (synced to gh-pages root)
│   └── index.html          # Active released version
├── versions/               # All version archives
│   ├── v1/
│   ├── index_v2.html
│   ├── index_v3.html
│   ├── index_v4.html
│   └── index_v5.html       # Latest — edit this file
├── plans/                  # Implementation plans & reports
├── docs/                   # Project documentation
├── CLAUDE.md               # Claude Code instructions
├── AGENTS.md               # OpenCode instructions
└── GEMINI.md               # This file (Gemini/Antigravity instructions)
```

## Development Rules

- Follow rules in `.claude/rules/development-rules.md`
- **YAGNI / KISS / DRY** principles
- Keep code clean, readable, maintainable
- No mocking or fake implementations
- Use conventional commit format

## Design System (v5)

- **Fonts:** Sora (heading) + Plus Jakarta Sans (body)
- **Colors:** Near-black `#050505` bg, lime green `#84CC16` accent, white `#FFFFFF` text
- **Style:** Apple-inspired dark mode, bento grid, glassmorphism nav, grain texture
- **Icons:** Lucide Icons (SVG, no emojis)
- **Accessibility:** WCAG AA compliant, `prefers-reduced-motion`, 44px touch targets

## Deploy Workflow

### Preview (đánh version / push preview)
1. Edit `versions/index_vN.html`
2. Sync to `tingtingnetworks/index.html`
3. Commit + tag `vX.Y.Z` on `main`, push
4. Deploy to `gh-pages`: only push `versions/` folder
5. Preview URL: `https://tingtingnetworks.asia/versions/index_vN.html`

### Release to Production (release vN / go live)
1. Copy `tingtingnetworks/index.html` to root `index.html` on `gh-pages`
2. Push `gh-pages`
3. Live at: `https://tingtingnetworks.asia`

## Key Info

- GitHub Pages serves from `gh-pages` branch, root `/`
- Custom domain: `tingtingnetworks.asia` (CNAME on gh-pages)
- Contact: partnership@tingting.asia, +84 901807346
- Address: 25A Tu Xuong, District 3, Ho Chi Minh City
