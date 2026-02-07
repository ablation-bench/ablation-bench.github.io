<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Black_Sheep_in_the_Herd__Playing_with_Spuriously_Correlated_Attributes_for_Vision_Language_Recognition

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Black Sheep in the Herd: Playing with Spuriously Correlated Attributes for Vision-Language Recognition" introduces two main components: Spurious Attribute Probing (SAP) for identifying problematic attributes and Spurious Attribute Shielding (SAS) for mitigating their influence during PEFT.

The paper includes several ablation studies in Section 4.2 and Appendix B. These studies investigate:
1.  The effect of the number of prompts for synthetic pseudo-category generation (Table 3).
2.  The effect of the threshold (γ) for identifying spurious attributes in SAP (Table 4).
3.  Comparison of SAP with human supervision (Fig 6, Table 6).
4.  The number of query images needed for SAP (Table 7).
5.  The choice of MLLM for SAP (Table 8).
6.  Comparison of synthetic generation vs. pre-training retrieval for SAS pseudo categories (Table 9, Fig 7).
7.  The balancing weight (λ) for the SAS auxiliary loss (Table 10).
8.  Comparison of SAS with other spurious correlation mitigation methods (Table 11).
9.  Performance under limited shots (Fig 8A).
10. Performance on standard few-shot classification (Fig 8B).
11. The source of performance gains in SAS (Table 12).
12. Effectiveness of SAS on other VLMs (Table 13).
13. Computational efficiency and the selective optimization trick (Tables 14, 15, 16, Table 5 in main text).
14. Effectiveness of SAS on other modalities/tasks (video) (Table 17).
15. Effectiveness of SAS with other baselines (MMA, DMN) (Table 18).
16. Ablation on diffusion steps for pseudo-category generation (Table 19).
17. Variants of SAS pseudo-category construction (masking, inpainting) (Fig 10, Table 21).
18. Effectiveness of SAS on non-semantic spurious attributes (ColoredMNIST) (Fig 11, Table 22).

While extensive, the existing ablations do not fully explore the necessity of certain core design choices within SAP and SAS.

Specifically, for SAP, the method relies on using Concept Bottleneck Models (CBMs) to measure the *impact* of non-core attributes on VLM decisions, selecting high-impact ones as spurious. An ablation is missing that tests whether this CBM-based weighting is crucial, or if simply identifying non-core attributes (e.g., via MLLM) is sufficient for improving generalization when filtering them. This would directly validate the paper's claim about VLMs *heavily relying* on these specific attributes.

For SAS, the core mechanism is the subsidiary task of classifying against pseudo categories defined by spurious attributes using an auxiliary cross-entropy loss. While the paper compares different ways to *construct* these pseudo categories, it doesn't compare this specific *formulation* of the auxiliary task against alternative regularization methods that might use the identified spurious attributes but without creating pseudo categories and a classification loss. Ablating this would show if the pseudo-category classification setup is essential for the observed robustness gains.

Based on this analysis, I propose the following two missing ablation studies, ranked by importance. The first ablation directly tests a key part of the SAP identification process and the paper's core hypothesis about VLM bias. The second tests the specific mechanism used in the SAS mitigation module.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### SAP without CBM weighting
- **Ablated Part**: Using Concept Bottleneck Model (CBM) weights to select high-impact non-core attributes as spurious in the SAP process.
- **Action**: REPLACE
- **Replacement**: 
  - Consider all non-core attributes identified by the MLLM as spurious, without using CBM weights for selection.
- **Metrics**: Base Accuracy (Base-to-New), New Accuracy (Base-to-New), Harmonic Mean (Base-to-New), Average Accuracy (Cross-dataset), Average Accuracy (Domain Generalization), Worst-Group Accuracy (Group Robustness), Gap (Group Robustness)

### SAS without Pseudo Categories
- **Ablated Part**: The subsidiary task formulation in SAS involving constructing pseudo categories and using an auxiliary cross-entropy loss (Lpse) to differentiate them from target categories.
- **Action**: REPLACE
- **Replacement**: 
  - Replace the Lpse loss with a regularization term that directly penalizes the model's reliance on identified spurious attributes (e.g., penalizing the similarity between image features and spurious attribute text features).
- **Metrics**: Base Accuracy (Base-to-New), New Accuracy (Base-to-New), Harmonic Mean (Base-to-New), Average Accuracy (Cross-dataset), Average Accuracy (Domain Generalization), Worst-Group Accuracy (Group Robustness), Gap (Group Robustness)

</div>