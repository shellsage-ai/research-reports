# Executive Summary

**Research question:** Research the best practical tuning/settings for running qwen3.6-35b-a3b-mtp locally, especially for coding-agent use, web automation, research tasks, and long-running assistant workflows.

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

**Verdict: Adopt, with guarded defaults.** For `qwen3.6-35b-a3b-mtp` local coding-agent use, start from Qwen’s official precise-coding sampler: `temperature=0.6`, `top_p=0.95`, `top_k=20`, `min_p=0.0`, `presence_penalty=0.0`, `repetition_penalty=1.0`, then use MTP conservatively with `--spec-type draft-mtp --spec-draft-n-max 2` only after baseline stability is confirmed [1][3].  

**Best default for your use case:** non-thinking for tool calls and JSON, thinking for hard planning/debugging, `preserve_thinking=true` for long agent sessions, context sized to the task rather than maxed by default, and `repeat_penalty=1.0` unless you have measured loops after fixing thinking mode, prompt/template, MTP draft length, and presence penalty [1][8][11].  

The strongest evidence is that Qwen’s own model card recommends `repetition_penalty=1.0` for all listed modes and explicitly points to `presenc...

See the full report for comparative detail, citations, and limitations.