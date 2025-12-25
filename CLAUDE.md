# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Mintlify documentation site named "AI Agent TR". Mintlify is a documentation platform that uses MDX (Markdown with JSX) for content authoring and provides a modern docs experience with built-in features like code highlighting, API references, and contextual navigation.

## Development Commands

### Local Development
```bash
# Install Mintlify CLI globally (requires Node.js v19+)
npm i -g mint

# Start local development server at http://localhost:3000
mint dev

# Start on custom port
mint dev --port 3333

# Update CLI to latest version
mint update

# Validate links in documentation
mint broken-links
```

### Deployment
Changes pushed to the main branch are automatically deployed to production via the Mintlify GitHub app (configured in the dashboard).

## Architecture & Content Structure

### Configuration
- `docs.json`: Main configuration file controlling site theme, navigation, colors, and global settings
  - Theme colors: primary (#16A34A), light (#07C983), dark (#15803D)
  - Navigation organized into tabs: "Guides" and "API reference"
  - Contextual menu options include copy, view, ChatGPT, Claude, Perplexity, MCP, Cursor, and VSCode integrations

### Content Organization
Documentation is organized into these main directories:

- `ai-tools/`: Documentation about AI coding assistants (Cursor, Claude Code, Windsurf)
- `api-reference/`: API documentation generated from OpenAPI spec
  - `openapi.json`: OpenAPI 3.1.0 specification (example: Plant Store API)
  - `endpoint/`: Individual endpoint documentation pages
- `essentials/`: Core documentation about using Mintlify features
  - Settings, navigation, markdown, code blocks, images, reusable snippets
- `snippets/`: Reusable content snippets that can be included across pages
- `images/` and `logo/`: Static assets

### Key Files
- `index.mdx`: Homepage/introduction
- `quickstart.mdx`: Three-step getting started guide
- `development.mdx`: Local development setup instructions

## Content Authoring

### MDX Files
All documentation pages use MDX format with frontmatter:
```mdx
---
title: "Page Title"
description: "Page description"
---

Content here...
```

### Mintlify Components
The codebase uses Mintlify's built-in components:
- `<Card>`, `<CardGroup>`: Interactive card layouts
- `<Columns>`: Multi-column layouts
- `<Accordion>`, `<AccordionGroup>`: Collapsible content sections
- `<Steps>`, `<Step>`: Step-by-step guides
- `<Frame>`: Image containers
- `<Info>`, `<Tip>`, `<Note>`, `<Warning>`: Callout boxes

### Navigation
Navigation structure is defined in `docs.json` under the `navigation` key. Pages are organized into tabs and groups. To add a new page:
1. Create the MDX file in the appropriate directory
2. Add the file path (without .mdx extension) to the relevant group in `docs.json`

### API Documentation
API endpoints are auto-generated from the OpenAPI specification in `api-reference/openapi.json`. The spec defines a sample Plant Store API with bearer authentication.

## Important Notes

- The site uses a tabbed navigation structure with "Guides" and "API reference" as main tabs
- Local preview updates automatically as files are edited (hot reload)
- The contextual menu is configured to show multiple AI assistant integrations
- Port 3000 is default; if occupied, Mintlify will auto-increment to next available port
- Prerequisites: Node.js version 19 or higher

## Troubleshooting

If encountering "sharp" module errors on darwin-arm64:
1. Remove CLI: `npm remove -g mint`
2. Upgrade to Node v19+
3. Reinstall: `npm i -g mint`

For unknown errors, delete `~/.mintlify` folder and retry `mint dev`.
