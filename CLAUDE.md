# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the official documentation site for **AI Agent TR** (AI Çağrı Merkezi Platformu), an AI-powered call center platform. The documentation is built with Mintlify and is entirely in **Turkish**.

**Platform Purpose**: AI Agent TR provides businesses with intelligent voice AI assistants for automating and optimizing customer communications. The platform includes CRM, campaign management, pipeline management, and call monitoring features.

**Documentation URL**: https://docs.aiagenttr.com

**Key Characteristics**:
- All content is in Turkish (UTF-8 encoding)
- 15+ comprehensive documentation articles covering all platform features
- Two reference documents for form fields and validation rules
- Image placeholders for future screenshots
- Three main navigation tabs: Kullanım Kılavuzu (User Guide), Referans (Reference), AI Araçları (AI Tools)

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
  - Turkish navigation labels
  - Three main tabs: "Kullanım Kılavuzu", "Referans", "AI Araçları"
  - Contextual menu options include copy, view, ChatGPT, Claude, Perplexity, and Cursor integrations
  - Global anchors: Ana Sayfa (https://aiagenttr.com), Platform (https://app.aiagenttr.com)
  - Support email placeholder: support@aiagenttr.com
  - Social media placeholders: Twitter/X, GitHub, LinkedIn

### Content Organization

Documentation is organized into these main directories:

**Core Documentation (Kullanım Kılavuzu Tab)**:
- `getting-started/`: Platform introduction, API key setup, dashboard, organization settings (4 files)
- `voice-ai-agents/`: AI agent creation and knowledge base management (2 files)
- `customer-management/`: Customer addition and interaction tracking (2 files)
- `campaigns/`: Campaign creation and management (1 file)
- `call-monitoring/`: Call recordings and transcripts (1 file)
- `phone-numbers/`: SIP trunk setup and phone number management (1 file)
- `pipeline-management/`: Sales and support pipeline management (4 files)
- `analytics/`: Coming soon page (1 file)
- `troubleshooting/`: Coming soon page (1 file)

**Reference Documentation (Referans Tab)**:
- `reference/`: Form fields reference and required fields table (2 files)

**AI Tools (AI Araçları Tab)**:
- `ai-tools/`: Mintlify integration guides for Cursor, Claude Code, and Windsurf (3 files - preserved from template for reference)

**Assets**:
- `images/`: Image placeholders for platform screenshots (to be added)
- `logo/`: Light and dark mode logos (need AI Agent TR branding)
- `favicon.svg`: Favicon (needs AI Agent TR branding)

### Key Files

**Root Pages**:
- `index.mdx`: Homepage with platform overview and feature cards
- `quickstart.mdx`: 3-step quickstart guide (account setup, AI agent creation, test call)

**Critical Configuration**:
- `docs.json`: Navigation structure and theme settings (Turkish labels)
- `CLAUDE.md`: This file

**Important Notes**:
- Template files (`essentials/`, `api-reference/`, original `index.mdx`) have been removed
- All content migrated from `/Users/ugurgokdere/Developer/ai-call-center-platform-new/knowledge_base`

## Content Authoring

### MDX Files

All documentation pages use MDX format with Turkish frontmatter:
```mdx
---
title: "Türkçe Başlık"
description: "Türkçe açıklama"
---

Content here in Turkish...
```

### Mintlify Components

The documentation extensively uses Mintlify's built-in components:

**Layout Components**:
- `<Card>`, `<CardGroup>`: Feature highlights and navigation cards
- `<Tabs>`, `<Tab>`: Alternative views and options
- `<Accordion>`, `<AccordionGroup>`: FAQ sections and collapsible content
- `<Steps>`, `<Step>`: Step-by-step guides (heavily used throughout)

**Callout Components**:
- `<Info>`: General information
- `<Tip>`: Best practices and recommendations
- `<Note>`: Important notes
- `<Warning>`: Warnings and critical information

**Media Components**:
- `<Frame>`: Image containers with placeholders

### Image Placeholders

All images are currently placeholders with descriptive Turkish notes:
```mdx
<Frame>
  <img src="/images/placeholder-name.png" alt="Türkçe açıklama" />
</Frame>

<Note>
  Ekran görüntüsü eklenecek: [What the screenshot should show]
</Note>
```

**Naming Convention**: `/images/[category]-[description]-[variant].png`

Examples:
- `/images/quickstart-api-setup.png`
- `/images/placeholder-agent-created.png`
- `/images/placeholder-transcript.png`

### Navigation

Navigation structure is defined in `docs.json` under the `navigation.tabs` key. The structure follows:

```json
{
  "tabs": [
    {
      "tab": "Kullanım Kılavuzu",
      "groups": [
        {
          "group": "Başlangıç",
          "pages": ["index", "quickstart", "getting-started/...", ...]
        },
        {
          "group": "Sesli Yapay Zeka Ajanlar",
          "pages": ["voice-ai-agents/..."]
        },
        // ... more groups
      ]
    },
    {
      "tab": "Referans",
      "groups": [...]
    },
    {
      "tab": "AI Araçları",
      "groups": [...]
    }
  ]
}
```

To add a new page:
1. Create the MDX file in the appropriate directory with Turkish frontmatter
2. Add the file path (without .mdx extension) to the relevant group in `docs.json`
3. Ensure internal links use the format `/category/filename`

### Internal Links

Use Mintlify's path-based linking:
```mdx
[Link text](/getting-started/platform-introduction)
[Another link](/voice-ai-agents/create-agent)
```

**Important**: No `.mdx` extension in links.

## Platform-Specific Terminology

### Turkish Terms
- **AI Agent**: Sesli yapay zeka asistanı
- **Pipeline**: İş akışı sistemi
- **Ticket**: Müşteri kaydı
- **Stage**: Aşama
- **Campaign**: Kampanya
- **SIP Trunk**: Telefon altyapısı
- **E.164 Format**: Uluslararası telefon numarası formatı (+905301234567)

### Key Platform Concepts

**AI Agents**:
- Voice AI assistants for automated calling
- Configurable with greeting messages, system prompts, and knowledge bases
- Can be assigned to pipelines
- Support escalation/forwarding to human agents

**Pipelines**:
- Sales Pipeline: Lead → Qualified → Proposal → Negotiation → Won/Lost
- Service Pipeline: New → In Progress → Waiting → Resolved → Closed
- Tickets move through stages
- Drag-and-drop interface

**Campaigns**:
- Automated outbound calling
- Requires: AI Agent, phone number, call list
- Configurable: concurrent calls, delay between calls, working hours

**SIP Trunk**:
- VoIP infrastructure for phone calls
- Protocols: UDP, TCP, TLS, TLS/SRTP
- Gateways for redundancy

**Validation**:
- E.164 phone format: +[country code][area code][number]
- Form validation rules documented in `/reference/form-fields.mdx`

## Important Notes

### CRITICAL: API Provider Confidentiality
- **VAPI is the backend provider but MUST NEVER be exposed to customers**
- All references to "VAPI" have been removed from customer-facing documentation
- Use generic terms: "Platform API", "API bağlantısı", "AI servisi"
- API key setup is **automatic** - customers do not manually configure API keys
- Documentation reflects automatic setup, not manual entry

### Language and Encoding
- **All content is in Turkish** - preserve exact Turkish characters (ç, ğ, ı, ö, ş, ü)
- UTF-8 encoding is critical
- Test with Turkish text search to ensure proper encoding

### Branding
- Logo and favicon need to be replaced with AI Agent TR branded versions
- Current files are placeholders from Mintlify template
- Maintain dual-mode support (light/dark)

### Placeholders
The following require updates before production:
- [ ] Replace all `/images/placeholder-*.png` with actual screenshots
- [ ] Update logo files (`/logo/light.svg`, `/logo/dark.svg`)
- [ ] Update favicon (`/favicon.svg`)
- [ ] Verify social media URLs in `docs.json` (Twitter/X, GitHub, LinkedIn)
- [ ] Confirm support email in navbar

### Coming Soon Pages
Two categories have placeholder "coming soon" pages:
- `analytics/coming-soon.mdx`
- `troubleshooting/coming-soon.mdx`

These should be updated with actual content when available.

### Migration Source
Original content migrated from:
`/Users/ugurgokdere/Developer/ai-call-center-platform-new/knowledge_base`

The knowledge base scripts (JIRA integration) are no longer relevant after migration to Mintlify.

## Troubleshooting

### General Mintlify Issues
If encountering "sharp" module errors on darwin-arm64:
1. Remove CLI: `npm remove -g mint`
2. Upgrade to Node v19+
3. Reinstall: `npm i -g mint`

For unknown errors, delete `~/.mintlify` folder and retry `mint dev`.

### Turkish Character Issues
If Turkish characters appear garbled:
1. Verify file encoding is UTF-8
2. Check browser rendering settings
3. Ensure Mintlify version is up to date

### Link Validation
Run `mint broken-links` to check for:
- Broken internal links
- Missing pages
- Incorrect path references

### Image Placeholders
All placeholder images will show broken image icons until replaced. This is expected behavior during development.

## Testing Checklist

Before deployment:
- [ ] Run `mint dev` and verify all pages load
- [ ] Test navigation between all tabs and groups
- [ ] Verify Turkish content renders correctly
- [ ] Check all internal links work
- [ ] Run `mint broken-links` to validate
- [ ] Test search functionality with Turkish keywords
- [ ] Verify mobile responsiveness
- [ ] Check that coming-soon pages display properly
- [ ] Confirm contextual menu options work
- [ ] Test global anchor links (Ana Sayfa, Platform)

## Future Enhancements

Planned additions:
- Actual platform screenshots to replace placeholders
- Analytics documentation content
- Troubleshooting documentation content
- Video tutorials (if needed)
- API documentation (if platform exposes public APIs)
- Multi-language support (if international expansion)


# Mintlify documentation

## Working relationship
- You can push back on ideas-this can lead to better documentation. Cite sources and explain your reasoning when you do so
- ALWAYS ask for clarification rather than making assumptions
- NEVER lie, guess, or make up information

## Project context
- Format: MDX files with YAML frontmatter
- Config: docs.json for navigation, theme, settings
- Components: Mintlify components

## Content strategy
- Document just enough for user success - not too much, not too little
- Prioritize accuracy and usability of information
- Make content evergreen when possible
- Search for existing information before adding new content. Avoid duplication unless it is done for a strategic reason
- Check existing patterns for consistency
- Start by making the smallest reasonable changes

## Frontmatter requirements for pages
- title: Clear, descriptive page title
- description: Concise summary for SEO/navigation

## Writing standards
- Second-person voice ("you")
- Prerequisites at start of procedural content
- Test all code examples before publishing
- Match style and formatting of existing pages
- Include both basic and advanced use cases
- Language tags on all code blocks
- Alt text on all images
- Relative paths for internal links

## Git workflow
- NEVER use --no-verify when committing
- Ask how to handle uncommitted changes before starting
- Create a new branch when no clear branch exists for changes
- Commit frequently throughout development
- NEVER skip or disable pre-commit hooks

## Do not
- Skip frontmatter on any MDX file
- Use absolute URLs for internal links
- Include untested code examples
- Make assumptions - always ask for clarification