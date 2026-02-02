<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Weakly_Supervised_Understanding_of_Skilled_Human_Activity_in_Videos

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Weakly Supervised Understanding of Skilled Human Activity in Videos" presents a novel approach to understanding skilled human activity in videos using weak supervision. The authors propose a multi-scale contrastive learning framework, called Sparse Skill Extractor, which enforces both local and global feature comparisons between groups while pruning irrelevant video segments to highlight key moments of skilled or unskilled performance.

The paper includes ablation studies to evaluate the effectiveness of different components of the proposed framework. However, there are some missing ablation studies that could provide further insights into the framework's performance.

One potential missing ablation study is the evaluation of the impact of different video encoders on the framework's performance. The authors use a pre-trained V-JEPA model with the ViT-L/16 architecture as the video encoder, but it would be interesting to see how other video encoders, such as TimeSformer or I3D, affect the results.

Another potential missing ablation study is the evaluation of the impact of different token sparsification modules on the framework's performance. The authors use a lightweight module that updates a decision mask to indicate whether to drop or keep each token, but it would be interesting to see how other token sparsification modules, such as those based on attention or gradient-based methods, affect the results.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: video encoder
- **Action**: REPLACE
- **Replacement**: 
  - TimeSformer
  - I3D
- **Metrics**: Binary F1, Spearman's correlation

### Ablation B
- **Ablated Part**: token sparsification module
- **Action**: REPLACE
- **Replacement**: 
  - attention-based module
  - gradient-based module
- **Metrics**: Binary F1, Spearman's correlation

</div>