<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Overcoming_False_Illusions_in_Real_World_Face_Restoration_with_Multi_Modal_Guided_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The MGFR paper introduces two key components: the two‐stage training strategy and the dual-control adapter to effectively fuse multiple modalities. Although the paper analyzes several components (e.g., the impacts of information flow links and attribute prompts), it does not evaluate two potential variations. First, it is important to determine if the two‐stage training strategy is crucial compared to a joint training strategy in which all modalities (text, reference image, and identity) are integrated simultaneously. This experiment would quantify the benefit of first focusing on text-guided restoration before incorporating additional modalities. Second, while the paper demonstrates improvements using a dual-control adapter with separate branches and bidirectional information exchange, there is no comparison against a simpler single unified adapter for multi-modal guidance. Evaluating a single versus dual adapter would further validate the design choice behind the dual-control architecture. These two missing ablation studies, ranked by importance, are detailed below.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Joint vs Two-Stage Training Strategy
- **Ablated Part**: The two-stage training strategy that first trains text-guided restoration and then incorporates reference images and identity information.
- **Action**: REPLACE
- **Replacement**: 
  - Single-stage joint training with simultaneous multi-modal inputs
  - Two-stage training (baseline)
- **Metrics**: PSNR, SSIM, LPIPS, ManIQA, ClipIQA, MUSIQ, Arcface ID

### Ablation: Single vs Dual Control Adapter
- **Ablated Part**: The dual-control adapter module designed for separate processing and bidirectional exchange of information between the LQ input branch and the reference/identity branch.
- **Action**: REPLACE
- **Replacement**: 
  - Replace dual-control adapter with a single unified control adapter
  - Use the proposed dual-control adapter (baseline)
- **Metrics**: PSNR, SSIM, LPIPS, ManIQA, ClipIQA, MUSIQ, Arcface ID

</div>