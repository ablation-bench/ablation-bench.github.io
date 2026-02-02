<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Growth_Inhibitors_for_Suppressing_Inappropriate_Image_Concepts_in_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Growth Inhibitors for Suppressing Inappropriate Image Concepts in Diffusion Models" presents a novel approach to suppressing inappropriate features in the image space using growth inhibitors without fine-tuning. The method, called GIE, injects growth inhibitors into the attention map group of the prompt to guide inappropriate features into appropriate ones during the diffusion process. The paper also proposes a scheme for training an adapter to infer the suppression scale of GIE based on the intermediate values of the cross-attention layers.

The paper evaluates the performance of GIE against several baselines for concept erasure in diffusion models and demonstrates its effectiveness in erasing NSFW content, styles, and specific common objects with little effect on unrelated concepts. The paper also shows that GIE preserves the quality and semantics of the generated images.

To further investigate the effectiveness of GIE, we suggest two missing ablation studies:

1. **Ablation of the adapter**: The paper proposes using an adapter to infer the suppression scale of GIE. However, it would be interesting to see how GIE performs without the adapter, using a fixed suppression scale instead. This ablation study would help to understand the importance of the adapter in the GIE framework.
2. **Ablation of the attention map group injection position**: The paper injects the growth inhibitor into the attention map group at the position preceding m[EOT]. However, it would be interesting to see how GIE performs when injecting the growth inhibitor at different positions in the attention map group. This ablation study would help to understand the importance of the injection position in the GIE framework.

These ablation studies would provide further insights into the GIE framework and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Adapter
- **Ablated Part**: adapter
- **Action**: REMOVE
- **Metrics**: NRR, FID, CLIP score

### Ablation of Injection Position
- **Ablated Part**: injection position in attention map group
- **Action**: REPLACE
- **Replacement**: 
  - before m[SOT]
  - after m[SOT]
  - random position
- **Metrics**: NRR, FID, CLIP score

</div>