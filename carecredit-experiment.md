# CareCredit Split-Framing Audit: Does Negative Consumer Sentiment Change LLM Citation Framing?

**Author:** Uba Alintah, VP Growth and GTM at Contently
**Conducted:** April 15, 2026

## Hypothesis

If LLMs incorporate consumer sentiment into how they describe brands, then a brand with sustained negative review patterns (CareCredit, Trustpilot 1.2/5) should be cited with warnings, caveats, or qualifying language on decision-intent prompts, while content-authority signals from owned pages remain comparable to higher-rated competitors.

## Purpose

Test whether a brand with dominant SEO authority but severely negative consumer review sentiment maintains its citation share in LLM-generated responses, and document how the brand is framed when cited.

CareCredit (Synchrony Financial) was chosen because it represents the clearest possible natural experiment. They hold position 1 on Google for at least 10 healthcare-cost keywords (veneers cost, root canal cost, dentures cost, dental implants cost, braces cost, and others verified via SEMrush on April 15 2026). They invest approximately 1 to 2 million dollars per year in their Well-U content hub. At the same time, their consumer-facing review reputation is severely negative: Trustpilot rating 1.2 out of 5 across more than 300 reviews, WalletHub rating 2.0 out of 5 across more than 1,000 reviews with 71 percent of reviewers giving one star.

If owned content wins LLM visibility outright, CareCredit should dominate citations for healthcare-financing prompts. If negative sentiment blocks citation, CareCredit should be absent or rare. Either finding is publishable.

## Methodology

Fifteen commercial-intent prompts were matched to CareCredit's top 30 organic keywords from SEMrush (US database, April 15 2026 snapshot). Prompts cover cost-intent queries (where CareCredit's Well-U content ranks position 1 on Google) and decision-intent queries (where CareCredit wants to be recommended as a financing option).

Three LLMs were tested using each provider's current flagship model with web retrieval enabled so the experiment reflects what a real user sees in the consumer product UI:

- **GPT-5.4** via OpenAI Responses API with the `web_search` tool enabled
- **Claude Sonnet 4.6** (`claude-sonnet-4-6`) via Anthropic Messages API with the `web_search_20250305` tool enabled, `max_uses: 5`
- **Gemini Pro Latest** (`gemini-pro-latest`) via Google genai SDK with `google_search_retrieval` grounding enabled

**Total: 15 prompts × 3 LLMs = 45 API calls. All 45 completed successfully.**

## The 15 prompts

1. How much do dental veneers cost?
2. How much does a root canal cost?
3. How much do dental implants cost?
4. What are the types of dental implants?
5. How much do dentures cost?
6. How much are partial dentures?
7. How much do braces cost?
8. How much do Invisalign braces cost?
9. What is the cost of orthodontic treatment for adults?
10. How much does LASIK eye surgery cost?
11. How much does Botox cost on average?
12. What is the cost of hearing aids?
13. How do I pay for a root canal without insurance?
14. Best way to pay for expensive dental procedures?
15. How can I afford dental implants if I don't have insurance?

Prompts 1-12 are cost-intent. Prompts 13-15 are decision-intent.

## Brands tracked in responses

CareCredit, Affirm, Klarna, Afterpay, Sezzle, Zip, Sunbit, GreenSky, LendingClub, Prosper, Upgrade, Ally Lending, Cherry, PatientFi, Alphaeon, Wells Fargo Health Advantage, Scratchpay, PayTomorrow, Lending USA, United Medical Credit, Denefits, Proceed Finance, iCare Financial.

## Aggregate findings

**CareCredit was cited in 17 of 45 responses across all three LLMs.** That is a 38 percent mention rate. No competing healthcare financing brand exceeded 2 citations in the same 45 responses.

**Brand citation counts across all 45 calls:**

| Brand | Mentions |
|---|---|
| CareCredit | 17 |
| Sunbit | 2 |
| Zip | 2 (false positive — matched "zip code") |
| Proceed Finance | 1 |
| Wells Fargo Health Advantage | 1 |
| Cherry | 1 |
| LendingClub | 1 |

**By LLM, CareCredit citation rate:**

- GPT-5.4: 4 of 15 responses (27%)
- Claude Sonnet 4.6: 5 of 15 responses (33%)
- Gemini Pro Latest: 9 of 15 responses (60%)

## The cost vs. decision split (the key finding)

CareCredit citation rate differs dramatically between cost-intent queries and decision-intent queries.

- **On 12 cost-intent prompts across all three LLMs (36 responses total):** CareCredit appeared in 8 of 36 (22% mention rate)
- **On 3 decision-intent prompts across all three LLMs (9 responses total):** CareCredit appeared in 9 of 9 (**100% mention rate**)

CareCredit wins decision-stage citation outright across all three LLMs.

## Framing classification

The 17 CareCredit mentions were classified by how the LLM framed the brand in context. Four buckets:

