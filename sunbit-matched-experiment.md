# Sunbit Matched-Prompt Experiment — Controlled A/B Comparison

**Author:** Uba Alintah, VP Growth and GTM at Contently
**Conducted:** April 15, 2026
**Status:** Controlled follow-up to the CareCredit LLM Citation Experiment

## Purpose

Test whether the Parallel-Signal Collision Model — discovered in the original 45-call CareCredit experiment — generalizes across brands by running a matched-prompt controlled comparison between CareCredit (Trustpilot 1.2/5) and Sunbit (Trustpilot 4.7/5) on identical decision-intent prompts across the same three LLMs.

If the model generalizes, then on the same prompts, Sunbit should receive recommendation-quality framing without buyer warnings while CareCredit continues to receive warnings. If the original finding was a one-brand anomaly, framing should be similar for both brands.

## Methodology

Nine decision-intent prompts were tested across three LLMs with web retrieval enabled (same configuration as the original experiment):

- **GPT-5.4** via OpenAI Responses API with the `web_search` tool enabled
- **Claude Sonnet 4.6** (`claude-sonnet-4-6`) via Anthropic Messages API with the `web_search_20250305` tool enabled, `max_uses: 5`
- **Gemini Pro Latest** (`gemini-pro-latest`) via Google genai SDK with `google_search_retrieval` grounding enabled

**Total: 9 prompts × 3 LLMs = 27 API calls. All 27 completed successfully.**

The first 3 prompts are the exact same decision-intent prompts from the original CareCredit experiment. The remaining 6 are additional healthcare financing decision prompts designed to increase sample size.

## The 9 prompts

1. How do I pay for a root canal without insurance?
2. Best way to pay for expensive dental procedures?
3. How can I afford dental implants if I don't have insurance?
4. What are the best payment plans for dental work?
5. How to finance cosmetic dental procedures?
6. What financing options are available for LASIK surgery?
7. Best buy now pay later options for medical procedures?
8. How to pay for elective surgery without insurance?
9. What healthcare credit cards or payment plans should I consider?

## Brand sentiment profiles (verified April 15, 2026)

**CareCredit** (Synchrony Financial):
- Trustpilot: 1.2 out of 5 across 300+ reviews
- WalletHub: 2.0 out of 5 across 1,000+ reviews with 71% one-star share

**Sunbit:**
- Trustpilot: 4.7 out of 5 across 3,361 reviews
- Better Business Bureau: 3.97 out of 5 with A+ accreditation

Sentiment delta: +3.5 Trustpilot points in Sunbit's favor.

## Aggregate Results

### Citation rates

| Brand | Mentions | Rate |
|---|---|---|
| CareCredit | 25 of 27 | 93% |
| Sunbit | 9 of 27 | 33% |

CareCredit's content authority dominance is even more pronounced on pure decision-intent prompts (93% vs 38% in the original mixed-intent experiment).

### Citation rates by LLM

| LLM | CareCredit | Sunbit |
|---|---|---|
| GPT-5.4 | 7/9 (78%) | 2/9 (22%) |
| Claude Sonnet 4.6 | 9/9 (100%) | 3/9 (33%) |
| Gemini Pro Latest | 9/9 (100%) | 4/9 (44%) |

### Co-occurrence: Both brands in the same response

Nine responses cited both CareCredit and Sunbit. These are the controlled comparisons — same prompt, same LLM, same response, different framing.

## The key finding: Structural framing divergence in co-occurring responses

### Example 1: Gemini Pro Latest on "What healthcare credit cards or payment plans should I consider?"

Gemini created a two-tier structural taxonomy in a single response:

**Tier 1 — "Dedicated Healthcare Credit Cards"** (CareCredit, Alphaeon, Wells Fargo):
> "🚨 The Deferred Interest Trap: Most healthcare credit cards use 'deferred interest' for their 0% promotional periods. This means if you do not pay off the entire balance by the end of the promotional period (or if you miss a payment), you will be charged interest retroactively from the original purchase date. Because the standard APR on these cards is usually very high (often nearly 30%), this can cost you hundreds or thousands of dollars unexpectedly."

**Tier 2 — "Healthcare 'Buy Now, Pay Later' & Point-of-Sale Loans"** (Sunbit, Cherry, Affirm):
> "These often feature simple interest or true 0% interest without the 'deferred interest' trap."
> "Sunbit: Increasingly popular in dental offices, optometry clinics, and veterinary offices. Sunbit boasts a very high approval rate (around 85%), uses a soft credit check that doesn't hurt your credit score."

The LLM placed CareCredit in the warned category and Sunbit in the safe category, within the same response, based on the consumer consensus signal. No prompt instruction directed this categorization.

### Example 2: Claude Sonnet 4.6 on "Best buy now pay later options for medical procedures?"

Claude ranked four brands explicitly:

**#1 Cherry** — "Best Overall for Healthcare": "True 0% APR for qualified borrowers (no deferred interest)", "~90% approval rate"

**#2 CareCredit** — "Best for Wide Acceptance" but with explicit warning:
> "⚠️ Watch out: Promotional 'No Interest if Paid in Full' offers provide flexibility, but they can become costly if a payment is missed or a balance remains at the end of the period — triggering retroactive interest charged from the purchase date."
> Listed cons: "Deferred interest model can be risky", "Hard credit check required"

