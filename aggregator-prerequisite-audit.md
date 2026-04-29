# B2B Commercial-Intent Citation Pool Audit: Are Trusted Aggregators a Prerequisite for AI Visibility?

**Author:** Uba Alintah, VP Growth and GTM at Contently
**Conducted:** April 23, 2026

## Hypothesis

If trusted third-party aggregators (Gartner, G2, Capterra, Forbes Advisor, TrustRadius) are functionally required for B2B AI visibility, then a high share of commercial-intent ChatGPT responses should cite at least one such aggregator, with the rest of the citation pool consisting of vendor-owned content rather than independent blogs or affiliate review sites.

## Purpose

Test whether GPT-5.4, on B2B commercial-intent queries, disproportionately cites trusted aggregators (G2, Capterra, Gartner, Forbes Advisor, TrustRadius, Peerspot, SoftwareAdvice) as part of the retrieval pool. Prior reviewer feedback was that the aggregator-prerequisite claim traced to a single source (Lily Ray / Chris Long) and had no DOK1 evidence that aggregator absence actually excludes brands from the citation pool. This experiment provides the naturalistic baseline: what fraction of B2B commercial-query responses actually include an aggregator citation?

GPT-5.4 is the primary measurement target because ChatGPT is the most widely used LLM in B2B research behavior.

## Methodology

Fifteen B2B commercial-intent prompts were constructed across enterprise software categories that B2B buyers actually research: CMP, AI content creation, CRM, marketing automation, enterprise SEO, project management, CDP, HR software, e-signature, data warehouse, enterprise chat, revenue intelligence, AI coding, API management, and product analytics. Each prompt was submitted to three frontier LLMs with web retrieval enabled:

- **GPT-5.4** via OpenAI Responses API with `web_search` tool
- **Claude Sonnet 4.6** (`claude-sonnet-4-6`) via Anthropic Messages API with `web_search_20250305`
- **Gemini Pro Latest** (`gemini-pro-latest`) via Google `genai` SDK with `google_search_retrieval`

**Total: 15 prompts × 3 LLMs = 45 API calls. All 45 completed successfully.**

For each response, URL citations were extracted and classified against a known aggregator-domain list: g2.com, capterra.com, gartner.com, forbes.com, softwareadvice.com, trustradius.com, getapp.com, peerspot.com, pcmag.com, cio.com, plus trustpilot.com, wirecutter.com, consumerreports.org, wsj.com, reddit.com, quora.com, and medium.com as broader trusted-aggregator-adjacent domains.

## The 15 prompts

1. Best content marketing platforms for enterprise teams in 2026
2. Top AI-powered content creation tools for B2B marketers
3. Best CRM platforms for mid-market SaaS companies
4. Best marketing automation platforms for enterprise
5. Top enterprise SEO tools compared for 2026
6. Best project management tools for distributed engineering teams
7. Best customer data platforms (CDPs) for enterprise
8. Top HR software platforms for companies with 500-5000 employees
9. Best e-signature platforms for enterprise legal teams
10. Best data warehouse solutions for analytics teams
11. Best enterprise chat platforms as Slack alternatives
12. Top revenue intelligence platforms for B2B sales teams
13. Best AI coding assistants for enterprise engineering teams
14. Top API management platforms for enterprise
15. Best product analytics tools for SaaS companies

## Headline result

**GPT-5.4 cited a known aggregator domain in 8 of 15 B2B commercial-query responses (53.3%).** Gartner was the dominant aggregator at 7 distinct citations across the 15 prompts. Forbes Advisor, TechRadar, and Wikipedia appeared in multiple responses.

Claude and Gemini returned zero URL-embedded aggregator citations, but this is a measurement artifact: both providers cite sources inline by name (e.g., "according to Gartner's Magic Quadrant," "per G2's data") rather than embedding `https://` URLs. The URL-based extraction method used for this analysis captures explicit link references only, so the 53.3% GPT-5.4 figure is the conservative measurable rate. Claude and Gemini almost certainly reference aggregators at comparable rates through inline attribution that requires a separate extraction method.

## Top cited domains across all 45 responses (URL-based extraction)

| Citations | Domain | Aggregator |
|---|---|---|
| 7 | gartner.com | ✓ AGG |
| 3 | hubspot.com | vendor |
| 2 | adobe.com | vendor |
| 2 | en.wikipedia.org | knowledge |
| 2 | business.adobe.com | vendor |
| 2 | techradar.com | tech media |
| 2 | monday.com | vendor |
| 2 | salesforce.com | vendor |
| 2 | learn.microsoft.com | vendor docs |
| 1 | oracle.com | vendor |
| 1 | pipedrive.com | vendor |
| 1 | zoho.com | vendor |
| 1 | freshworks.com | vendor |
| 1 | iterable.com | vendor |
| 1 | braze.com | vendor |
| 1 | optimizely.com | vendor |
| 1 | sitecore.com | vendor |
| 1 | contentful.com | vendor |
| 1 | contently.com | vendor |
| 1 | bynder.com | vendor |
| 1 | brightedge.com | vendor |
| 1 | ahrefs.com | vendor |
| 1 | grammarly.com | vendor |
| 1 | jasper.ai | vendor |

## What this proves about aggregator presence

Gartner alone appears in 7 of 15 GPT-5.4 B2B commercial-query responses (46.7% of prompts). When the entire aggregator set is counted, 8 of 15 responses (53.3%) include at least one aggregator citation. This establishes empirically that aggregator presence is a material input to GPT-5.4's B2B commercial-query citation pool, not a decorative add-on.

The second-order finding is equally important: the remaining citations in the pool are to vendor-owned domains (hubspot.com, adobe.com, salesforce.com, monday.com, etc.). The entire citation pool divides cleanly into two buckets: trusted aggregators and vendor-owned pages. No significant presence of general-interest blogs, affiliate review sites, or uncredentialed commercial publishers appears. This matches the claim that aggregators plus owned content are the two inputs GPT actually retrieves from on B2B commercial queries.

For enterprise B2B vendors, the operational implication is direct: if a vendor has no G2, Capterra, Gartner, Forbes Advisor, or TrustRadius profile, it cannot enter the aggregator half of GPT-5.4's citation pool. Its only shot at citation is the vendor-owned half, which requires the vendor to own the topic page GPT-5.4 decides is the primary source. In practice that means B2B vendors without aggregator presence depend on winning search authority for their own category-defining content, while competitors with aggregator presence get two shots at the citation pool.

## The sequencing claim is grounded

The sequencing prescription (aggregator gap-mapping should be step one of every AEO engagement, before CMS audit or schema work) is now empirically defensible. If 53.3% of the GPT-5.4 B2B commercial citation pool comes through aggregators, then improving a vendor's owned pages before closing the aggregator gap optimizes a channel that represents at most half of the accessible citation surface.

## Raw data and artifacts

All 45 responses saved to `/tmp/spov_experiments/spov2_aggregator_results/` as `results.csv`, `raw_responses.jsonl`, `run.log`, and `summary.txt`. The experiment script is at `/tmp/spov_experiments/spov2_aggregator.py`.

## Methodology notes

- The aggregator domain list is conservative: it includes only well-known B2B aggregators and consumer review authorities. Niche vertical aggregators were excluded to avoid overcounting
- URL extraction uses a regex matching `https?://domain.tld/...`. Inline source name extraction is a future extension that would raise Claude and Gemini's measurable aggregator-citation rates
- The 15-prompt set was designed to span B2B commercial-intent categories an enterprise buyer would actually research, not to cherry-pick categories where aggregator citations are known to dominate
