# AGENTS.md

This file provides guidance to OpenCode when working with code in this repository.

## Project: TingTing Networks Landing Page

**Company:** TingTing Networks — Vietnam's #1 Shoppertainment Platform
**Tagline:** Content · Creator · Commerce — Where connection brings impact.
**Domain:** tingtingnetworks.asia
**Repo:** github.com/duonglx/tingting
**Stack:** Single-file HTML, Tailwind CSS CDN, Lucide Icons, vanilla JS
**Current version:** v5 (Apple-inspired bento grid, OLED dark mode, lime green accent)

## Role & Responsibilities

Analyze user requirements, delegate tasks to appropriate sub-agents, ensure cohesive delivery of features that meet specifications and architectural standards.

## Folder Structure

```
/TingTing
├── tingtingnetworks/       # Production source (synced to gh-pages root)
│   └── index.html          # Active released version
├── versions/               # All version archives (edit here)
│   ├── v1/
│   ├── index_v2.html .. index_v5.html
├── plans/                  # Implementation plans & reports
├── docs/                   # Project documentation
```

## Workflows

- Primary workflow: `./.claude/rules/primary-workflow.md`
- Development rules: `./.claude/rules/development-rules.md`
- Orchestration protocols: `./.claude/rules/orchestration-protocol.md`
- Documentation management: `./.claude/rules/documentation-management.md`

## Development Principles

- **YAGNI**: You Aren't Gonna Need It
- **KISS**: Keep It Simple, Stupid
- **DRY**: Don't Repeat Yourself
- Conventional commit format, no AI references
- No mocking or fake implementations

## Design System (v5)

- **Fonts:** Sora (heading) + Plus Jakarta Sans (body)
- **Colors:** Near-black `#050505` bg, lime green `#84CC16` accent, white `#FFFFFF` text
- **Style:** Apple-inspired dark mode, bento grid, glassmorphism, grain texture
- **Icons:** Lucide Icons (SVG, no emojis)
- **Accessibility:** WCAG AA, `prefers-reduced-motion`, 44px touch targets

## Deploy

- **Preview:** push `versions/index_vN.html` to `gh-pages` → `tingtingnetworks.asia/versions/index_vN.html`
- **Production:** copy to root `index.html` on `gh-pages` → `tingtingnetworks.asia`
- GitHub Pages: `gh-pages` branch, custom domain via CNAME
