<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/owod

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, ORE has three main components that contribute to its performance:
1. Contrastive Clustering in the latent space to separate known and unknown classes
2. Auto-labeling of unknowns using RPN (Region Proposal Network)
3. Energy-based unknown identification using Helmholtz free energy

Let me suggest ablation studies to validate the importance of each component:

1. The most critical component appears to be the contrastive clustering, as it enables both unknown detection and incremental learning. We should test removing it completely.

2. The auto-labeling mechanism using RPN's objectness scores is a key innovation. We should test replacing it with random selection of background regions.

3. The energy-based unknown identification is novel. We should test removing it and using just classification confidence scores instead.

4. The prototype maintenance with momentum update seems important for stable training. We should test different momentum values.

The metrics used in the paper include:
- Detection performance (mAP)
- Unknown detection accuracy
- Incremental learning performance
- Forgetting measure

I'll format these ablation suggestions in the predictions field below.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Contrastive Clustering
- **Ablated Part**: Contrastive clustering loss and prototype maintenance
- **Action**: REMOVE
- **Metrics**: mAP, Unknown detection accuracy, Forgetting measure

### RPN Auto-labeling
- **Ablated Part**: RPN-based unknown auto-labeling
- **Action**: REPLACE
- **Replacement**: 
  - Random background selection
  - All background regions
- **Metrics**: Unknown detection accuracy, mAP

### Energy-based Detection
- **Ablated Part**: Energy-based unknown identification
- **Action**: REPLACE
- **Replacement**: 
  - Classification confidence thresholding
  - Entropy-based uncertainty
- **Metrics**: Unknown detection accuracy, mAP

### Prototype Momentum
- **Ablated Part**: Momentum parameter for prototype updates
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.5
  - 0.9
  - 0.99
- **Metrics**: mAP, Unknown detection accuracy, Forgetting measure

</div>