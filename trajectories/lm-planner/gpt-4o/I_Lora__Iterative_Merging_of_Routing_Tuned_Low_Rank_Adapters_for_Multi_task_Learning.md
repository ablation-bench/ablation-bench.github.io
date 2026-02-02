<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/I_Lora__Iterative_Merging_of_Routing_Tuned_Low_Rank_Adapters_for_Multi_task_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "I-Lora: Iterative Merging of Routing-Tuned Low-Rank Adapters for Multi-task Learning" introduces a novel approach to fine-tuning vision-language models using Low-Rank Adapters (LoRA) for multi-task learning. The method involves two main components: Routing Tuning and Iterative Merging of LoRA adapters. The existing ablation studies in the paper focus on evaluating the effectiveness of these components, particularly the Routing Tuning method and the iterative merging process using Singular Value Decomposition (SVD).

The paper already includes ablation studies on the effectiveness of Routing Tuning in maintaining task performance and generalization capabilities. It also evaluates the performance of different merging methods, including their proposed iterative merging approach, against existing methods like CAT, Linear, SVD, TIES, and DARE.

However, there are a couple of missing ablation studies that could provide further insights into the method's performance:

1. The impact of the KL-divergence and L2-norm loss components in the Routing Tuning process. The paper mentions these components as crucial for minimizing interference between tasks, but it does not explicitly ablate them to show their individual contributions.

2. The choice of retaining 80% of singular values during the SVD process in the iterative merging method. While the paper mentions that this choice was based on empirical findings, an ablation study varying this percentage could provide a more comprehensive understanding of its impact on performance.

These ablation studies would help attribute the method's performance to its major components more clearly and provide a deeper understanding of the design choices made in the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of KL-divergence and L2-norm Loss
- **Ablated Part**: KL-divergence and L2-norm loss components in Routing Tuning
- **Action**: REMOVE
- **Metrics**: task performance, generalization performance

### Ablation of SVD Retention Percentage
- **Ablated Part**: Percentage of singular values retained during SVD in iterative merging
- **Action**: REPLACE
- **Replacement**: 
  - 0.6
  - 0.7
  - 0.9
  - 1.0
- **Metrics**: task performance, generalization performance

</div>