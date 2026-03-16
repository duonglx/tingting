# Development Rules

**IMPORTANT:** Analyze the skills catalog and activate the skills that are needed for the task during the process.
**IMPORTANT:** You ALWAYS follow these principles: **YAGNI (You Aren't Gonna Need It) - KISS (Keep It Simple, Stupid) - DRY (Don't Repeat Yourself)**

## General
- **File Naming**: Use kebab-case for file names with a meaningful name that describes the purpose of the file, doesn't matter if the file name is long, just make sure when LLMs read the file names while using Grep or other tools, they can understand the purpose of the file right away without reading the file content.
- **File Size Management**: Keep individual code files under 200 lines for optimal context management
  - Split large files into smaller, focused components/modules
  - Use composition over inheritance for complex widgets
  - Extract utility functions into separate modules
  - Create dedicated service classes for business logic
- When looking for docs, activate `docs-seeker` skill (`context7` reference) for exploring latest docs.
- Use `gh` bash command to interact with Github features if needed
- Use `psql` bash command to query Postgres database for debugging if needed
- Use `ai-multimodal` skill for describing details of images, videos, documents, etc. if needed
- Use `ai-multimodal` skill and `imagemagick` skill for generating and editing images, videos, documents, etc. if needed
- Use `sequential-thinking` and `debug` skills for sequential thinking, analyzing code, debugging, etc. if needed
- **[IMPORTANT]** Follow the codebase structure and code standards in `./docs` during implementation.
- **[IMPORTANT]** Do not just simulate the implementation or mocking them, always implement the real code.

## Code Quality Guidelines
- Read and follow codebase structure and code standards in `./docs`
- Don't be too harsh on code linting, but **make sure there are no syntax errors and code are compilable**
- Prioritize functionality and readability over strict style enforcement and code formatting
- Use reasonable code quality standards that enhance developer productivity
- Use try catch error handling & cover security standards
- Use `code-reviewer` agent to review code after every implementation

## Pre-commit/Push Rules
- Run linting before commit
- Run tests before push (DO NOT ignore failed tests just to pass the build or github actions)
- Keep commits focused on the actual code changes
- **DO NOT** commit and push any confidential information (such as dotenv files, API keys, database credentials, etc.) to git repository!
- Create clean, professional commit messages without AI references. Use conventional commit format.

## Project Folder Structure
```
/TingTing
├── tingtingnetworks/    # Production site (tingtingnetworks.asia)
│   └── index.html       # Active production version (overwritten on release)
├── versions/            # All version archives
│   ├── v1/              # Legacy v1 folder
│   ├── index_v2.html
│   ├── index_v3.html
│   ├── index_v4.html
│   └── index_v5.html
└── ...
```

## Deploy Modes

### Preview (đánh version / upload GitHub Pages / push preview)
User says: "đánh version", "upload lên github pages", "push preview", "deploy preview"
- Purpose: push version lên `gh-pages` để xem trước, **KHÔNG** ghi đè production
- URL: `https://tingtingnetworks.asia/versions/index_vN.html`
- Steps:
  1. Save to `versions/index_vN.html` + sync to `tingtingnetworks/index.html` on `main`
  2. Commit to `main` with conventional message
  3. Tag: `git tag -a vX.Y.Z` (increment from `git tag --sort=-v:refname | head -1`)
  4. Push: `git push origin main && git push origin vX.Y.Z`
  5. Deploy preview to `gh-pages`:
     ```
     git checkout gh-pages
     git checkout main -- versions/index_vN.html
     git add versions/ && git commit -m "feat: deploy vN preview"
     git push origin gh-pages
     git checkout main
     ```
  6. Confirm preview URL

### Release to Production (release / public / go live)
User says: "release vN", "release version N", "public lên production", "go live"
- Purpose: ghi đè root `index.html` trên `gh-pages` → live tại custom domain
- URL: `https://tingtingnetworks.asia`
- Steps:
  1. Ensure version exists in `versions/index_vN.html`
  2. Sync: `cp versions/index_vN.html tingtingnetworks/index.html`
  3. Commit + push to `main`
  4. Deploy to `gh-pages` — overwrite root `index.html`:
     ```
     git checkout gh-pages
     git checkout main -- tingtingnetworks/index.html
     cp tingtingnetworks/index.html index.html
     git add index.html tingtingnetworks/ && git commit -m "release: vN to production"
     git push origin gh-pages
     git checkout main
     ```
  5. Confirm: `https://tingtingnetworks.asia` now serves vN
- **Custom domain**: CNAME = `tingtingnetworks.asia`, DNS A records → GitHub Pages IPs

## Code Implementation
- Write clean, readable, and maintainable code
- Follow established architectural patterns
- Implement features according to specifications
- Handle edge cases and error scenarios
- **DO NOT** create new enhanced files, update to the existing files directly.

## Visual Aids
- Use `/preview --explain` when explaining unfamiliar code patterns or complex logic
- Use `/preview --diagram` for architecture diagrams and data flow visualization
- Use `/preview --slides` for step-by-step walkthroughs and presentations
- Use `/preview --ascii` for terminal-friendly diagrams (no browser needed to understand)
- **Plan context:** Active plan determined from `## Plan Context` in hook injection; visuals save to `{plan_dir}/visuals/`
- If no active plan, fallback to `plans/visuals/` directory
- For Mermaid diagrams, use `/mermaidjs-v11` skill for v11 syntax rules
- See `primary-workflow.md` → Step 6 for workflow integration