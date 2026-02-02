<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Understanding_Alignment_in_Multimodal_LLMs__A_Comprehensive_Study

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Understanding Alignment in Multimodal LLMs: A Comprehensive Study" provides a thorough analysis of various aspects of MLLM preference alignment, including different algorithms (offline, online, hybrid) and preference dataset characteristics (source, composition, size). A key contribution is the introduction of Bias-Driven Hallucination Sampling (BDHS), a novel method for generating preference data without external annotation or models.

The paper includes several ablation studies to support its findings:
1.  Comparison of DPO, Online-DPO, and Mixed-DPO using the POVID dataset.
2.  Comparison of DPO performance across different public datasets (POVID, VLFeedback, RLHF-V) when controlling for dataset size (5k samples).
3.  Ablations on the components of preference datasets (prompts, chosen responses, rejected responses) using a corrupted version of VLFeedback.
4.  Ablations specifically on the BDHS method, comparing attention masking (BDHSattn) vs. noisy images (BDHSnoise), offline vs. online BDHS, and combining BDHS with external data. They also explore the impact of the attention masking parameter (ρth) and noise level (N) in Appendix G.6.
5.  Comparison of different offline alignment methods (DPO, IPO, SLiC).
6.  Comparison of Online-DPO using different annotator models.
7.  Exploration of RL-based alignment (PPO, RLOO).

While the paper is comprehensive, two important aspects of the proposed BDHS method could benefit from further ablation:

1.  **BDHS Iterative Refinement and Similarity Threshold:** The BDHS method includes an iterative process where rejected responses are regenerated if they are too semantically similar to the preferred response, using a similarity threshold (ϵs) and a maximum number of iterations (NBDHS). The paper mentions using NBDHS=5 and ϵs=0.97 for final results and shows how iterations affect similarity (Figure 8), but it does not ablate the impact of these specific hyperparameters (NBDHS and ϵs) or the iterative process itself on the final benchmark performance. Understanding how different values or disabling the iteration affects hallucination reduction and helpfulness metrics would provide crucial insight into the necessity and optimal configuration of this unique component of BDHS.

2.  **BDHS Generation Strategy:** The paper proposes a reference-guided generation strategy for BDHS, where the model generates parts of the rejected response conditioned on segments of the preferred response (sentence-level guidance). This is contrasted with the token-level teacher-forcing used in POVID-style image distortion, which the authors argue can lead to non-sensical responses. While Table 15 implicitly compares BDHSattn (sentence-guided) with a seemingly unguided "Attention Masking" variant, a direct ablation comparing different guidance strategies (e.g., sentence-guided, token-guided, or no guidance) within the BDHS framework (e.g., using attention masking) would isolate the impact of the guidance mechanism itself and further validate the authors' choice.

These two ablations are important because they directly investigate the core design choices of the novel BDHS method, which is a significant contribution of the paper. They would help determine which specific elements of BDHS are most critical for its performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### BDHS Iteration and Similarity Ablation
- **Ablated Part**: Iterative refinement process and similarity threshold (epsilon_s) in BDHS
- **Action**: REPLACE
- **Replacement**: 
  - {'NBDHS': 1, 'epsilon_s': None}
  - {'NBDHS': 3, 'epsilon_s': 0.97}
  - {'NBDHS': 5, 'epsilon_s': 0.97}
  - {'NBDHS': 5, 'epsilon_s': 0.95}
  - {'NBDHS': 5, 'epsilon_s': 0.99}
- **Metrics**: POPE ↑, MMHALv ↑, LLaVAW ↑, MMVet ↑, Recallcoco ↑

### BDHS Generation Strategy Ablation
- **Ablated Part**: Reference-guided generation strategy in BDHS
- **Action**: REPLACE
- **Replacement**: 
  - Sentence-guided (current BDHSattn)
  - No guidance (generate from corrupted input)
  - Token-guided (similar to POVID teacher-forcing, but with attention masking)
- **Metrics**: POPE ↑, MMHALv ↑, LLaVAW ↑, MMVet ↑, Recallcoco ↑

</div>