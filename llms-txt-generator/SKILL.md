---
name: "llms-txt-generator"
description: "Use when the user asks to create, write, generate or audit an llms.txt file for any website, in any sector (ecommerce, local services, global brands, YMYL, B2B)."
---

# llms.txt Generator

Produces a publication-ready `/llms.txt` for any website: a curated, fact-dense Markdown map that tells LLMs and AI search engines who the business is, what it sells, what it costs, who stands behind it, and which pages hold the answers. The standard is an llms.txt that an AI assistant could use to answer most commercial questions about the business correctly without guessing.

Works the same for a national restaurant chain, a global cosmetics group, or a single-site dental practice. The structure is fixed; the sections inside it flex to the business.

## Inputs

- **Required:** the website URL.
- **Optional:** priority pages, markets/countries in scope, current offers, pages to exclude, anything the site owner wants emphasised (endorsements, accreditations). If the user gives none, proceed with sensible defaults and state them.

## Process

### 1. Discover the site (research before writing)

Use your web-fetching tool (or a browser tool if a page needs JavaScript rendering). Never invent content for a page you could not read; if a fetch is blocked, note it and move on rather than working around it.

1. Check for an existing `/llms.txt` and `/llms-full.txt` (improve on it rather than ignore it).
2. Read `/robots.txt` and the XML sitemap(s) to get the full URL inventory and see what is blocked.
3. Read the homepage: main navigation, footer links, hero claims, trust signals (endorsements, awards, accreditations, review scores, years trading).
4. Read the money pages: product/service/category pages, pricing, plans, menus, treatment fees.
5. Read offers/promotions, delivery/shipping, returns, booking or ordering pages.
6. Read About, Team/Experts, Locations/Contact, FAQs, case studies/testimonials, and the blog/resource hub (category archives, pillar guides).
7. Note regulatory or YMYL signals: registrations, licences, clinical reviewers, credentials, compliance statements.

Record for each candidate URL: final canonical URL, page title/H1, what information it actually contains, and whether it is indexable (not noindex, not redirected, not parameterised).

### 2. Select and group pages

- Aim for roughly 15-60 links. Small local sites may have 10-20; large brands should curate to the pages that best answer real customer questions, not dump the sitemap.
- Include: homepage, every core product/service page (or category hubs for large catalogues), pricing, offers, key people/experts, about/trust pages, locations, delivery/booking, FAQs, top guides/pillar content, case studies/reviews, main resource archives.
- Exclude: cart, checkout, account, login, search results, tag pages, paginated URLs, thin legal boilerplate (unless the privacy/terms page is commercially relevant), duplicate or parameter URLs, anything blocked in robots.txt or noindexed.
- Group links into H2 sections that mirror how the business is actually organised and how a customer thinks, not the CMS folder structure.

### 3. Write the file using the structure below

### 4. Verify, then deliver

- Re-check every price, offer, code, name and credential against the page it came from.
- Confirm every URL is absolute, HTTPS, canonical (matching trailing-slash convention) and resolves.
- Save as `llms.txt` (UTF-8, plain text/Markdown) in the outputs location for your environment (e.g. `<domain>/llms.txt`), and share it with the user.
- Reply with a short note: pages covered, anything assumed or unverifiable, time-sensitive items (prices/offers) that need a refresh cadence, and deployment reminder (serve at `https://domain/llms.txt`, `Content-Type: text/plain; charset=utf-8`, not blocked in robots.txt).

## File structure

Sections marked **(always)** appear in every file. Sections marked **(if applicable)** appear only when the site has real content for them. Never add an empty section or a placeholder.

```
# {Brand name}                                              (always)

> {One-sentence entity summary}                               (always)

## Key Facts                                                  (always)

## Pricing Overview                                           (if public pricing)

## Offers                                                     (if live promotions)

## Home                                                       (always)

## {Products | Services | Treatments | Menu | Brands | ...}   (always, 1+ sections)

## {People: Team | Experts | Clinicians | Leadership}         (if applicable)

## {Segment sections: Business/Trade, Locations, ...}         (if applicable)

## {Topic hubs / pillar guides}                               (if applicable)

## {Logistics: Delivery | Booking | Returns | Opening Hours}  (if applicable)

## About Us                                                   (always if page exists)

## FAQs                                                       (if applicable)

## {Case Studies | Reviews | Testimonials}                    (if applicable)

## Resources                                                  (if applicable)
```