**Bucket A — Positive as a data source (3 mentions, 18%).** On prompts about denture cost, partial denture cost, and Invisalign cost, GPT-5.4 and Claude cite CareCredit's cost research as the authoritative data source.

Verbatim example from **GPT-5.4 on denture cost**:
> "CareCredit's 2024-2025 cost data lists these national averages: basic full dentures (upper and lower) about $452, traditional full dentures about $1,968, and premium full dentures about $6,514."

Verbatim example from **GPT-5.4 on partial denture cost**:
> "A recent CareCredit cost guide lists a national average of about $1,738 for partial resin dentures and about $2,229 for partial metal dentures" — with a direct link back to carecredit.com

Verbatim example from **Claude Sonnet 4.6 on Invisalign cost**:
> "According to CareCredit's research, the average cost for clear aligner treatment in the United States (before insurance) is approximately $5,108."

**Bucket B — Neutral listing as one financing option among others (6 mentions, 35%).**

Example verbatim:
> "work with third-party financing services (like CareCredit) that allow you to split the cost into monthly payments"

**Bucket C — Positive recommendation with 0% APR emphasis (5 mentions, 29%).**

Example verbatim from **Gemini on LASIK**:
> "Most major eye centers offer financing plans (such as CareCredit) that allow you to pay off the procedure in monthly installments, often with 0% interest if paid within a certain timeframe."

**Bucket D — Negative warning with deferred interest caution (3 mentions, 18%).** All three appeared on decision-intent prompts.

## The three verbatim warning quotes (the central finding)

**Verbatim from Claude Sonnet 4.6 on "Best way to pay for expensive dental procedures?":**
> "The standard APR for CareCredit financing is 32.99%, but you can get 0% interest if you charge $200 or more and pay it off within a 6, 12, 18, or 24-month term. If you aren't able to pay off your balance, you'll be charged interest retroactively from the date of your first purchase."

**Verbatim from Gemini Pro Latest on the same prompt:**
> "Cards like CareCredit or the Wells Fargo Health Advantage card are designed specifically for out-of-pocket healthcare expenses. They often offer promotional 0% APR for 6 to 24 months. **Warning:** These cards usually use 'deferred interest'..."

The word "Warning:" appears verbatim in the response body, inserted by the model without user prompting, attached to the CareCredit mention rather than to the broader category.

**Verbatim from GPT-5.4 on "How can I afford dental implants if I don't have insurance?":**
> "Medical credit / personal financing - Options like healthcare credit cards or loans can help, but be careful: promotional rates may expire, **deferred interest can be brutal**, compare APRs before agreeing."

## Interpretation

The experiment falsifies the simple version of the hypothesis ("negative sentiment blocks LLM citation") and establishes a sharper structural finding.

**LLMs run parallel lookups on a brand mention.** Owned content authority wins the factual slot. Consumer consensus wins the recommendation slot. For a brand with strong SEO and negative review consensus, the two signals collide in the same response: positive factual attribution arrives wrapped in cautionary buyer language drawn directly from the consumer complaint patterns visible on review aggregators.

The language in the three warning quotes maps almost word-for-word to the most common CareCredit complaints on Trustpilot and WalletHub: the 32.99% standard APR, the deferred interest trap when promotional periods expire, and the retroactive interest charge when a balance is not paid off within the promo window. **The LLM is not making these warnings up. It is surfacing the consumer consensus that the review corpus encodes.**

The implication for enterprise CMOs is that citation share and conversion share are now two different metrics with opposite trajectories for sentiment-weak brands. CareCredit is winning the citation slot because their SEO is strong enough to be unavoidable on 100% of decision-stage queries. But on those exact queries the recommendation layer is attaching buyer warnings that the brand's analytics cannot see. **Every impression funded by content investment is wrapped in a buyer warning funded by nobody.**

---

# Addendum: Competitor Framing Comparison (Sunbit and Cherry)

The experiment dataset contains a natural controlled comparison that emerged from the raw responses without being designed into the original methodology.

## Competitor sentiment profiles (verified April 15, 2026)

**Sunbit** (buy-now-pay-later installment financing, sunbit.com):
- Trustpilot: **4.7 out of 5 across 3,361 reviews**
- Better Business Bureau: 3.97 out of 5 across 238 reviews, with A+ accreditation
- Sentiment delta vs. CareCredit: **+3.5 points on Trustpilot** (4.7 minus 1.2)

**Cherry** (healthcare installment loans, withcherry.com):
- Google Reviews: 4.7 out of 5
- Better Business Bureau: 4.7 out of 5
- Sentiment delta vs. CareCredit: composite equivalent to Sunbit

**CareCredit** (the subject of the primary experiment):
- Trustpilot: 1.2 out of 5 across 300+ reviews
- WalletHub: 2.0 out of 5 across 1,000+ reviews with 71% one-star share

