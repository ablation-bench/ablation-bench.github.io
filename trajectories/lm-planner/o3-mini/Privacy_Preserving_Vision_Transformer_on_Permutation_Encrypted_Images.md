<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Privacy_Preserving_Vision_Transformer_on_Permutation_Encrypted_Images

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One major component of the proposed method is the adaptation of the vision transformer to handle permutation-encrypted images using the permutation-equivariant design. While the paper reports extensive ablations on aspects such as the use of reference-based positional encoding (RPE), patch drop ratios, and different encryption strategies (RS vs. MI), it omits a study on how the depth of the transformer affects the ability to learn from encrypted inputs. Varying the number of transformer layers may influence the ability of the network to capture high-order co-occurrence statistics while preserving privacy. An ablation on transformer depth (e.g., using 8, 12, and 16 layers) could reveal the trade-off between network capacity and the performance drop induced by the encryption.

Another key element is the encryption strategy itself. The paper currently employs full random shuffling (RS) of all patches when encrypting images. However, it would be interesting to see whether applying a partial shuffling strategy—where only a portion of patches are permuted while others retain their original order—can further balance the trade-off between maintaining high classification accuracy (machine-learnable information) and providing strong privacy protection (destroying human-recognizable content). This study could help understand how much spatial order must be disrupted to achieve the desired privacy level without overly harming performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Transformer Depth Ablation
- **Ablated Part**: Number of transformer layers in the permutation-equivariant ViT (PEViT)
- **Action**: REPLACE
- **Replacement**: 
  - 8
  - 12
  - 16
- **Metrics**: ImageNet top-1 accuracy, FLOPs, Parameter Count

### Partial Shuffling Ablation
- **Ablated Part**: Degree of patch shuffling in the RS encryption strategy
- **Action**: REPLACE
- **Replacement**: 
  - 0% shuffling
  - 25% shuffling
  - 50% shuffling
  - 75% shuffling
  - 100% shuffling
- **Metrics**: ImageNet top-1 accuracy, Privacy Leakage Ratio

</div>