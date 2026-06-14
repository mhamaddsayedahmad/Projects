# CLAUDE.md

Guidance for Claude Code (claude.ai/code) when working in this repository.

## Design & Frontend Tooling

This repo is provisioned with design-intelligence tooling. Use it for **any** UI/UX
work — visual design decisions, component implementation, layout, color, typography,
accessibility, and review.

### `ui-ux-pro-max` skill — `.claude/skills/ui-ux-pro-max/`

A searchable design-intelligence database: 67 UI styles, 96 color palettes,
57 font pairings, 25 chart types, and a UX-guidelines library, spanning 13 stacks
(React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui,
HTML/CSS, and more).

- **Auto-activates** on UI/UX tasks (build / design / review / improve UI, choose
  colors, fonts, or layout, accessibility checks, chart selection).
- **Query the database directly** when you want specific recommendations:

  ```bash
  # Domain search: product | style | typography | color | landing | chart | ux
  python3 .claude/skills/ui-ux-pro-max/scripts/search.py "<query>" --domain <domain>

  # Stack-specific guidance (html-tailwind default)
  python3 .claude/skills/ui-ux-pro-max/scripts/search.py "<query>" --stack <react|nextjs|vue|svelte|swiftui|flutter|shadcn|...>
  ```

### Magic MCP — `@21st-dev/magic`

AI UI-component generation, configured in `.mcp.json` (project scope) so it loads
automatically in every session.

- The API key is **not** stored in the repo. It is read from the `MAGIC_API_KEY`
  environment variable.
- **Web sessions:** add `MAGIC_API_KEY` to the environment's variables
  (see https://code.claude.com/docs/en/claude-code-on-the-web).
- **Local:** `export MAGIC_API_KEY=...` before launching, or keep a user-scope
  config (`claude mcp add magic --scope user --env API_KEY=... -- npx -y @21st-dev/magic@latest`).

## Recommended workflow for UI work

1. Consult `ui-ux-pro-max` for style, palette, typography, and UX decisions.
2. Generate components with the Magic MCP.
3. Validate the result against the skill's UX guidelines and accessibility notes
   before considering the work done.