### H1
The brand name exactly as the business writes it. Nothing else.

### Summary blockquote
One sentence, roughly 25-45 words, answering: **what type of business, where, what it offers, for whom, and its strongest differentiator/trust signal.** Pattern:

> {Brand} is a {location/market}-based {business type} specialising in {core offerings} {differentiator or trust signal} to {outcome for target audience}.

Adapt the pattern, but keep it one factual sentence. No superlatives the site cannot back up.

### Key Facts
Bold-label bullet list. Use the fields that fit; add sector-relevant ones; drop ones that do not apply.

Core fields (use nearly always):
- **Company** / **Brand**
- **Website**
- **Location** (HQ, or full address for local businesses; markets served for international brands)
- **Industry** (use slashes for synonyms people search: e.g. "Dentistry / Dental Practice / Cosmetic Dentistry")
- **Target Audience**
- **Core Services** or **Core Products**
- **Availability** (opening hours, 24/7 service, delivery areas, booking channels)
- **Pricing Model** (subscription, per-item, per-treatment, quote-based, public vs private (e.g. NHS vs private in the UK), free delivery thresholds, tax relief)

Sector-relevant extras (examples, pick what applies):
- **Parent Company / Brands Portfolio** (multi-brand groups)
- **Founded**, **Number of Locations**
- **Accreditations / Regulated By** (e.g. professional body, regulator, registration numbers shown on the site)
- **Endorsements / Awards**
- **Contact** (phone/email as published, for local businesses)
- **Ordering Channels** (app, delivery partners, click and collect)
- **Languages / Countries**

### Pricing Overview (if public pricing)
1. Open with a pointer to the live pricing page as the source of truth: "For the most up-to-date pricing, always refer directly to the [{Pricing page title}]({URL}) page."
2. State the tax basis if relevant (e.g. inc./exc. VAT, sales tax, exemptions).
3. One bullet per plan/product/treatment: **{Name}**: price(s) with billing period and currency exactly as shown, then one clause on what is included.
4. Include one-off fees (setup, delivery, consultation, deposit) as their own bullets.
5. Use "from" / "starts from" when the site does. Never estimate, round, or infer a price. For large catalogues, give category-level "from" prices only if the site states them; otherwise describe the pricing model and link to the pages.

### Offers (if live promotions)
Open with the same pointer to the offers page, then number each offer:

```
- **Offer 1: {Offer name}**
    - **Description**: {what the customer gets}
    - **Requirement**: {code, minimum spend, plan type, eligibility}
    - **Applicable {Plans/Products/Locations}**: {scope, and explicit exclusions}
```

Always state exclusions explicitly ("does not apply to X"); this is what stops AI assistants misquoting offers. Include end dates when shown. If no live offers, omit the section.

### Link sections
Every link line uses exactly this format:

```
- [{Page title or clear descriptive title}]({absolute canonical URL}): {Description}
```

Description rules:
- One sentence, about 12-35 words.
- Describe **what information the page contains** so an LLM knows when to cite it: features, pricing, specifications, eligibility, credentials, process, coverage, cut-off times, compatibility.
- Use concrete nouns and named entities (product names, people, credentials, locations, standards), not adjectives.
- Neutral, third-person, factual. Remove sales fluff ("amazing", "best-in-class") unless quoting a verifiable claim.
- Use the page's existing title when it is clear; rewrite it into a descriptive title when it is vague (e.g. "Archives" becomes "Health & Wellbeing Archives").

Ordering: within each section, lead with the hub/comparison page, then individual items. Order sections by commercial importance: Home, core offering, people/trust, segments, topic hubs, logistics, about, FAQs, proof, resources.

### People / expertise section
For each key person: `[{Name} | {Role} at {Brand}]({URL}): {what the profile covers: responsibilities, credentials, specialism}`. Prioritise people who carry trust: founders, medical/clinical reviewers, qualified practitioners, named experts, ambassadors. Include credentials and post-nominals exactly as the site states them. Essential for YMYL sites.

## Sector adaptation guide

The skeleton never changes; these are the typical sections and Key Facts to reach for.

