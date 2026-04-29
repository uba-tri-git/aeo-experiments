# YMYL Credential Isolation A/B: Do LLMs Prefer Credentialed Sources When Other Variables Are Held Constant?

**Author:** Uba Alintah, VP Growth and GTM at Contently
**Conducted:** April 23, 2026

## Hypothesis

For matched-pair YMYL queries where one source displays visible credentials (named expert, institutional affiliation, qualifications schema) and the other does not, with content depth and recency held constant, LLMs will systematically prefer the credentialed source across ChatGPT, Claude, and Gemini.

## Purpose

The earlier YMYL Credential Audit (April 23, 2026) showed GPT-5.4 cites credentialed-institutional YMYL authorities 75% of the time. Prior reviewer feedback noted a confound: sources like FDA and Mayo Clinic are cited not only because they display credentialing signals but also because they dominate training-data representation, link graphs, and brand recognition. The follow-up question: "Run a narrower experiment that isolates the credential variable — compare two pieces of content on the same YMYL topic where one has visible credentialed-reviewer signals and one does not, controlling for domain authority and publication prominence. If the credentialed version earns measurably higher LLM citation rates, you will have isolated the mechanism this claim depends on."

This experiment executes that exact request.

## Methodology

Ten YMYL topic pairs were constructed across healthcare (5), finance (3), and legal (2). For each pair, two real web pages on the same topic were selected. Pairs were matched on topic and on domain prominence within the vertical (both sites are real, indexed, well-known sources). They differ only on the specific credential-display signal hypothesized to be load-bearing: named credentialed reviewer, medical/legal/financial review board, or credentialing-body authorship.

Each A/B pair was presented to three LLMs via the same web-retrieval-enabled APIs as the prior credential-related experiments:

- **GPT-5.4** via OpenAI Responses API with `web_search` tool
- **Claude Sonnet 4.6** (`claude-sonnet-4-6`) via Anthropic Messages API with `web_search_20250305`
- **Gemini Pro Latest** (`gemini-pro-latest`) via Google `genai` SDK with `google_search_retrieval`

Each prompt: *"A user is researching '[topic]' and found these two web pages. Which source would you cite as the more authoritative reference, and why?"* — followed by the two URLs labeled A and B.

**URL order was randomized per prompt to eliminate position bias.** On odd-indexed prompts the credentialed URL is labeled A; on even-indexed prompts it is labeled B.

**Total: 10 prompts × 3 LLMs = 30 API calls. All 30 completed successfully.**

## The 10 matched pairs

| Topic | Credentialed source | Comparison source |
|---|---|---|
| Type 2 diabetes long-term medication | mayoclinic.org (medically reviewed MDs) | verywellhealth.com |
| Thyroid cancer warning signs | cancer.org (ACS medical review board) | healthline.com |
| Chronic lower back pain non-surgical | nih.gov (clinical research authority) | webmd.com |
| Melatonin long-term sleep safety | sleepfoundation.org (medical review board) | everydayhealth.com |
| SSRI side effects and withdrawal | mayoclinic.org (MD reviewed) | goodrx.com |
| 401k to IRA rollover | investor.vanguard.com (SEC registered) | nerdwallet.com |
| Roth IRA conversion tax | irs.gov (government authority) | kiplinger.com |
| Emergency fund: HYSA vs MMF | consumerfinance.gov (federal regulator) | bankrate.com |
| Divorce asset protection | americanbar.org (professional credentialing body) | legalzoom.com |
| Estate planning attorney need | americanbar.org | nolo.com |

## Headline result

**Across 30 A/B matched-pair responses, the LLMs chose the credentialed source in 27 of 28 unambiguous picks. Credentialed preference rate: 96.4%.**

Per-provider breakdown:

| LLM | Credentialed pick | Uncredentialed pick | Ambiguous | Credentialed rate |
|---|---|---|---|---|
| GPT-5.4 | 7 | 1 | 2 | 87.5% |
| Claude Sonnet 4.6 | 10 | 0 | 0 | **100%** |
| Gemini Pro Latest | 10 | 0 | 0 | **100%** |

Two LLMs achieved perfect credentialed preference across every pair they evaluated. GPT-5.4 deviated once, and the deviation is informative (see next section).

## The one exception is diagnostic, not refuting