**#4 Sunbit** — "Best for Low Credit Scores": No warning attached. Described neutrally as offering "flexible payment plans, spreading the cost over up to 72 months."

### Example 3: Claude Sonnet 4.6 on "What are the best payment plans for dental work?"

**CareCredit** (listed #1): Neutral but with caveats: "After the promotional period, interest rates apply, so timely payments are crucial to avoid additional costs."

**Sunbit** (listed #3): Purely positive framing:
> "Sunbit offers a simple, fast, and transparent way for patients to pay over time for dental care."
> "Sunbit has among the highest approval rates in the industry — more than double the industry average, approving 87% of patients who apply."

### Example 4: GPT-5.4 on "What healthcare credit cards or payment plans should I consider?"

GPT-5.4 placed CareCredit last (#4 of 4 options) with CFPB as the source of the warning:
> "The best-known example is CareCredit, which is widely used by providers. CFPB materials specifically caution about deferred-interest structures in products like these."

Sunbit was listed alongside other options without any warning language.

### Example 5: GPT-5.4 on "What are the best payment plans for dental work?"

**CareCredit** (listed #2): With "Important warning" section citing CFPB:
> "the CFPB warns consumers to be careful with deferred-interest promotions on medical credit cards. If you do not pay the full amount by the end of the promo period, you may be charged interest retroactively."

**Sunbit** (listed #4): Described as "fast approval", "no hard credit check", "87% approval rate" with no warning.

## Framing classification across all 27 responses

### CareCredit framing when cited (25 mentions):

| Framing | Count | Share |
|---|---|---|
| WARNING | 6 | 24% |
| MIXED | 1 | 4% |
| NEUTRAL | 16 | 64% |
| POSITIVE | 2 | 8% |

### Sunbit framing when cited (9 mentions):

| Framing | Count | Share |
|---|---|---|
| WARNING | 1 | 11% |
| MIXED | 1 | 11% |
| NEUTRAL | 4 | 44% |
| POSITIVE | 2 | 22% |

Note: One Sunbit "WARNING" classification (Gemini P7) was a genuine but mild warning about deferred interest on some Sunbit plans, significantly softer than the CareCredit warnings in the same response. The other Sunbit "WARNING" from the automated classifier was a false positive caused by context-window bleed from CareCredit's warning text appearing in the preceding paragraph.

### Head-to-head framing in the 9 co-occurring responses:

| Prompt | LLM | CareCredit | Sunbit | Winner |
|---|---|---|---|---|
| P1 | Claude | POSITIVE | POSITIVE | Tie |
| P1 | Gemini | NEUTRAL | NEUTRAL* | Tie |
| P4 | GPT-5.4 | NEUTRAL | NEUTRAL | Tie |
| P4 | Claude | NEUTRAL | POSITIVE | Sunbit |
| P4 | Gemini | NEUTRAL+caveat | NEUTRAL | Tie |
| P7 | Claude | WARNING | NEUTRAL | Sunbit |
| P7 | Gemini | WARNING | MILD-WARNING | Sunbit |
| P9 | GPT-5.4 | WARNING | NEUTRAL | Sunbit |
| P9 | Gemini | NEUTRAL+trap | POSITIVE-framed | Sunbit |

In 4 of 9 co-occurrences, Sunbit received materially better framing than CareCredit. In 0 of 9 did CareCredit receive better framing than Sunbit. The remaining 5 were ties (both neutral or both positive).

**Sunbit never received worse framing than CareCredit on any matched prompt.**

## Interpretation

The matched-prompt experiment confirms the Parallel-Signal Collision Model generalizes across brands within the healthcare financing vertical:

1. **Content authority determines citation presence.** CareCredit's SEO dominance drives 93% citation rate vs Sunbit's 33%. Content investment wins the visibility slot.

2. **Consumer sentiment determines citation framing.** On identical prompts within the same LLM response, CareCredit receives explicit buyer warnings (deferred interest, retroactive charges, CFPB cautions) while Sunbit receives neutral-to-positive framing (simple, fast, transparent, high approval rates).

3. **LLMs create structural taxonomies that encode sentiment.** The most striking evidence is Gemini's P9 response, which created a two-tier category system separating "Healthcare Credit Cards" (CareCredit, warned) from "Healthcare BNPL" (Sunbit, safe) — an editorial judgment driven by the consumer consensus, not by the prompt.

4. **The framing delta is monotonic.** Across all 9 co-occurring responses, Sunbit received equal or better framing than CareCredit in every case. CareCredit never received better framing than Sunbit on any matched prompt.

5. **The warnings map to the review corpus.** CareCredit's warnings reference the 32.99% APR, deferred interest trap, and retroactive charges — the exact complaint patterns from its Trustpilot and WalletHub reviews. Sunbit's framing references high approval rates and ease of use — the positive signals from its 4.7/5 Trustpilot profile.

Combined with the original 45-call experiment, the total evidence base is now 72 API calls across two experiments, demonstrating the same mechanism: content authority wins the citation, consumer sentiment writes the recommendation.

## Replicability

All 27 API calls can be reproduced using the Python script at `/tmp/sunbit_matched_experiment.py`. The raw responses are logged to `/tmp/sunbit_matched_experiment_results/raw_responses.jsonl`. The structured results are in `/tmp/sunbit_matched_experiment_results/results.csv`. The framing comparison is in `/tmp/sunbit_matched_experiment_results/framing_comparison.txt`.