| Business type | Core sections | Key Facts / pricing emphasis |
|---|---|---|
| Local service (dentist, clinic, solicitor, trades) | Treatments/Services, Fees, Team/Practitioners (with registrations), Location & Opening Hours, New Patients/Booking, Emergency, Reviews | Full address, phone, hours, regulator/registration, public vs private (e.g. NHS) or insured vs self-pay, finance options, areas served |
| Restaurant / food chain | Menu (by category), Deals, Locations/Store Finder, Delivery & Collection, Allergens & Nutrition, App/Rewards, Careers, Franchising | Number of locations, ordering channels, delivery partners, dietary ranges (vegan, gluten-free) |
| Global consumer brand (beauty, fashion, CPG) | Brands/Ranges, Product Categories, Ingredients/Science, Sustainability, Where to Buy, Country Sites, Investors/Corporate, Press | Parent company, brand portfolio, markets, certifications, research credentials |
| Ecommerce retailer | Category hubs, Best Sellers, Buying Guides, Delivery, Returns, Size Guides, Trade/B2B | Delivery thresholds and speeds, returns window, payment/finance options |
| SaaS / B2B | Product/Features, Pricing & Plans, Integrations, Use Cases/Industries, Customers/Case Studies, Security & Compliance, Docs, Support | Plan tiers, free trial, compliance standards, deployment options |
| YMYL (health, finance, legal, care) | Services, Expert/Clinical team, Reviewed-by/Editorial policy, Regulatory info, Guides, FAQs | Regulator, licences, reviewer credentials, eligibility, risk disclosures as stated on site |

## Quality bar (check before delivering)

- [ ] H1, one-sentence blockquote, Key Facts, Home and at least one core-offering section present.
- [ ] Every fact, price, code, name and credential traceable to a page read during research. Nothing invented or estimated.
- [ ] Prices and offers point to their live source page and state billing period, currency, tax basis and exclusions.
- [ ] Every link absolute, HTTPS, canonical, indexable, and not a duplicate.
- [ ] Every link has a factual description of the page's content; no bare links, no marketing fluff.
- [ ] Sections reflect the business, not a copy of another site's sections; no empty sections.
- [ ] Language, spelling and currency match the site's market (UK English and GBP for UK sites, etc.).
- [ ] Trust signals (people, credentials, accreditations, endorsements) surfaced in the summary, Key Facts and a dedicated section where they exist.
- [ ] File is clean Markdown: one blank line between blocks, `-` bullets, 4-space indent for nested offer fields, no HTML.

## Illustrative example (fictional business)

```
# Riverside Dental Care

> Riverside Dental Care is a family-run dental practice in Riverton, offering NHS and private general, cosmetic and emergency dentistry, with GDC-registered dentists and an in-house implant clinician, for patients of all ages.

## Key Facts

- **Company**: Riverside Dental Care
- **Website**: https://www.riversidedental.example/
- **Location**: 12 Example Street, Riverton, RT1 1AA, United Kingdom
- **Industry**: Dentistry / Dental Practice / Cosmetic Dentistry
- **Target Audience**: Adults, children and families in Riverton and surrounding areas
- **Core Services**: Check-ups, hygiene, fillings, Invisalign, whitening, dental implants, emergency appointments
- **Availability**: Monday-Friday 8am-6pm, Saturday 9am-1pm; same-day emergency slots
- **Pricing Model**: NHS band charges and private fee list; 0% finance on treatments over £1,000
- **Regulated By**: Care Quality Commission (CQC); all dentists registered with the General Dental Council (GDC)

## Pricing Overview

For the most up-to-date fees, always refer directly to the [Fees and Finance](https://www.riversidedental.example/fees/) page.

- **Private Examination**: £65.00 per visit. Includes oral cancer screening and treatment plan.
- **Hygienist Appointment**: £75.00 per 30-minute session.
- **Single Dental Implant**: From £2,450.00, including crown.

## Home

- [Riverside Dental Care | Dentist in Riverton](https://www.riversidedental.example/): Practice homepage covering NHS and private services, opening hours, new patient registration and patient reviews.

## Treatments

- [All Dental Treatments](https://www.riversidedental.example/treatments/): Overview of general, cosmetic, orthodontic and restorative treatments offered, with links to individual treatment pages and fees.
- [Dental Implants](https://www.riversidedental.example/treatments/dental-implants/): Implant procedure stages, suitability criteria, recovery timeline, clinician credentials and private pricing with finance options.

## Our Dentists

- [Dr Jane Doe BDS | Principal Dentist](https://www.riversidedental.example/team/jane-doe/): Profile of the principal dentist, including GDC registration, qualifications and special interest in implant dentistry.
```

The example shows the standard, not the content: never reuse its sections, wording or fields for a real business without evidence from that business's own site.
