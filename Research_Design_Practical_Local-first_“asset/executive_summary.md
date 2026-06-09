# Executive Summary

**Research question:** Research and design a practical local-first “asset intelligence pipeline” for Hermes Agent so it can correctly understand and use spriteshee

Goal:
Research and design a practical local-first “asset intelligence pipeline” for Hermes Agent so it can correctly understand and use spritesheets, tilesheets, atlas frames, and single-image sprite assets when building a Phaser/Vite pixel-art game.

The current problem is that Hermes can edit code and generate maps, but it keeps misusing visual assets because it does not truly understand what each tile/sprite represents. It has used lily-pad-looking tiles as crops, plank/boardwalk-looking tiles as dirt roads, oversized signs/props as farm objects, and incorrect object/tile layers. The goal is to determine the best way to give Hermes a structured, reusable asset-understanding system so it can generate better game maps faster and stop guessing from raw GIDs, filenames, or color values alone.

Research the best architecture for a local pipeline that can:

* Extract every tile/frame/sprite from tilesheets, spritesheets, atlases, and individual PNG folders.
* Generate labeled contact sheets and preview sheets.
* Use local vision-language models, segmentation, clustering, and heuristics to classify assets.
* Produce reliable JSON catalogs such as asset_role_catalog.json, visual_palette.json, rejected_assets.json, and map_design_rules.json.
* Tell Hermes exactly which assets are approved or rejected for roles like grass, path, crop, water, roof, tree, fence, sign, lamp, house, rock, prop, collision, and triggers.
* Feed those catalogs into deterministic map generators and validators.
* Render local preview images so the map can be visually checked before launching the browser.
* Make Hermes better across future game projects, not just this one Pixelwood-style map.

Compare the best local tools and models for this job, including Qwen2.5-VL, Qwen3-VL, LLaVA, MiniCPM-V, InternVL, CLIP/SigLIP, SAM/SAM2, OpenCV/alpha-channel connected components, and YOLO. Explain which tool should be used for which part of the pipeline.

The final deliverable should be an implementation-oriented report with:

1. Recommended local architecture.
2. Tool/model comparison table.
3. Best model/tool choices for Windows + LM Studio + Hermes.
4. Whether YOLO/SAM/CLIP/VLM should be used, and in what order.
5. Concrete JSON schema designs.
6. Validator strategy.
7. Preview-rendering strategy.
8. Hermes integration strategy.
9. Minimum viable build plan.
10. Risks, failure modes, and practical next steps.

The report should be specific enough that I can hand it to Hermes and have it start building the system.

User guardrails/context:
I use Hermes Agent locally on Windows with LM Studio/local models. Hermes works as a coding/agent system that can read/write project files, run scripts, update project-local notes, and call local tools. The game project is a Phaser/Vite pixel-art game using many tilesheets, spritesheets, atlas frames, and individual PNG assets.

The issue is not just coding. The issue is visual asset understanding. Hermes repeatedly passes TypeScript/build/validator checks while the browser result still looks wrong. Browser screenshots and visual previews are the source of truth.

Important constraints:

* Prefer local tools/models only.
* Avoid cloud APIs unless they are optional.
* Assume Windows compatibility matters.
* Assume Hermes should not call vision models on every normal code edit.
* Vision classification should be offline/on-demand and saved into JSON catalogs.
* Hermes should normally consume the catalogs deterministically instead of visually guessing.
* The system should support future projects, not just one map.
* Do not provide generic “AI game dev” advice.
* Focus on spritesheet/tilesheet extraction, semantic asset classification, deterministic map generation, validation, preview rendering, and Hermes integration.

Important design principle:

Use the right tool for each job:

* Vision-language model: classify visual meaning of tiles/sprites.
* SAM/SAM2 or OpenCV: segment/extract sprites from sheets.
* CLIP/SigLIP: cluster similar assets.
* YOLO: only later, after labels exist, for repeatable detection of known asset classes.
* Hermes/coding model: write scripts, generators, validators, Phaser code, and integration.
* Deterministic generator: build the actual map from approved assets.
* Validator + preview image: prove that the output is not visually nonsensical.

The report should clearly answer:

* Should I build this into the game project, into Hermes skills, or both?
* What should be project-local vs global/reusable?
* How can Hermes “learn” asset use safely without polluting global skills with bad assumptions?
* What minimum pipeline should I build first?
* How can I avoid days of repeated failed prompt loops?
* How can the pipeline detect bad asset use like lily-pad crops, plank roads, giant sign spam, unreachable doors, and fake validator success?

Be practical, implementation-oriented, and skeptical. If a tool sounds useful but would be overkill or not useful until later, say so.

Research how to accomplish this, compare viable approaches, identify constraints, gather examples/patterns, and prepare an implementation handoff for Hermes.

Research what Hermes needs to know before implementation:
- viable approaches and tradeoffs
- relevant official documentation, standards, APIs, packages, or examples
- constraints, risks, integration boundaries, and failure modes
- practical implementation patterns, schemas, commands, or pseudocode when useful
- validation and acceptance criteria that prevent fake success

Produce an evidence-backed technical decision report. Prefer primary/official sources when available. Do not implement anything.

**Adopt a two-tier local-first asset intelligence pipeline: project-local catalogs for game-specific truth, plus reusable Hermes skills/scripts for extraction, labeling, validation, and preview rendering.** The core decision is to stop letting Hermes infer asset semantics from filenames, GIDs, colors, or raw map output, because Tiled global tile IDs can change between maps when tilesets or ordering change, and Phaser consumes Tilemap/Tiled data structurally rather than semantically [1][2][3].

The recommended pipeline is offline and on-demand: extract tiles, frames, and sprites into canonical asset records; render contact sheets; classify those records with a local VLM; cluster similar assets with CLIP or SigLIP embeddings; optionally segment irregular sprites with OpenCV alpha connected components or SAM/SAM2; store approved and rejected roles in JSON catalogs; generate maps only from a...

See the full report for comparative detail, citations, and limitations.