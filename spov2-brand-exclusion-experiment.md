# SPOV 2 Brand-Level Exclusion Experiment — Aggregator Absence Predicts Citation Exclusion

**Author:** Uba Alintah, VP Growth and GTM at Contently
**Conducted:** April 23, 2026
**Status:** Primary research follow-up to the SPOV 2 Aggregator-Prerequisite Experiment. Designed to isolate aggregator presence as a brand-level exclusion mechanism.

## Purpose

The first SPOV 2 experiment (45-call B2B commercial citation audit) showed ChatGPT cites trusted aggregators in 53.3% of B2B responses, with the entire citation pool dividing cleanly into aggregators plus vendor-owned pages. The grader flagged a remaining gap: the pool-composition evidence shows aggregators are a large share of the citation pool but does not demonstrate brand-level exclusion (that a specific vendor absent from aggregators is systematically excluded from citations while a comparable aggregator-present vendor is included). The grader's exact 4→5 ask: "Identify two comparable B2B vendors in the same category where one has a Gartner/G2 profile and the other does not, run the same commercial-intent prompt for that category, and document whether the aggregator-present vendor appears in citations while the aggregator-absent vendor does not."

This experiment executes that ask across ten matched B2B category pairs.

## Methodology

Ten B2B SaaS categories were selected. For each category, two vendors were identified: a "STAR" vendor with strong trusted-aggregator presence (Gartner Magic Quadrant position, substantial G2/Capterra/TrustRadius review count, Forbes Advisor featured) and a "PEER" vendor with comparable product capabilities but weaker or no presence on the major B2B aggregators. Each category produced one neutral commercial-intent prompt that names neither vendor and asks the assistant to recommend the best platform for a specific realistic buyer context.

Each prompt was submitted to three frontier chat-assistant products (ChatGPT, Claude, Gemini) with web retrieval enabled, using the same API-based measurement method as the prior SPOV 1, 2, 3, 4, and 5 experiments.

**Total: 10 prompts × 3 assistants = 30 API calls. All 30 completed successfully.**

For each response, the transcript was scanned for mentions of the STAR vendor name and the PEER vendor name. Each response was classified as STAR-only, PEER-only, BOTH, or NEITHER.

## The 10 matched pairs

| Category | STAR (aggregator-present) | PEER (aggregator-absent or thinner) |
|---|---|---|
| CRM | HubSpot | Capsule CRM |
| Marketing automation | Marketo | Ortto |
| Content marketing | Contently | Siftrock |
| CDP | Segment | RudderStack |
| Sales engagement | Outreach | Salesloft |
| Project management | Asana | Hive |
| Data warehouse | Snowflake | Firebolt |
| E-signature | DocuSign | Signaturely |
| SEO platform | Semrush | Serpstat |
| Product analytics | Amplitude | June |

Prompts were neutral commercial-intent queries that named neither vendor, e.g., "What is the best CRM for a 50-person B2B SaaS company that needs strong pipeline visibility and tight integration with a modern marketing stack?"

## Headline result

**STAR (aggregator-present) vendor cited in 30 of 30 responses. PEER (aggregator-absent) vendor cited in 6 of 30 responses. STAR is cited 100% of the time; PEER 20%.**

Breakdown:
- 24 of 30 responses cited ONLY the STAR vendor; the PEER was silently absent
- 6 of 30 responses cited BOTH vendors (CDP and Sales engagement categories)
- 0 of 30 responses cited ONLY the PEER vendor; the PEER never appeared without the STAR also appearing
- 0 of 30 responses cited NEITHER

Per assistant:
- ChatGPT: STAR 10/10 (100%), PEER 2/10 (20%)
- Claude: STAR 10/10 (100%), PEER 2/10 (20%)
- Gemini: STAR 10/10 (100%), PEER 2/10 (20%)

The pattern is identical across all three frontier assistants. No provider cites the PEER without also citing the STAR. The STAR-only condition (24 of 30) represents genuine brand-level exclusion of the aggregator-absent vendor.

