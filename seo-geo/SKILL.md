---
name: seo-geo
description: SEO & GEO (Generative Engine Optimization) for websites. Evaluate keywords, produce schema markup, and optimize for AI-powered search engines (ChatGPT, Perplexity, Gemini, Copilot, Claude) alongside traditional search (Google, Bing). Employ when the user seeks to boost search visibility, search optimization, search ranking, AI visibility, ChatGPT ranking, Google AI Overview, indexing, JSON-LD, meta tags, or keyword research.
---

# SEO/GEO Optimization Skill

End-to-end SEO and GEO (Generative Engine Optimization) for websites. Optimize for both conventional search engines (Google, Bing) and AI-driven search platforms (ChatGPT, Perplexity, Gemini, Copilot, Claude).

## Quick Reference

**GEO = Generative Engine Optimization** — Tailoring content so that AI search engines cite it.

**Core Insight:** AI search engines do not rank pages — they **cite sources**. Being cited is the new equivalent of "ranking #1".

## Workflow

### Step 1: Website Audit

Obtain the target URL and assess its current SEO/GEO standing.

**Basic SEO Audit (Free):**
```bash
python3 scripts/seo_audit.py "https://example.com"
```
**Use this for**: A rapid technical SEO check covering title, meta, H1, robots, sitemap, and load time. No API key needed.

---

**Inspect Meta Tags:**
```bash
curl -sL "https://example.com" | grep -E "<title>|<meta name=\"description\"|<meta property=\"og:|application/ld\+json" | head -20
```

**Use this for**: A quick look at essential meta tags and schema markup present on any webpage.

---

**Inspect robots.txt:**
```bash
curl -s "https://example.com/robots.txt"
```

**Use this for**: Confirming which bots are permitted or blocked. This is critical for ensuring AI search crawlers can access your site.

---

**Inspect sitemap:**
```bash
curl -s "https://example.com/sitemap.xml" | head -50
```

**Use this for**: Verifying sitemap structure and confirming all significant pages are listed for search engine discovery.

**Confirm AI Bot Access:**
```
# These bots should be allowed in robots.txt:
- Googlebot (Google)
- Bingbot (Bing/Copilot)
- PerplexityBot (Perplexity)
- ChatGPT-User (ChatGPT with browsing)
- ClaudeBot / anthropic-ai (Claude)
- GPTBot (OpenAI)
```

### Step 2: Keyword Research

Leverage **WebSearch** to investigate target keywords:

```
WebSearch: "{keyword} keyword difficulty site:ahrefs.com OR site:semrush.com"
WebSearch: "{keyword} search volume 2026"
WebSearch: "site:{competitor.com} {keyword}"
```

**Evaluate:**
- Search volume and difficulty
- Competitor keyword strategies
- Long-tail keyword opportunities
- International keyword conflicts (e.g., "OPC" = industrial automation in English markets)

### Step 3: GEO Optimization (AI Search Engines)

Implement the **9 Princeton GEO Methods** (see [references/geo-research.md](./references/geo-research.md)):

| Method | Visibility Boost | How to Apply |
|--------|-----------------|--------------|
| **Cite Sources** | +40% | Add authoritative citations and references |
| **Statistics Addition** | +37% | Include specific numbers and data points |
| **Quotation Addition** | +30% | Add expert quotes with attribution |
| **Authoritative Tone** | +25% | Use confident, expert language |
| **Easy-to-understand** | +20% | Simplify complex concepts |
| **Technical Terms** | +18% | Include domain-specific terminology |
| **Unique Words** | +15% | Increase vocabulary diversity |
| **Fluency Optimization** | +15-30% | Improve readability and flow |
| ~~Keyword Stuffing~~ | **-10%** | **AVOID - hurts visibility** |

**Optimal Combination:** Fluency + Statistics = Maximum boost

**Produce FAQPage Schema** (+40% AI visibility):
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [{
    "@type": "Question",
    "name": "What is [topic]?",
    "acceptedAnswer": {
      "@type": "Answer",
      "text": "According to [source], [answer with statistics]."
    }
  }]
}
```

**Optimize Content Structure:**
- Adopt "answer-first" format (direct answer at the top)
- Maintain clear H1 > H2 > H3 hierarchy
- Use bullet points and numbered lists
- Employ tables for comparison data
- Keep paragraphs short (2-3 sentences max)

### Step 4: Traditional SEO Optimization

**Meta Tags Template:**
```html
<title>{Primary Keyword} - {Brand} | {Secondary Keyword}</title>
<meta name="description" content="{Compelling description with keyword, 150-160 chars}">
<meta name="keywords" content="{keyword1}, {keyword2}, {keyword3}">

