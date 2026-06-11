# Activity Report (Streamlined Mode)

- [05:53:48] **Created**: Job created for prompt: Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp locally, especially for coding-agent use, web automation, research tasks, and long-running assistant workflows.

Goal:
Find the most reliable LM Studio / llama.cpp / GGUF settings for qwen3.6-35b-a3b-mtp, with emphasis on reducing loops, repetition, tool-call weirdness, overthinking, and slow output while preserving coding accuracy.

Model/context:
- Model: qwen3.6-35b-a3b-mtp
- Likely GGUF / local inference
- Use case: coding agent, research agent, general assistant, Hermes-style local agent
- Hardware target: GMKtec-style mini PC / local rig, 128GB RAM, likely CPU/iGPU/NPU experimentation
- Prior issue: model can repeat actions, reread files, loop, or ignore that it already saw something
- Need settings for both “thinking” and “non-thinking/instruct” use

Research requirements:
1. Find official Qwen, Hugging Face, ModelScope, Unsloth, llama.cpp, and LM Studio guidance for:
   - temperature
   - top_p
   - top_k
   - min_p
   - repeat_penalty / repetition_penalty
   - presence_penalty
   - frequency_penalty
   - context length
   - MTP-specific settings
   - stop sequences
   - thinking mode vs non-thinking mode
   - prompt format / chat template
   - system prompt recommendations

2. Compare recommended settings for these modes:
   - Precise coding
   - General research
   - Agentic tool use
   - Long context debugging
   - Creative brainstorming
   - Low-loop / low-repetition mode
   - Fast mode

3. Specifically investigate whether repeat_penalty should stay at 1.0 or be raised slightly.
   - Look for evidence that Qwen3.6 prefers repetition_penalty=1.0.
   - Look for cases where users raise it to 1.05–1.15 to prevent loops.
   - Determine whether repeat_penalty hurts code quality, structured output, or reasoning.

4. Investigate MTP-specific issues:
   - Does MTP cause repetition or “/////” style loops in llama.cpp?
   - Are there llama.cpp bugs or flags related to MTP?
   - Are there incompatible flags with MTP?
   - Does speculative/MTP decoding need different sampling?

5. Find ideal settings for LM Studio specifically:
   - Preset recommendations
   - GPU offload / CPU settings if available
   - Context size recommendations
   - Flash attention / KV cache / quantization notes
   - Whether to use Q4, Q5, Q6, Q8, or Unsloth Dynamic quant
   - Best balance of speed and quality

6. Build a testing matrix:
   - At least 8 setting profiles
   - Each profile should include all sampler values
   - Label each profile by purpose
   - Include expected behavior and risk

7. Create test prompts to compare settings:
   - Coding bugfix test
   - Long-file reasoning test
   - Tool-use planning test
   - “Do not reread file” compliance test
   - Repetition/loop stress test
   - JSON output test
   - Step-by-step debugging test
   - Concise answer test

8. Final output format:
   - Executive summary: best starting settings
   - Table of recommended profiles
   - Evidence summary with source links
   - Known problems and fixes
   - Final recommended default for my use case
   - LM Studio exact values
   - llama.cpp command-line equivalent if possible
   - “If it loops, change these first” section
   - “If it gets dumb, revert these” section

