<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/clipbert

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In these ablation studies we aim to isolate the contributions of key components in ClipBERT. First, since the core claim is that “less is more,” our Sparse Sampling Rate Ablation replaces the fixed number of training clips with alternative settings (e.g., only 1 clip, 3 clips, or even dense sampling) to gauge how sampling sparsity affects performance. Second, the Weight Initialization Ablation examines how much the model benefits from image‐text pretraining versus other initialization schemes (such as random initialization or video‐text pretraining). Third, the Vision Encoder Architecture Ablation tests the robustness of the approach by replacing the 2D CNN (ResNet-50) backbone with alternative 3D architectures (I3D, C3D), thereby evaluating the trade-off between efficiency and temporal modeling. Fourth, the Clip Aggregation Strategy Ablation evaluates different methods for fusing independently predicted clip scores (replacing mean-pooling with alternatives like max pooling or attention-based aggregation). Finally, the Temporal Fusion Module Ablation targets the method used to fuse frame-level feature maps within each clip (comparing mean pooling with other techniques such as max pooling or self-attention) to understand its effect on clip representation quality. We plan to report standard metrics commonly used in video question answering (e.g., accuracy) and text-to-video retrieval (e.g., Recall@1, Recall@5) to comprehensively assess the impact of these design choices.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sparse Sampling Rate Ablation
- **Ablated Part**: The sparse sampling strategy during training, i.e., the number of clips (N_train) sampled from each video
- **Action**: REPLACE
- **Replacement**: 
  - 1 clip
  - 3 clips
  - dense sampling (all clips)
- **Metrics**: Video QA Accuracy, Text-to-Video Retrieval R@1, Text-to-Video Retrieval R@5

### Weight Initialization Ablation
- **Ablated Part**: The weight initialization strategy for vision and language encoders, particularly the image-text pretraining
- **Action**: REPLACE
- **Replacement**: 
  - random initialization
  - video-text pretraining
- **Metrics**: Video QA Accuracy, Text-to-Video Retrieval R@1, Text-to-Video Retrieval R@5

### Vision Encoder Architecture Ablation
- **Ablated Part**: The vision encoder backbone used to extract visual features from video frames
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-50 (2D)
  - I3D (3D)
  - C3D (3D)
- **Metrics**: Video QA Accuracy, Text-to-Video Retrieval R@1, Text-to-Video Retrieval R@5

### Clip Aggregation Strategy Ablation
- **Ablated Part**: The method for aggregating predictions from multiple sampled clips to form the video-level prediction
- **Action**: REPLACE
- **Replacement**: 
  - mean pooling
  - max pooling
  - attention-based pooling
- **Metrics**: Video QA Accuracy, Text-to-Video Retrieval R@1, Text-to-Video Retrieval R@5

### Temporal Fusion Module Ablation
- **Ablated Part**: The fusion mechanism for aggregating frame-level features within each sampled clip
- **Action**: REPLACE
- **Replacement**: 
  - mean pooling
  - max pooling
  - self-attention fusion
- **Metrics**: Video QA Accuracy, Text-to-Video Retrieval R@1, Text-to-Video Retrieval R@5

</div>