<!-- Open Graph -->
<meta property="og:title" content="{Title}">
<meta property="og:description" content="{Description}">
<meta property="og:image" content="{Image URL 1200x630}">
<meta property="og:url" content="{Canonical URL}">
<meta property="og:type" content="website">

<!-- Twitter Cards -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="{Title}">
<meta name="twitter:description" content="{Description}">
<meta name="twitter:image" content="{Image URL}">
```

**JSON-LD Schema** (see [references/schema-templates.md](./references/schema-templates.md)):
- WebPage / Article for content pages
- FAQPage for FAQ sections
- Product for product pages
- Organization for about pages
- SoftwareApplication for tools/apps

**Content Checklist:**
- [ ] H1 contains primary keyword
- [ ] Images have descriptive alt text
- [ ] Internal links to related content
- [ ] External links have `rel="noopener noreferrer"`
- [ ] Content is mobile-friendly
- [ ] Page loads in < 3 seconds

### Step 5: Validate & Monitor

**Schema Validation:**
```bash
# Open Google Rich Results Test
open "https://search.google.com/test/rich-results?url={encoded_url}"

# Open Schema.org Validator
open "https://validator.schema.org/?url={encoded_url}"
```

**Verify Indexing Status:**
```bash
# Google (use Search Console API or manual check)
open "https://www.google.com/search?q=site:{domain}"

# Bing
open "https://www.bing.com/search?q=site:{domain}"
```

**Produce Report:**
```markdown
## SEO/GEO Optimization Report

### Current Status
- Meta Tags: ✅/❌
- Schema Markup: ✅/❌
- AI Bot Access: ✅/❌
- Mobile Friendly: ✅/❌
- Page Speed: X seconds

### Recommendations
1. [Priority 1 action]
2. [Priority 2 action]
3. [Priority 3 action]

### GEO Optimizations Applied
- [ ] FAQPage schema added
- [ ] Statistics included
- [ ] Citations added
- [ ] Answer-first structure
```

## Platform-Specific Optimization

Refer to [references/platform-algorithms.md](./references/platform-algorithms.md) for detailed ranking factors.

### ChatGPT
- Prioritize **branded domain authority** (cited 11% more than third-party)
- Refresh content within **30 days** (3.2x more citations)
- Cultivate **backlinks** (>350K referring domains = 8.4 avg citations)
- Align content style with ChatGPT's response format

### Perplexity
- Allow **PerplexityBot** in robots.txt
- Employ **FAQ Schema** (higher citation rate)
- Host **PDF documents** (prioritized for citation)
- Emphasize **semantic relevance** over keywords

### Google AI Overview (SGE)
- Optimize for **E-E-A-T** (Experience, Expertise, Authority, Trust)
- Leverage **structured data** (Schema markup)
- Build **topical authority** (content clusters + internal linking)
- Include **authoritative citations** (+132% visibility)

### Microsoft Copilot / Bing
- Ensure **Bing indexing** (required for citation)
- Optimize for **Microsoft ecosystem** (LinkedIn, GitHub mentions help)
- Page speed **< 2 seconds**
- Clear **entity definitions**

### Claude AI
- Ensure **Brave Search indexing** (Claude uses Brave, not Google)
- High **factual density** (data-rich content preferred)
- Clear **structural clarity** (easy to extract)

## Skill Dependencies

This skill pairs well with:
- **twitter skill** — Search SEO experts for the latest tips
- **reddit skill** — Search r/SEO, r/bigseo for discussions
- **WebSearch** — Keyword research and competitor analysis

## References

- [references/platform-algorithms.md](./references/platform-algorithms.md) - Detailed ranking factors for each platform
- [references/geo-research.md](./references/geo-research.md) - Princeton GEO research (9 methods)
- [references/schema-templates.md](./references/schema-templates.md) - JSON-LD templates
- [references/seo-checklist.md](./references/seo-checklist.md) - Complete SEO audit checklist
- [references/tools-and-apis.md](./references/tools-and-apis.md) - Tools and API reference
- [examples/opc-skills-case-study.md](./examples/opc-skills-case-study.md) - Real-world optimization example
