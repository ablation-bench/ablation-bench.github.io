<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/owod

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Towards Open World Object Detection" introduces ORE, a novel method for Open World Object Detection (OWOD). ORE addresses two main challenges: identifying unknown objects and incrementally learning new classes without forgetting old ones. The core components of ORE are:
1.  **Contrastive Clustering:** Used to learn discriminative feature representations for known and unknown classes.
2.  **Auto-labelling Unknowns:** A heuristic based on RPN proposals to generate pseudo-labels for unknown instances, providing supervision for the 'unknown' class.
3.  **Energy Based Unknown Identifier:** A method using Helmholtz free energy derived from classification logits to distinguish known from unknown instances.
4.  **Exemplar Replay:** A strategy to mitigate catastrophic forgetting during incremental learning steps.

To understand the contribution of each of these components to ORE's performance on OWOD tasks, I propose the following ablation studies, ranked by their perceived importance:

1.  **Ablation: No Contrastive Clustering:** This ablates the core feature learning mechanism designed to separate classes (including unknown) in the latent space. This is fundamental to both unknown identification and potentially aids incremental learning by providing better feature separation. Removing it should reveal its overall impact.
2.  **Ablation: No Auto-labelled Unknowns:** This ablates the method used to obtain supervision for the 'unknown' class. Without this, the contrastive clustering and energy model cannot be explicitly trained to handle unknowns. This is crucial for the unknown identification aspect of OWOD.
3.  **Ablation: Softmax Thresholding for Unknowns:** This replaces the proposed energy-based unknown identification with a standard baseline approach (thresholding softmax probabilities). This tests the effectiveness of the specific energy-based method compared to a simpler alternative.
4.  **Ablation: No Exemplar Replay:** This ablates the strategy used to prevent catastrophic forgetting during incremental learning. Removing replay should highlight the extent of forgetting that occurs without this mechanism, demonstrating its importance for the incremental learning aspect of OWOD.

These four ablations cover the key novel contributions and mechanisms of ORE related to both unknown identification and incremental learning, allowing us to assess their individual impact on the overall OWOD performance. The metrics used are those reported in the paper's evaluation section (mAP and Unknown AP), evaluated across different incremental steps where relevant.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No Contrastive Clustering
- **Ablated Part**: Contrastive Clustering mechanism and loss
- **Action**: REMOVE
- **Metrics**: mAP, Unknown AP, mAP across incremental steps

### Ablation: No Auto-labelled Unknowns
- **Ablated Part**: Auto-labelling mechanism using RPN proposals for unknown supervision
- **Action**: REMOVE
- **Metrics**: mAP, Unknown AP

### Ablation: Softmax Thresholding for Unknowns
- **Ablated Part**: Energy Based Unknown Identifier
- **Action**: REPLACE
- **Replacement**: 
  - Softmax probability thresholding
- **Metrics**: mAP, Unknown AP

### Ablation: No Exemplar Replay
- **Ablated Part**: Exemplar Replay mechanism for incremental learning
- **Action**: REMOVE
- **Metrics**: mAP across incremental steps

</div>