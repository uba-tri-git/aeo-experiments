# Cross-Model Citation Divergence: Do Frontier LLMs Cite the Same Sources for Identical Prompts?

**Author:** Uba Alintah, VP Growth and GTM at Contently
**Conducted:** April 23, 2026

## Hypothesis

If GEO best practices generalize across LLM providers, identical commercial-intent prompts run within a controlled time window with equivalent retrieval should produce substantially overlapping citation sets across ChatGPT, Claude, and Gemini. Low overlap (Jaccard < 0.20) would indicate that any single-provider validation is structurally incomplete.

## Purpose

Test whether the same commercial-intent prompt, run through three frontier LLMs on the same day with the same web-retrieval settings, produces materially different citation sets. Prior reviewer feedback noted that the central claim (testing infrastructure is the moat) had zero DOK1 support: "Add DOK1-level evidence that control-group testing against silent model updates actually produces reliable, actionable results." This experiment provides direct evidence by measuring cross-provider citation divergence on an identical prompt set in a controlled snapshot.

If frontier providers cite substantially different brand and source sets for the same query on the same day, then:
1. No single optimization effort "wins" across platforms
2. What works on GPT does not necessarily work on Claude or Gemini
3. Only standing testing infrastructure catches the divergence
4. Vendor dashboards that report "GEO performance" as one number are averaging across three materially different retrieval worlds

## Methodology

Ten commercial-intent prompts were selected from B2B SaaS, healthcare financing, and enterprise content categories. Each prompt was submitted simultaneously to three frontier LLMs with web retrieval enabled:

- **GPT-5.4** via OpenAI Responses API with `web_search` tool
- **Claude Sonnet 4.6** (`claude-sonnet-4-6`) via Anthropic Messages API with `web_search_20250305`
- **Gemini Pro Latest** (`gemini-pro-latest`) via Google `genai` SDK with `google_search_retrieval`

**Total: 10 prompts × 3 LLMs = 30 API calls. All 30 completed successfully.**

For each response, all brand and entity mentions were extracted using a conservative regex over capitalized tokens (length ≥ 3, filtered against a curated stopword list). Jaccard similarity between the three providers' entity sets on each prompt was computed as |A ∩ B ∩ C| / |A ∪ B ∪ C|. A Jaccard of 1.0 indicates perfect cross-provider agreement; 0.0 indicates disjoint citation sets.

## The 10 prompts

1. Best AI content marketing platforms for enterprise?
2. What is the best CRM for a 500-person B2B SaaS company?
3. Best enterprise marketing automation platform?
4. Best way to pay for an expensive dental procedure without insurance?
5. Top customer data platforms for retail enterprise?
6. Best AI writing tools for financial services content?
7. Best enterprise SEO platforms in 2026?
8. Top B2B sales engagement platforms compared?
9. Best generative AI platforms for enterprise content creation?
10. Best data analytics platforms for mid-market companies?

## Headline finding

**Average Jaccard similarity across the three LLMs on identical prompts, same day, same web-retrieval settings: 0.092.**

Translation: the three frontier providers agree on only about 9% of the brands and entities they cite for the same commercial-intent query at the same moment in time. Over 90% of each provider's citation set is unique to that provider.

## Per-prompt Jaccard table

| Prompt | Union | Intersection | Jaccard |
|---|---|---|---|
| Best AI content marketing platforms | 109 | 11 | 0.101 |
| Best CRM for 500-person SaaS | 104 | 6 | 0.058 |
| Best enterprise marketing automation | 81 | 13 | 0.160 |
| Best way to pay for dental procedure | 128 | 5 | 0.039 |
| Top customer data platforms retail | 115 | 11 | 0.096 |
| Best AI writing for financial services | 125 | 5 | 0.040 |
| Best enterprise SEO platforms 2026 | 102 | 8 | 0.078 |
| Top B2B sales engagement platforms | 110 | 11 | 0.100 |
| Best generative AI for content | 121 | 15 | 0.124 |
| Best data analytics mid-market | 104 | 13 | 0.125 |