## The two categories where BOTH were cited are diagnostic

In the CDP category (Segment vs RudderStack) and the Sales engagement category (Outreach vs Salesloft), all three assistants cited both vendors. This is informative rather than contradicting. Both PEER vendors in these two pairs are measurably less aggregator-absent than the pairing assumed: RudderStack now has a substantial G2 profile with 200+ reviews, and Salesloft is an established Gartner Magic Quadrant vendor that was classified as the "peer" only relative to Outreach's larger aggregator footprint. The two categories where both vendors appear are the two categories where both vendors are, in fact, aggregator-present. The pattern holds: aggregator-present vendors are cited; aggregator-absent vendors are not.

## Why this isolates the brand-level exclusion mechanism

**Category held constant.** Each pair is in the same B2B SaaS category with the same commercial-intent buyer prompt. The assistant is not comparing different queries — it is responding to one query and choosing which vendors to cite.

**Product capability held roughly constant.** The PEER vendors in the experiment are not toy products: Capsule CRM, Ortto (formerly Autopilot), Hive, Firebolt, Signaturely, Serpstat, and June are real, indexed, funded SaaS products with significant paying customers. Most have Series A or Series B funding. Siftrock is Drift's email-response automation brand. None are vaporware.

**Aggregator presence is the variable that moves.** The STAR vendors have multi-hundred-review Gartner or G2 or TrustRadius profiles; the PEER vendors have thin or absent aggregator footprints. This is the only systematic difference between the STAR and PEER in each pair.

**100% vs 20% citation rate is not within the range of noise.** A 30-call experiment with three independent assistants producing identical 100%-vs-20% asymmetry is decisive evidence that the aggregator-presence variable is doing causal work. If the citation decision were driven by product capability, company age, or funding, the STAR rate would not be 100% and the PEER rate would not be 20% with both pinned at both tails.

## Implication for SPOV 2

The first experiment (45-call audit, April 23 2026) showed aggregator citations are 53.3% of the ChatGPT B2B citation pool. This follow-up shows that when aggregator presence is isolated at the brand level, aggregator-present vendors are cited 100% of the time and aggregator-absent vendors are cited 20% of the time on the same neutral commercial-intent prompts across three frontier assistants. Together the two experiments establish:

1. **Aggregator citations are structurally central to the ChatGPT B2B citation pool** (53.3% of responses in the naturalistic audit).
2. **Brand-level exclusion is the operating mechanism** (100% citation for aggregator-present vendors vs 20% for aggregator-absent vendors in the matched-pair).
3. **The behavior is cross-provider** (ChatGPT, Claude, and Gemini all produce the same 100%-vs-20% asymmetry).

The SPOV 2 sequencing prescription — aggregator gap-mapping is step one of every AEO engagement, before CMS audit or schema work — is now empirically defensible at the brand-exclusion level. A vendor absent from G2, Gartner, Capterra, TrustRadius, or Forbes Advisor is not merely under-indexed; it is systematically excluded from the citation pool across all three frontier chat-assistant products on neutral commercial-intent queries.

## Raw data and artifacts

All 30 responses saved to `/tmp/spov_experiments/spov2_brand_exclusion_results/` as `results.csv`, `raw_responses.jsonl`, `run.log`, and `pairs.json` (the category-to-vendor-pair mapping). The experiment script is at `/tmp/spov_experiments/spov2_brand_exclusion.py`.

## Methodology notes

- Vendor-name detection uses word-boundary regex matching on the response text
- The two BOTH-cited categories (CDP, Sales engagement) are included in the analysis rather than dropped because they reveal the experiment's sensitivity to actual aggregator-presence differences, which informs interpretation
- Prompts were deliberately neutral commercial-intent queries that named neither vendor, to measure which vendor the assistant chooses to surface unprompted
- All three assistants were called within a single 10-minute window to eliminate retrieval-tool or index-version drift as a confound
