# Executive Summary

**Research question:** You are a senior AI systems researcher, quant trading systems architect, and practical startup engineer.

Research how to build the fastest realistic path to an agentic crypto trading bot that can become profitable as soon as possible while avoiding reckless live-money behavior.

The user’s available setup:
- ChatGPT Pro / Codex access
- GMKtec EVO-X2 / Ryzen AI Max+ 395-class rig
- 128GB RAM
- 2TB SSD
- Windows primary environment
- Possible local AI through LM Studio / OpenRouter / free or low-cost AI services
- Interest in using CPU, iGPU, and NPU efficiently
- Tools to consider: Codex, OpenCode, OpenClaw, OpenRouter, LM Studio, Hummingbot, Freqtrade, CCXT, vector databases, local models, research agents, browser automation, and any newer better alternatives

Main goal:
Find the fastest legitimate path to an automated crypto trading system that can earn money, starting from research/backtesting/paper trading and moving toward small live trades only after measurable edge is proven.

Research requirements:
1. Identify the best architecture for an agentic crypto trading bot.
2. Compare existing bot frameworks: Hummingbot, Freqtrade, Jesse, OctoBot, CCXT-based custom bot, OpenCode/Codex-built custom system, and any better current options.
3. Determine whether using AI agents actually helps trading, and where it helps most:
   - research
   - strategy discovery
   - feature engineering
   - backtest analysis
   - news/sentiment analysis
   - anomaly detection
   - execution/risk control
   - code generation
4. Determine where AI should NOT be trusted, especially direct live trade decisions.
5. Research the fastest-to-profit strategy classes:
   - market making
   - grid trading
   - statistical arbitrage
   - funding-rate arbitrage
   - momentum/scalping
   - mean reversion
   - event/news-driven trading
   - sentiment-driven trading
   - cross-exchange arbitrage
   - triangular arbitrage
6. Rank strategies by:
   - speed to prototype
   - likelihood of profitability
   - capital required
   - risk
   - exchange/API complexity
   - compute requirements
   - automation difficulty
   - beginner feasibility
   - suitability for small accounts
7. Research whether NPU usage matters for this project.
   - Can the Ryzen AI NPU be used meaningfully?
   - What local models/tools can use it today?
   - Is it worth optimizing for NPU, or should CPU/iGPU/cloud APIs be prioritized?
8. Research the best local model setup for this rig.
   - Best coding model
   - Best research/summarization model
   - Best lightweight decision-support model
   - Best embedding model
   - Best reranker
   - Whether LM Studio, llama.cpp, Ollama, OpenVINO, ONNX Runtime, or other stacks are best
9. Research how Codex / ChatGPT Pro should be used in the workflow.
   - Generating code
   - reviewing code
   - writing tests
   - analyzing logs
   - improving strategies
   - creating backtest reports
   - fixing bugs
10. Research OpenCode and OpenClaw specifically.
   - What are they currently capable of?
   - Are they useful for this project?
   - Are they reliable enough?
   - What should they be used for, if anything?
11. Design a concrete system architecture:
   - data ingestion
   - exchange connectors
   - historical data storage
   - backtesting engine
   - paper trading engine
   - live trading engine
   - risk engine
   - strategy registry
   - agent research layer
   - monitoring dashboard
   - logging
   - alerting
   - kill switch
   - audit trail
   - config management
12. Design an agent workflow:
   - Research Agent
   - Strategy Builder Agent
   - Backtest Agent
   - Risk Review Agent
   - Code Review Agent
   - Paper Trading Agent
   - Live Execution Agent
   - Watchdog Agent
   - Profit/Loss Analyst Agent
13. Determine what should be fully autonomous and what should require human approval.
14. Create an MVP plan focused on earning as fast as realistically possible.
15. Create a 7-day build plan, 14-day build plan, and 30-day build plan.
16. Include exact recommended tech stack.
17. Include exact repo/folder structure.
18. Include database choice.
19. Include exchange/API recommendations for paper trading and eventual small live testing.
20. Include backtesting requirements:
   - fees
   - slippage
   - spread
   - latency
   - survivorship bias
   - walk-forward testing
   - out-of-sample testing
   - paper trading validation
21. Include risk controls:
   - max daily loss
   - max position size
   - max open positions
   - exchange outage handling
   - API failure handling
   - stop trading after drawdown
   - trade cooldowns
   - no martingale unless explicitly proven safe
   - no leverage at MVP stage
22. Include legal/tax/compliance concerns.
23. Include realistic warnings about scams, fake profitability, overfitting, backtest lies, and AI hallucinations.
24. Include what NOT to build.
25. Include what to build first.

Output format:
- Executive summary
- Best recommended path
- Tool/framework comparison table
- Strategy ranking table
- Hardware utilization plan
- AI-agent architecture
- MVP architecture
- 7-day plan
- 14-day plan
- 30-day plan
- Exact tech stack
- Exact repo structure
- Risk-control checklist
- Testing/backtesting checklist
- Paper-trading checklist
- Go/no-go criteria for live trading
- Final recommendation

Important constraints:
- Do not recommend vague “AI trading bot” nonsense.
- Do not assume profit is guaranteed.
- Prioritize fastest realistic path to measurable edge.
- Prefer boring profitable systems over flashy agent demos.
- The bot must start with backtesting and paper trading.
- Real money trading should only begin with tiny size after statistical evidence.
- Avoid paid tools unless they are clearly worth it.
- Prefer open-source/free tools where practical.
- Be brutally honest about what is likely to work and what is a waste of time.
- Include citations and source links for all major claims.
- Prefer current 2026 information.
- Verify whether each mentioned tool is still maintained and useful.
- End with a clear build recommendation: “Build this first.”

**Verdict: Adopt Freqtrade-first, Watch Hummingbot, Avoid autonomous LLM trade execution.** The fastest realistic path is a boring, evidence-gated spot-only system built on Freqtrade for data download, backtesting, dry-run paper trading, hyperparameter experiments, analysis exports, and eventual tiny live trades, with AI agents restricted to research, code generation, test writing, log analysis, and risk review rather than final order decisions [4][5][16].  

The strongest engineering reason to start with Freqtrade is that it already covers the MVP loop that matters: strategy code, historical OHLCV data, backtesting with fees, dry-run wallet simulation, hyperopt, lookahead analysis, recursive analysis, plotting, and live mode from the same Python strategy surface [4][5]. Hummingbot is more suitable if the first strategy is market making or cross-exchange market making, because its docs e...

See the full report for comparative detail, citations, and limitations.