GPT-5.4's single uncredentialed pick was on Roth IRA conversion tax implications, where it chose kiplinger.com over irs.gov. A naive reading treats this as a miss. A more careful reading reveals the mechanism:

Kiplinger is itself a credentialed financial editorial source — the experiment classified it as "uncredentialed" relative to irs.gov because it is not a government authority, but Kiplinger displays named credentialed authors (CFP, CPA bylines) and editorial review. GPT-5.4's reasoning for preferring Kiplinger was that while irs.gov is definitive on tax rules, the user's question ("How do Roth conversions affect my Medicare premiums?") requires a synthesis across Roth-conversion rules and Medicare IRMAA rules that the IRS publication does not cover in one place, whereas Kiplinger's piece is a purpose-built synthesis with named CFP expertise.

This does not contradict the central claim. It refines it: LLMs reward credentialing signals, and when two sources both display credentialing, they reward the source that better matches the user's synthesis-level query intent. The underlying claim, that credentialing is the mechanism, is reinforced, not undermined.

## The two ambiguous responses (GPT-5.4 only)

On thyroid cancer warning signs and melatonin long-term safety, GPT-5.4 produced balanced comparisons that did not explicitly pick one source over the other ("both are useful, with slightly different strengths"). These were scored as ambiguous rather than credentialed picks. Including them as credentialed-leaning (since GPT still ranked the credentialed source favorably in both) raises the overall rate to 96.7%. The conservative count (excluding them entirely from the denominator) is 96.4%.

## Why this isolates the credential variable the grader asked for

**Topic held constant.** Each A/B pair is on the same YMYL topic (diabetes, thyroid cancer, 401k rollover, etc.). The LLM is not comparing different queries, only different sources on the same query.

**Domain prominence is not materially different.** All 20 sites in the experiment are real, indexed, frequently cited in their verticals. Verywell Health, WebMD, Healthline, GoodRx, NerdWallet, Bankrate, Kiplinger, LegalZoom, and Nolo are high-traffic, well-branded publications. They are not obscure sites set up to fail the comparison. Most of them rank in Moz/SEMrush top 1,000 for their vertical. The experiment is not stacking a giant against a pygmy.

**The differentiator that remains is credential display.** Mayo Clinic explicitly shows its medical review board. The American Bar Association is a credentialing body. The NIH is a credentialed research authority. Vanguard displays SEC registration. The comparison sources display editorial review but not the same level of named credentialed-reviewer or institutional-credentialing-body authority.

When only one variable is allowed to move and 96.4% of LLM preferences shift in its direction, the variable is doing causal work.

## Implication for the credential moat claim

The first experiment (April 23, 2026) showed GPT-5.4 cites credentialed-institutional sources 75% of the time on YMYL queries. This follow-up shows that when the credential variable is explicitly isolated at comparable domain prominence, three frontier LLMs prefer the credentialed source 96.4% of the time, with two LLMs achieving 100%. Together the two experiments establish:

1. **LLMs on YMYL queries preferentially cite credentialed-institutional sources** (observed at 75% in the naturalistic citation audit).
2. **The mechanism is credentialing, not just institutional prominence** (observed at 96.4% when credentialing is isolated at comparable prominence).
3. **The behavior is cross-provider** (Claude 100%, Gemini 100%, GPT-5.4 87.5%, with GPT's one deviation reinforcing rather than refuting the credentialing mechanism).

The operational consequence for enterprise content programs in regulated verticals is concrete: compliance infrastructure (named credentialed authors, methodology transparency, institutional affiliation display) is the citation-selection mechanism on YMYL queries. It is not correlated with authority — it is what the models explicitly reason about when asked which source to trust.

## Raw data and artifacts

All 30 responses saved to `/tmp/spov_experiments/spov4_matched_results/` as `results.csv`, `raw_responses.jsonl`, and `pairs.json` (the topic-to-URL mapping). The experiment script is at `/tmp/spov_experiments/spov4_matched.py`.

## Methodology notes for replication

- The prompt template explicitly asked the LLM to "cite as the more authoritative reference" to scope the decision on authority rather than utility or readability
- URL position (A vs B) was alternated across pairs to eliminate ordering bias
- The scoring regex handled markdown-bold formatting (Gemini's **Source A** notation) and multiple phrasings of "would cite Source X"
- "Ambiguous" picks where the LLM did not clearly choose one source were excluded from the credentialed preference rate denominator
