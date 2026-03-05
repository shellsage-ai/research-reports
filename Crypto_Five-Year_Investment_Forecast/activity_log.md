# Activity Report (Streamlined Mode)

- [05:23:40] **Created**: Job created for prompt: You are a crypto financial research AI. Produce a 5-year (2026–2031) investment research report that includes **price prediction charts** (bar charts + line charts) for the top candidates you identify.

Objective
Identify the best crypto investment(s) to hold for 5 years (2026–2031) and support the conclusion with a transparent, data-driven forecast.

Hard Rules
- Use **current real market data** (price, market cap, supply, on-chain where available). Do not guess without sourcing.
- Clearly separate: **Facts (with sources)** vs **Assumptions** vs **Forecasts**.
- No hype. No “guarantees.” Always include uncertainty bands and scenario ranges.
- Provide at least **3 scenarios**: Bear / Base / Bull.
- Output must include **charts** and the **exact data tables** used to generate them (so the charts are reproducible).

Universe & Selection
1) Start with a broad screen of major assets (e.g., top by market cap + key sectors: L1s, L2s, DeFi, infra, oracles, RWAs).
2) Narrow to a final set:
   - 1 “core” (can include BTC/ETH if justified)
   - 2–4 “high conviction” alts
   - Optional: 1 “speculative” pick (clearly labeled)
3) Explain why each made the cut using a scoring framework.

Evaluation Framework (must be explicit + scored)
Score each candidate (0–10) on:
- Technology & security
- Developer activity & ecosystem growth
- Adoption & real usage
- Tokenomics & value capture (fees, burn, staking)
- Competitive moat
- Liquidity & market structure risk
- Regulatory risk (security/commodity classification risk, geo exposure)
- Catalyst outlook (roadmap, integrations, macro tailwinds)
Show a ranked table of scores and weights used.

Forecasting Method (required)
Use a hybrid approach:
A) Market-cycle + macro model
- Explicit assumptions about cycle timing, liquidity conditions, risk-on/off regimes.
B) Fundamental value-capture model (when applicable)
- Reasoned link from network usage → fees/revenue → token value capture.
C) Comparable/relative valuation
- Compare to sector peers (e.g., L1 vs L1, L2 vs L2) for sanity checks.
D) Monte Carlo or range-based forecasting
- Use volatility/drawdown history to produce plausible ranges.
If you cannot run Monte Carlo, use a transparent range method and justify it.

Time Granularity
Forecast at minimum:
- Annual endpoints: 2026, 2027, 2028, 2029, 2030, 2031
Better: quarterly points (Q1 each year or full quarterly series if feasible).

CHART REQUIREMENTS (must include all)
For EACH selected asset (and portfolio):
1) Line Chart (regular)
- X-axis: time (years or quarters 2026–2031)
- Y-axis: projected price
- Plot 3 scenario lines (Bear/Base/Bull)
- Include a shaded uncertainty band around Base (e.g., 25th–75th percentile or stated range)

2) Line Chart (log scale)
- Same as above but with log Y-axis to show growth differences more clearly

3) Bar Chart: Yearly targets
- Bars for each year 2026–2031 for Base scenario
- Overlay markers or error bars for Bear/Bull ranges

4) Bar Chart: Expected return comparison
- Compare expected CAGR and expected max drawdown (two separate bar charts)
- Include the portfolio vs each asset

Portfolio Output (required)
- Recommend a 5-year allocation (percent weights)
- Show portfolio forecast charts (same chart types above)
- Rebalance policy (none / annual / threshold-based) and why

Risk Section (required)
- Key failure modes per asset (technical, regulatory, competitive, governance, liquidity)
- What would falsify the thesis (specific metrics/thresholds)
- Stress test: 70–90% drawdown scenario and recovery assumptions

Deliverables (in this order)
1) Executive Summary (top pick + portfolio, 8–12 bullets)
2) Data Sources (links) + date pulled
3) Scoring Table + rationale
4) Deep dives for each selected asset (facts first, then analysis)
5) Forecast model explanation (assumptions + math described plainly)
6) Forecast outputs:
   - Exact forecast tables (Bear/Base/Bull + bands)
   - ALL required charts (regular line, log line, yearly bars, return/risk bars)
7) Portfolio recommendation + charts
8) Risks, stress tests, and “what would change my mind”
9) References (credible sources)

Formatting Notes
- Include captions under every chart explaining what it shows and the assumptions.
- If any dataset is missing, state it and substitute with the best proxy (and say why).
- Do not omit charts: charts are mandatory.
- [05:23:40] **Streamlined**: Using streamlined Codex path — single synthesis with native web search
- [05:24:26] **Acquired**: Captured: [PDF] 40745_2022_Article_433.pdf (https://pmc.ncbi.nlm.nih.gov/articles/PMC9436724/pdf/40745_2022_Article_433.pdf)
- [05:24:26] **Drafting**: Streamlined synthesis: Codex researches + writes in one call
- [05:35:40] **GroundingScore**: Grounding: 86% (48/56 claims cited)