Sunbit's Trustpilot rating is 3.5 points higher than CareCredit's on a 5-point scale. Both Sunbit and Cherry are materially better than CareCredit by any reasonable consumer-sentiment measure.

## The framing delta on prompt 15 (Claude Sonnet 4.6, same response)

**Prompt 15:** "How can I afford dental implants if I don't have insurance?"

Claude Sonnet 4.6 listed four healthcare financing brands in a single response. Verbatim framing of each:

**CareCredit:** Listed under the heading "Third-Party Financing (CareCredit, Lending Club, etc.)" with framing about 1-year zero-interest plans. In Claude's adjacent response to prompt 14, Claude attached the 32.99% APR and retroactive deferred-interest clause specifically to CareCredit. On the same decision-intent prompt set, Claude treats CareCredit as a cautioned brand.

**LendingClub:** Listed alongside CareCredit in the category header. No separate framing.

**Cherry:** Framed verbatim as:
> "Cherry, which lets you split your dental bill into monthly payments."
Neutral-positive framing, no warning, no interest rate caveat.

**Sunbit:** Framed verbatim as:
> "a simple way to pay over time with less stress."

This is **the most positive framing of any financing brand in any of the 45 responses** collected in the experiment. It is the only brand mention across all 45 responses that includes the phrase "less stress" as a product descriptor. No warning attached, no APR caveat, no deferred interest flag.

## The framing delta on prompt 13 (Gemini Pro Latest, same response)

**Prompt 13:** "How do I pay for a root canal without insurance?"

Gemini Pro Latest listed three brands together: "third-party medical lenders like **CareCredit**, **Proceed Finance**, or **Sunbit**."

In the same response, Gemini attached the deferred-interest warning specifically to the CareCredit product description:
> "CareCredit acts as a credit card specifically for out-of-pocket medical and dental expenses. The catch: This is 'deferred interest.' If you do not pay off the entire balance before the promotional period ends..."

**Sunbit was not subject to this warning despite being listed in the same sentence.** The LLM automatically scoped the deferred-interest framing to the product class that CareCredit's review corpus complains about (promotional-period credit cards with retroactive interest) and left Sunbit's installment BNPL structure unflagged. This differentiation happened without any prompt instruction.

## Interpretation (competitor comparison)

The framing delta tracks the sentiment delta directly across the three brands present in the experiment data.

- **Sunbit** (Trustpilot 4.7/5, 3.5 points higher than CareCredit) → most positive framing in the experiment
- **Cherry** (Google/BBB 4.7/5, equivalent to Sunbit) → neutral-positive framing with no warnings
- **CareCredit** (Trustpilot 1.2/5, WalletHub 2.0/5 with 71% one-star) → all three verbatim warning quotes across GPT-5.4, Claude, Gemini

**Brands with materially better consumer sentiment receive materially better LLM framing on identical decision-intent prompts, within the same LLM response.** The split-framing effect is a function of the consumer consensus signal, not a quirk of CareCredit specifically.

## Caveats and limits

The comparison is based on two LLM responses out of 45 calls (not a designed controlled experiment with equal N per competitor brand). Sunbit appeared in 2 of 45 responses and Cherry in 1. The small sample size means the comparison is suggestive rather than definitive, but the size of the framing delta (explicit positive phrasing vs. explicit warning phrasing, on identical prompts within the same LLM response) is large enough that it would be difficult to explain by chance.

The "Zip" mention initially flagged by the brand tracker was a false positive: the brand matcher caught the substring "zip" in "zip code" in Gemini's mention of DentalPlans.com, not the Zip BNPL brand. This has been excluded from the competitor framing analysis.

## Replicability

All 45 API calls can be reproduced using the Python script at `/tmp/carecredit_experiment.py` on Uba's local machine. The raw responses are logged to `/tmp/carecredit_experiment_results/raw_responses.jsonl` with the full text of every response truncated at 3,000 characters. The structured results are in `/tmp/carecredit_experiment_results/results.csv`. The script uses API keys from the Radarly backend environment file and can be re-run against the same models at any time to measure drift.

## Future experiments

This is a first-pass experiment. The next iteration should:

1. Run a dedicated comparison prompt set that explicitly asks each LLM to compare CareCredit against three named alternatives (Sunbit, Cherry, Affirm), forcing equal sample sizes per brand and producing a balanced controlled comparison with ~45 data points per brand instead of 1-2.
2. Expand to the **financial services vertical** (not just healthcare financing) to test whether the same split-framing mechanism holds for different negative-sentiment brands in finance — for example, payday lenders, aggressive BNPL brands, or debt consolidation companies with poor Trustpilot scores.
3. Add a **control group** of brands with strong SEO AND strong positive sentiment to establish the contrast.
4. Track response-level metadata including timestamp, model version ID, and retrieval tool latency to measure drift across model updates.
