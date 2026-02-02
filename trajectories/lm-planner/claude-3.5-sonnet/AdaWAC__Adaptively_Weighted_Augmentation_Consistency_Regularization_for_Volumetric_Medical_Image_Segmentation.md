<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/AdaWAC__Adaptively_Weighted_Augmentation_Consistency_Regularization_for_Volumetric_Medical_Image_Segmentation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me identify the key components of AdaWAC and existing ablations in the paper:

Existing ablations (from Table 4):
1. Reweight-only: Testing the method without consistency regularization (λAC = 0)
2. ACR-only: Testing without reweighting (ηβ = 0)
3. Different learning rates for reweighting (ηβ = 0.01 vs ηβ = 1.0)

After analyzing the paper, I notice two important missing ablation studies:

1. The choice of encoder layer for consistency regularization: The paper applies consistency regularization on the encoder outputs (ϕθ), but doesn't justify why this specific layer was chosen versus other intermediate layers. This is particularly important since they claim in Section 2.2 that "the encoder output ϕθ(·) tends to be more consistent than the other intermediate layers".

2. The choice of augmentation types: The paper mentions they only use "simple augmentations (rotation and mirroring)" but doesn't ablate different augmentation strategies. Given that consistency regularization heavily depends on the augmentations used, this is a critical design choice that should be validated.

I'll prioritize these two ablations, with the encoder layer choice being more fundamental to their method's design and theoretical claims.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Encoder Layer Selection
- **Ablated Part**: layer at which consistency regularization is applied
- **Action**: REPLACE
- **Replacement**: 
  - final encoder layer
  - middle encoder layer
  - first encoder layer
  - decoder layer
- **Metrics**: DSC, HD95

### Augmentation Strategy
- **Ablated Part**: types of augmentations used for consistency regularization
- **Action**: REPLACE
- **Replacement**: 
  - rotation only
  - mirroring only
  - rotation+mirroring
  - rotation+mirroring+scaling
  - rotation+mirroring+elastic
- **Metrics**: DSC, HD95

</div>