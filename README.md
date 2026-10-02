# llms-txt-builder

A Claude skill that generates a publication-ready `llms.txt` for any website, in any sector: ecommerce, local services, global brands, YMYL and B2B.

The skill reads the site first (existing llms.txt, robots.txt, sitemap, money pages, team, offers, FAQs) and then writes a curated, fact-dense Markdown file. It follows one fixed structure, and the sections inside that structure adapt to the business:

- `# Brand` heading and a one-sentence entity summary
- **Key Facts**: company, website, location, industry, audience, core offering, availability, pricing model, plus fields for the sector
- **Pricing Overview** and **Offers**, only when the site publishes them, with a link to the live source and any exclusions stated
- Grouped page links in the form `- [Title](URL): what the page contains`
- People, credentials and trust signals for E-E-A-T, especially on YMYL sites

## Install

1. Download the `llms-txt-generator` folder.
2. Upload it as a skill in Claude, or copy it into `~/.claude/skills/` for Claude Code.

## Use

> Create an llms.txt for https://www.example.com

You get `llms.txt` plus a short note covering the pages included, anything that couldn't be verified, and which time-sensitive items (prices, offers) need refreshing.

## Files

- `llms-txt-generator/SKILL.md`: the skill instructions, template, sector adaptation guide and quality checklist.
