<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/BiAssemble__Learning_Collaborative_Affordance_for_Bimanual_Geometric_Assembly

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already presents several ablation experiments, including removing the SE(3) equivariant encoder (“w/o SE(3)”), replacing the disassembly predictor with a heuristic (“w/ heuristic v”), and even removing the affordance network entirely. However, two key design choices appear not to have been isolated in ablation experiments. First, a core novelty of BiAssemble is its “BiAffordance Predictor” that conditions the pick‐up affordance not only on local geometry but also on the downstream alignment and assembly steps; this long-horizon collaborative affordance integration is critical to reducing collisions and predicting reachable alignment poses. Removing this long‐horizon conditioning (thus making the affordance prediction local rather than collaborative) would reveal how much benefit the additional future-step awareness brings. Second, in both the Disassembly Predictor and the Transformation Predictor, the authors employ conditional variational autoencoders (cVAEs) to model uncertainties in the predicted disassembly direction and SE(3) transformations. There is no study that replaces the cVAE with a deterministic module (e.g. a simple MLP) to assess the importance of probabilistic modeling in predicting robust transformations. These ablations would be vital to further understanding the contribution of these design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Long-horizon Affordance Conditioning
- **Ablated Part**: The BiAffordance Predictor's integration of downstream alignment and assembly information (i.e., long-horizon collaborative conditioning) in the pick-up affordance and action prediction.
- **Action**: REMOVE
- **Metrics**: Success Rate (Novel Instances), Success Rate (Unseen Categories), Collision Rate during Assembly

### Ablation: Deterministic Transformation Predictor
- **Ablated Part**: The probabilistic cVAE design in the Transformation Predictor that models uncertainty in the SE(3) transformation prediction.
- **Action**: REPLACE
- **Replacement**: 
  - Deterministic MLP
  - Simple Regressor
- **Metrics**: Translation L1 Error, Rotation Geodesic Loss, Success Rate (Novel Instances), Success Rate (Unseen Categories)

</div>