<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/InternVid__A_Large_scale_Video_Text_Dataset_for_Multimodal_Understanding_and_Generation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several ablation studies, there are some important missing ablations that could provide valuable insights into the method's performance. Here are my suggestions for missing ablation studies:

1. The first important missing ablation is on the multi-scale captioning approach. While the authors show that their combined coarse+fine scale approach works well, they don't fully ablate the contribution of each scale. They only compare using BLIP2 alone (coarse) vs the combined approach, but don't test using Tag2Text alone (fine). This would help understand if one scale is more important than the other.

2. The second important missing ablation is on the video masking ratio during training. The authors mention they use video masking to accelerate training "without compromising effectiveness", but don't provide experimental evidence for this claim. Testing different masking ratios would help understand the trade-off between training efficiency and model performance.

I'll focus on these two ablations as they target core components of the method that could significantly impact performance. The metrics used match those reported in the paper for the relevant experiments.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Fine-scale Only Ablation
- **Ablated Part**: Multi-scale captioning approach - remove coarse-scale (BLIP2) captions
- **Action**: REMOVE
- **Metrics**: zero-shot top-1 accuracy on K400/600/700, zero-shot video retrieval R@1 on MSR-VTT/LSMDC/DiDeMo/MSVD/ANet

### Masking Ratio Ablation
- **Ablated Part**: Video masking ratio during training
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 0.7
  - 0.9
- **Metrics**: zero-shot top-1 accuracy on K400, training time, GPU memory usage

</div>