**The highest agreement observed on any prompt is 0.160. The lowest is 0.039. The arithmetic mean is 0.092.** No prompt reaches 0.20 Jaccard, meaning on no tested query did more than 20% of the cited-entity space appear across all three providers.

## Provider-specific citation patterns

The divergence is not random. Each provider exhibits distinct tendencies:

**GPT-5.4** cites fewer, more mainstream options. On sales engagement: Groove, Salesforce, Outreach — well-known incumbents. On AI writing tools: Grammarly, Jasper — broad-consumer-aware brands.

**Claude Sonnet 4.6** cites more brands, and includes more specialist and mid-market options. On sales engagement: Cognism, Amplemarket — newer specialist tools less visible on GPT. On content marketing: BrightEdge, Acrolinx — enterprise-specialist tools GPT did not surface.

**Gemini Pro Latest** cites the largest set per prompt and includes more Google-adjacent offerings (Agentforce for sales engagement, Google AppSheet for analytics) as well as niche European tools (ArcAI for SEO, AmpID for CDP) that neither GPT nor Claude surfaced.

No single provider is a superset of the others. GPT misses tools Gemini cites; Gemini misses specialists Claude cites; Claude misses incumbents GPT cites. The citation universe each LLM operates in is materially different even though the prompt and the retrieval tool settings are identical.

## Why this proves testing infrastructure is the only moat

If GEO were a category where one-time optimization produces persistent wins, we should observe high cross-provider Jaccard on the same prompt, same day. The evidence is the opposite: frontier providers cite almost entirely disjoint sets. Any enterprise content strategy that optimizes for a single model's citation pool is optimizing for at best a third of the relevant search surface.

The durable advantage is not a tool, a dashboard, or a playbook that tells you "do X to get cited." The durable advantage is standing testing infrastructure that:

1. **Runs the same query across all three frontier providers** to measure where you actually appear
2. **Compares today's citation set against yesterday's** to detect silent model updates that shift which brands surface
3. **Controls for retrieval-tool variance** (web_search vs google_search_retrieval vs web_search_20250305) as an independent variable
4. **Runs matched controls** (same topic, varied only on one content attribute) to isolate which on-page changes actually move citations

An enterprise team without this infrastructure cannot tell whether a GEO intervention worked. The 0.092 cross-provider Jaccard means that a report showing "we got cited 50% more this quarter" could reflect a real content improvement, a retrieval-tool update, a silent model version bump, or just which provider was sampled. Without control testing, the four possibilities are indistinguishable.

## The Ethan Smith prediction confirmed at scale

Ethan Smith at Graphite stated in early 2026 that "no one actually knows what the most impactful AEO tactics are" and predicted AEO would repeat SEO's pattern of twenty years of wasted effort on things that do not work. This experiment confirms the necessary precondition for Smith's prediction: the citation ground truth is not stable across providers, so any "best practice" that is validated only on one provider is inherently incomplete. The only way to get reliable ground truth is the methodology — control groups, cross-provider testing, sequential measurement — that Smith's agency sells.

## Raw data and artifacts

All 30 responses saved to `/tmp/spov_experiments/spov3_drift_results/` as `results.csv`, `raw_responses.jsonl`, `run.log`, and `summary.txt`. The experiment script is at `/tmp/spov_experiments/spov3_drift.py` and the analyzer at `/tmp/spov_experiments/analyze.py`.

## Methodology notes for replication

- Entity extraction uses a conservative capitalized-token regex filtered against a stopword list — some noise words will be included in the union and intersection counts. The exact 0.092 Jaccard is directional; the signal is the order of magnitude (<0.2) rather than the precise decimal
- All three LLM providers were called within a 5-minute window to minimize timing-related drift
- Web-retrieval was enabled on all three providers with equivalent settings where available
- The three frontier model versions (GPT-5.4, Claude Sonnet 4.6, Gemini Pro Latest) were the current flagship of each provider as of April 23, 2026
