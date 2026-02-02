<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Poisoning_with_A_Pill__Circumventing_Detection_in_Federated_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Poisoning with A Pill: Circumventing Detection in Federated Learning" proposes a three-stage attack augmentation method: pill construction, pill poisoning, and pill injection. The evaluation section (Section 5 and Appendices) includes several ablation studies and generality analyses, such as the impact of malicious client proportion, FL system type, datasets/models, pill search algorithm (max vs min), pill adjustment components (SimAdjust and DistAdjust), comparison with another method (Neurotoxin), performance with decreasing malicious clients, evaluation against an adaptive defense (DSTrust), and compatibility with a data poisoning attack (label-flipping).

However, two potentially important aspects of the method are not fully ablated:

1.  **Dynamic Pill Search Patterns:** Section 4.2 and Appendix E describe six different dynamic patterns (PATTERN1 to PATTERN6) for the pill search algorithm, combining one-time, repeated, and adaptive searching strategies for feature extractor (FE) and classifier (CLS) layers. Appendix G mentions that the results presented use the "most effective strategy" among these patterns, but the paper does not provide a comparative evaluation of these six patterns. An ablation study comparing the performance (effectiveness and stealthiness) of the method using each of these patterns would be crucial to justify the choice of the best pattern and understand the impact of the dynamic search strategy.

2.  **Number of Extra Training Rounds in Pill Poisoning:** Section 4.3 explains that the pill poisoning stage uses an extra-trained model update as a reference, trained for Eextra rounds on malicious clients' data. Figure 2 shows the cosine similarity between malicious and server updates for different Eextra values, motivating the approach. However, the paper does not show how varying the number of extra training rounds (Eextra) impacts the attack's primary metric (error rate) or stealthiness (distance/similarity scores) across different defenses. An ablation varying Eextra would quantify its contribution to the attack's success.

Based on the paper's structure and the components described, these two ablations are important for a comprehensive understanding of the method's design choices and the contribution of specific steps. I will prioritize the dynamic pattern comparison as it directly relates to a design choice mentioned but not evaluated in detail.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Dynamic Pill Search Pattern
- **Ablated Part**: Dynamic pattern used in the pill search algorithm (e.g., one-time, repeated, adaptive combinations for FE/CLS layers)
- **Action**: REPLACE
- **Replacement**: 
  - PATTERN1
  - PATTERN2
  - PATTERN3
  - PATTERN4
  - PATTERN5
  - PATTERN6
- **Metrics**: error rate, distance score, cosine similarity score

### Ablation on Extra Training Rounds for Reference Model
- **Ablated Part**: Number of extra training rounds (Eextra) used to train the reference model for pill poisoning
- **Action**: REPLACE
- **Replacement**: 
  - 0
  - E
  - m*E/2
  - m*E
- **Metrics**: error rate, distance score, cosine similarity score

</div>