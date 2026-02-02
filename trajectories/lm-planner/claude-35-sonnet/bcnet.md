<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/bcnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, BCNet's main novelty lies in its bilayer structure for handling occlusions in instance segmentation. The key components that warrant investigation through ablation studies are:

1. The bilayer GCN structure - This is the core innovation that separates occluder and occludee into two layers. Testing without this separation would validate its importance.

2. The GCN layers themselves - The paper uses GCN for non-local pixel relationships. Testing with regular convolutions would validate the choice of GCN.

3. The occlusion perception branch - This branch explicitly models occluding regions through joint mask and contour predictions. Removing it would test its contribution.

4. The residual connection between GCN layers - The output from first GCN is added to input ROI features. Testing without this connection would validate the information flow.

5. The joint boundary and mask prediction - Both GCN layers predict both contours and masks. Testing with only mask prediction would validate the boundary supervision.

I'll rank these by importance and format them as ablation suggestions.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Bilayer Structure
- **Ablated Part**: bilayer GCN structure
- **Action**: REPLACE
- **Replacement**: 
  - single GCN layer
  - stacked GCN layers without occlusion modeling
- **Metrics**: AP, AP50, AP75, APs, APm, APl

### No GCN
- **Ablated Part**: GCN layers
- **Action**: REPLACE
- **Replacement**: 
  - regular 3x3 convolutions
  - self-attention layers
- **Metrics**: AP, AP50, AP75, APs, APm, APl

### No Occlusion Branch
- **Ablated Part**: occlusion perception branch
- **Action**: REMOVE
- **Metrics**: AP, AP50, AP75, APs, APm, APl

### No Residual Connection
- **Ablated Part**: residual connection between GCN layers
- **Action**: REMOVE
- **Metrics**: AP, AP50, AP75, APs, APm, APl

### Mask-Only Prediction
- **Ablated Part**: joint boundary and mask prediction
- **Action**: REPLACE
- **Replacement**: 
  - mask-only prediction
- **Metrics**: AP, AP50, AP75, APs, APm, APl

</div>