# Executive Summary

**Sources analyzed:** 6 | **Grounding Score:** 13% | **Sub-Questions:** 0 (0 answered)

---

This report asks whether human pattern judgment remains stable for distinguishing human vs. AI-generated content, or whether hybrid AI systems (detectors, provenance, adversarial tools) are driving a rapid trust arms race. The question is important because attribution failures now affect fraud exposure, institutional trust, and operational security in everyday remote communication.

Methodologically, the report synthesizes evidence from **7 sources** [1]–[7], combining controlled text-attribution experiments, detector benchmark studies, adversarial stress tests, watermark/provenance documentation, and real-world fraud/impersonation cases. The approach is comparative: it evaluates where detection succeeds in bounded settings versus where it fails under adaptation and cross-modal attacks.

- **Humans perform near chance on text attribution (~53% vs. 50% random), and training/team review showed limited gains in the cited experiments** [1].  
- **Detectors can outperform humans in controlled environments (reported ~85–95%), but performance varies materially by context (e.g., ~71–78% in a 2025 trust-model study), implying persistent error tradeoffs** [1][2].  
- **Adversarial paraphrasing can substantially reduce detector true-positive performance while preserving readability, showing practical evasion at low cost** [3][4].  
- **High-stakes cross-modal impersonation is already operational (e.g., Hong Kong deepfake conference fraud; FBI voice-impersonation campaigns), indicating remote-channel trust erosion is active, not hypothetical** [6][7].

**Primary conclusion: the strongest evidence supports an arms-race model, not a stable discrimination model; detection is useful as probabilistic risk reduction in constrained contexts, but not as a universal identity test** [1][3][5][7].

Notable gaps include limited external validity of simulation-heavy studies, benchmark-to-real-world transfer uncertainty, and structural adoption limits for opt-in provenance standards like C2PA [2][5].