# Copilot Instructions

- Project scope: static portfolio site served from docs/ for GitHub Pages; .nojekyll ensures files are served without Jekyll processing.
- Key entry point: docs/portfolio/index.html (currently empty). Build new pages there; keep supporting assets in docs/portfolio (e.g., css/, img/, js/).
- Reserved dirs: docs/client_site and docs/design_style exist but are empty; only use if expanding the site.
- No build tooling or bundler; write plain HTML/CSS/vanilla JS. Assets are served as-is from docs/.
- Node tooling lives in package.json: dev deps htmlhint, stylelint, lint-staged, husky; no runtime deps.
- Install deps with npm install; the prepare script auto-runs husky install.
- Lint workflow: lint-staged runs htmlhint on *.html and stylelint on *.css before commit. No project configs, so default rules apply until .htmlhintrc or .stylelintrc are added.
- If lint-staged or hooks stop running, re-run npm run prepare to reinstall husky hooks.
- Husky layout: scaffolding lives in .husky/_ (h wrapper expects actual hooks in .husky/<hook>). No active hooks are present; add one via npx husky add .husky/pre-commit "npx lint-staged" if you want enforcement.
- GitHub Pages: host from docs/. Keep links/asset paths relative (./foo.png) to avoid broken pages when published.
- Preferred structure: put shared styles in docs/portfolio/css/, scripts in docs/portfolio/js/, and images in docs/portfolio/img/; keep index.html lean and defer heavy inline styles/scripts.
- Accessibility/perf: use semantic HTML tags, include alt text for images, and keep external dependencies minimal unless necessary.
- Testing: no automated tests; validate locally by opening docs/portfolio/index.html in a browser or using a simple static server.
- Version control: node_modules is present locally but should stay out of edits; focus on source in docs/.
- When adding new scripts/commands, place them in package.json under scripts and document briefly in this file or a future README.
