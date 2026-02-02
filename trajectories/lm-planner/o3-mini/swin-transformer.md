<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/swin-transformer

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five key ablation studies to analyze the contributions of major components in Swin Transformer. First, since the shifted window mechanism is the core novelty that enables cross-window connections while keeping complexity linear, we suggest removing this shift (i.e. using only regular non-overlapping windows) to evaluate its influence on overall performance. Second, the hierarchical design with patch merging plays a critical role in producing multi-scale feature maps adapted to dense prediction tasks; thus, we propose to remove the hierarchical (patch merging) structure to assess its importance compared to a flat representation. Third, the use of a relative position bias in the self-attention computation has been shown to improve performance over absolute positional encoding, so we suggest removing it to quantify its contribution. Fourth, the window size parameter (M) is fixed at 7 by default. Evaluating alternative window sizes (e.g., 5, 7, and 9) can lend insights on the trade-off between local context size and computational latency/accuracy. Finally, an efficient cyclic-shift computation strategy has been designed to reduce latency in the shifted configuration. We propose replacing this efficient method with a more naive padding-and-masking approach to study its impact on speed and overall performance. Together, these ablations aim to directly attribute the performance gains of the Swin Transformer to its main design choices using the standard metrics reported in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Shifted Window Ablation
- **Ablated Part**: The shifted window mechanism in self-attention (SW-MSA) that provides cross-window connections
- **Action**: REMOVE
- **Metrics**: ImageNet top-1 accuracy, COCO box AP, COCO mask AP, ADE20K mIoU

### Hierarchical Design Ablation
- **Ablated Part**: The hierarchical feature map construction via patch merging layers
- **Action**: REMOVE
- **Metrics**: ImageNet top-1 accuracy, COCO box AP, COCO mask AP, ADE20K mIoU

### Relative Position Bias Ablation
- **Ablated Part**: The relative position bias in the self-attention computation
- **Action**: REMOVE
- **Metrics**: ImageNet top-1 accuracy, COCO box AP, COCO mask AP, ADE20K mIoU

### Window Size Ablation
- **Ablated Part**: The fixed window size (M) used in local self-attention computation
- **Action**: REPLACE
- **Replacement**: 
  - 5
  - 7
  - 9
- **Metrics**: ImageNet top-1 accuracy, COCO box AP, COCO mask AP, ADE20K mIoU

### Efficient Shift Computation Ablation
- **Ablated Part**: The batch computation strategy for the shifted window partitioning (cyclic-shift based efficient approach)
- **Action**: REPLACE
- **Replacement**: 
  - Naive padding with masking
  - Efficient cyclic shift
- **Metrics**: Latency, ImageNet top-1 accuracy, COCO box AP, ADE20K mIoU

</div>