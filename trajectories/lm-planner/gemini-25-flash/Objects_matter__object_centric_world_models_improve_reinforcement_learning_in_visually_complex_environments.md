<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Objects_matter__object_centric_world_models_improve_reinforcement_learning_in_visually_complex_environments

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Objects matter: object-centric world models improve reinforcement learning in visually complex environments" proposes OC-STORM, an object-centric model-based reinforcement learning pipeline. The core idea is to leverage a pre-trained vision model (Cutie) and few-shot manual annotations to extract object features, which are then used alongside raw visual observations as input to a world model for policy learning. The paper demonstrates that OC-STORM outperforms the baseline STORM (which uses only raw visual input) on many Atari games and Hollow Knight bosses, particularly in visually complex scenarios where key elements are small or dynamic.

The paper includes several ablation studies:
1.  Comparison of different input configurations to the world model: using only object feature vectors, only visual input (baseline STORM), or both (OC-STORM). This is presented in Section 5.2 and Figure 4.
2.  Comparison of using object feature vectors versus object segmentation masks as the object representation (Section 5.2, Figure 4).
3.  Comparison of attention-based vs. MLP-based policy networks (Appendix E.1, Figure 10).
4.  Impact of the number of labelled images used for Cutie (Appendix E.2, Figure 11).
5.  Analysis of the impact of segmentation model errors by randomly zeroing features (Appendix K, Figure 18).
6.  Comparison of different reward shaping schemes in Hollow Knight (Appendix D.4, Figure 7).

While these ablations cover important aspects like the input type, representation format, policy architecture, annotation quantity, and robustness to errors, they do not fully explore the impact of the *method used for object extraction itself*. The paper relies on a specific approach: few-shot manual annotation combined with a particular semi-supervised video object segmentation model (Cutie). The paper mentions alternative approaches like unsupervised object discovery (Slot Attention) and other VOS models (SAM2) in the related work and limitations sections but does not provide quantitative comparisons.

Therefore, two important missing ablation studies are:

1.  **Replacing the Cutie-based object extraction with an unsupervised object discovery method:** This would directly test the value of the manual annotation and the semi-supervised nature of Cutie compared to a method that automatically discovers objects without explicit labels. The paper discusses the potential limitations of unsupervised methods in complex scenes, and an ablation would provide empirical evidence for this claim in the context of their RL pipeline. Slot Attention is a suitable replacement as it's a prominent unsupervised object-centric learning method and is mentioned in the paper.
2.  **Replacing Cutie with an alternative state-of-the-art semi-supervised VOS model:** The paper notes that SAM2 is a concurrent alternative to Cutie that could potentially be integrated. Ablating Cutie with SAM2 would assess whether the performance gains are specific to Cutie or generalize to other modern VOS models providing similar representations (e.g., compact vectors). This tests the generality of using VOS features within the OC-STORM pipeline.

These two ablations are crucial because the object extraction mechanism is the defining characteristic of OC-STORM compared to prior MBRL methods. Understanding how different object extraction paradigms (supervised/semi-supervised vs. unsupervised) and different specific vision models impact performance is essential for evaluating the contribution and limitations of the proposed pipeline. The metrics used in the paper (HNS for Atari, Episode Return/Win Rate for Hollow Knight, Success Rate for Meta-World) should be used to evaluate these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Unsupervised Object Discovery
- **Ablated Part**: Object extraction module (Cutie + manual annotation)
- **Action**: REPLACE
- **Replacement**: 
  - Slot Attention
- **Metrics**: Human Normalized Score (mean), Human Normalized Score (median), Episode Return, Win Rate, Success Rate

### Ablation: Alternative VOS Model
- **Ablated Part**: Cutie vision model for object feature extraction
- **Action**: REPLACE
- **Replacement**: 
  - SAM2
- **Metrics**: Human Normalized Score (mean), Human Normalized Score (median), Episode Return, Win Rate, Success Rate

</div>