Important:
Do not rely on random comments alone. Prioritize official model cards, Unsloth docs, Qwen docs, llama.cpp issues, and highly repeated community experience. Cite every claim with links. Separate confirmed facts from user anecdotes.
- [05:53:48] **Streamlined**: Using streamlined Codex path — minimal search plus single synthesis call
- [05:54:42] **SearchStarted**: Streamlined seed search: 7 query/queries across 4 browser engines plus Google
- [05:54:44] **SearchError**: bing failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:54:44] **SearchError**: yahoo failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:54:44] **SearchError**: brave failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Cannot access a disposed object.
Object name: 'System.Threading.SemaphoreSlim'.
- [05:54:44] **SearchError**: scholar failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:54:50] **SearchEngine**: google returned 10 URL(s) for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca..." in 7.0s.
- [05:54:52] **SearchHeartbeat**: Streamlined seed search still running after 10s; 10 candidate URL(s) found.
- [05:54:58] **SearchEngine**: google returned 10 URL(s) for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca..." in 8.9s.
- [05:54:59] **SearchFinished**: Streamlined seed search finished with 11 candidate URL(s) in 16.0s.
- [05:54:59] **Acquired**: Captured: Qwen (https://qwen.ai/blog?id=qwen3.6-35b-a3b)
- [05:54:59] **Acquired**: Captured: unsloth/Qwen3.6-35B-A3B-MTP-GGUF · Hugging Face (https://huggingface.co/unsloth/Qwen3.6-35B-A3B-MTP-GGUF)
- [05:54:59] **Acquired**: Captured: How to run Qwen3.6-35B-A3B locally — the coding MoE that beats models 10x its active size - DEV Community (https://dev.to/purpledoubled/how-to-run-qwen36-35b-a3b-locally-the-coding-moe-that-beats-models-10x-its-active-size-3pbh)
- [05:54:59] **Acquired**: Captured: Reddit - Please wait for verification (https://www.reddit.com/r/LocalLLaMA/comments/1srziyq/optimizing_qwen_36_35b_a3b_sampling_parameters/)
- [05:55:12] **EvidenceRepair**: Evidence quotas unmet; running targeted repair search (Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp locally, espec official primary source docum; Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp locally, espec technical documentation imple; Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp locally, espec risks legal policy security p)
- [05:55:12] **SearchStarted**: Evidence repair search: 5 query/queries across 4 browser engines plus Google
- [05:55:12] **SearchError**: bing failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:55:12] **SearchError**: yahoo failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:55:12] **SearchError**: scholar failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:55:13] **SearchError**: brave failed for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca...": Process exited
- [05:55:16] **SearchEngine**: google returned 10 URL(s) for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca..." in 4.4s.
- [05:55:22] **SearchHeartbeat**: Evidence repair search still running after 10s; 10 candidate URL(s) found.
- [05:55:25] **SearchEngine**: google returned 10 URL(s) for "Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp loca..." in 8.8s.
- [05:55:25] **SearchFinished**: Evidence repair search finished with 13 candidate URL(s) in 13.3s.
- [05:55:27] **Acquired**: Captured: GitHub - hogeheer499-commits/strix-halo-guide: AMD Strix Halo local LLM guide: direct 100.0 t/s 30B Qwen MoE on Ryzen AI MAX+ 395 / Radeon 8060S. Setup, benchmarks, raw evidence. · GitHub (https://github.com/hogeheer499-commits/strix-halo-guide)
- [05:55:27] **Acquired**: Captured: Reddit - Please wait for verification (https://www.reddit.com/r/LocalLLaMA/comments/1tgrk75/configuration_qwen3635ba3b_12gb_vram/)
- [05:55:27] **EvidenceRepairComplete**: Repair added 2 source(s); Evidence quotas unmet: need 8 curated sources, found 3; need risk/legal/policy evidence
- [05:55:27] **CodexEvidenceRescue**: Local/search evidence is still weak; selected Codex will perform bounded live evidence rescue. Evidence quotas unmet: need 8 curated sources, found 3; need risk/legal/policy evidence
- [05:55:27] **Drafting**: Evidence-first synthesis: Codex writes from local evidence dossier
- [05:55:27] **CodexSynthesisStarted**: Codex gpt-5.5 synthesis started; timeout 420s; web search enabled; evidence rescue enabled; dossier sources 3; seeded citations 3.
- [05:55:57] **CodexSynthesisHeartbeat**: Codex synthesis still running after 30s; web-search events observed: 0.
- [05:56:27] **CodexSynthesisHeartbeat**: Codex synthesis still running after 60s; web-search events observed: 0.
- [05:56:57] **CodexSynthesisHeartbeat**: Codex synthesis still running after 90s; web-search events observed: 0.
- [05:57:27] **CodexSynthesisHeartbeat**: Codex synthesis still running after 120s; web-search events observed: 0.
- [05:57:57] **CodexSynthesisHeartbeat**: Codex synthesis still running after 150s; web-search events observed: 0.
- [05:58:27] **CodexSynthesisHeartbeat**: Codex synthesis still running after 180s; web-search events observed: 0.
- [05:58:45] **CodexSynthesisReturned**: Codex synthesis returned in 198.4s; web-search events observed: 25.
- [05:58:47] **GroundingScore**: Grounding: 98% (67/68 claims cited, 66 strong)
- [05:58:47] **ReportValidation**: professional polish: 2 process-leakage paragraph(s) removed
- [05:58:47] **CodexBudgetWarning**: Codex budget exceeded for Fast: web-search events 11/0.
- [05:58:47] **ReportQualityGate**: Health: NeedsExpansion; words: 3009; sources: 20; citations: 20; visuals: 4; citation density: 12.9 words/citation. Standard report is too short: 3,009 words; target minimum is 4,000.

## Cost Ledger

- Provider: Codex
- Model: gpt-5.5
- Report mode: Fast/Fast
- LLM calls: 2
- Local LM Studio calls: 1
- Local model attempts: 2
- Local model fallbacks: 1
- Local model timeouts: 0
- LM Studio busy observations: 1 (max queue depth 1)
- LM Studio active state: generating
- LM Studio attempted models: qwen3.6-35b-a3b-mtp, qwen3.6-27b-mtp
- LM Studio fallback reason: primary_failed_after_busy_wait
- Codex exec calls: 1
- Codex web-search events: 11
- Codex budget warning: Codex budget exceeded for Fast: web-search events 11/0.
- Tool calls: 1
- Web searches: 12
- Vision calls: 0
- Browser searches: 8
- Google searches: 4
- Search timeouts: 0
- Search elapsed: 29211 ms
- Source fetches: 7
- Visuals generated: 0
- Evidence repair loops: 2
- Local tokens: 1059 in / 37 out
- Approx tokens: 98000 in / 13266 out
- LLM elapsed: 252677 ms
- Report words: 3,009 (target 4,000-6,000)
- Report sources: 20
- Citation density: 12.9 words/citation
- Report visuals: 4
- Polish passes: 1
- Expansion passes: 1
- Finalization passes: 1
- Finalization fixed issues: 0
- Finalization unresolved issues: 0
- Encoding fixes: 0
- Process leakage removals: 0
- Uncited estimates repaired/found: 0
- Report rank: 91/100 (A-)
- Quality issues: TooShort: Standard report is too short: 3,009 words; target minimum is 4,000.
- Ranking criteria: Depth 6/10; Evidence 10/10; Citations 10/10; Structure 10/10; Visuals 10/10; Polish 10/10; Decision Utility 10/10; Title 10/10; Quality Gate 6/10
