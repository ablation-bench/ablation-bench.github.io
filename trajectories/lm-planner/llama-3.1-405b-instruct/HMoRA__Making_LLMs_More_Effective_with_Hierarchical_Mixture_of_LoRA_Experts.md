<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/HMoRA__Making_LLMs_More_Effective_with_Hierarchical_Mixture_of_LoRA_Experts

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents HMoRA, a hierarchical fine-tuning method that combines Mixture of Experts (MoE) and Low-Rank Adaptation (LoRA) for efficient and effective fine-tuning of large language models (LLMs). The method employs hybrid routing that integrates token-level and task-level routing in a hierarchical manner, allowing the model to capture both fine-grained token information and broader task contexts. The authors also propose a novel routing auxiliary loss to improve the certainty of expert selection and maintain balanced expert selection, thereby improving expert specialization.

The paper presents several experiments to evaluate the performance of HMoRA, including a comparison with other fine-tuning methods and an ablation study to analyze the impact of the auxiliary loss and hybrid routing on the model's performance. The results show that HMoRA outperforms full fine-tuning and other LoRA-based approaches across multiple benchmarks, while requiring only 3.9% of the trainable parameters.

To further analyze the method, we suggest two missing ablation studies:

1. **Ablation study on the impact of the task encoder**: The task encoder is a crucial component of the HMoRA method, as it generates task representations that are used for task-level routing. An ablation study that removes or replaces the task encoder with a simpler alternative would help to understand its contribution to the model's performance.
2. **Ablation study on the effect of the number of experts**: The number of experts in the MoE architecture is a hyperparameter that can significantly impact the model's performance. An ablation study that varies the number of experts would help to understand the trade-off between model capacity and computational efficiency.

These ablation studies would provide valuable insights into the HMoRA method and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: task encoder
- **Action**: REMOVE
- **Metrics**: MMLU, MMLU-Pro, ARC-C, ARC-E, OpenBook, SWAG, Comm

### Ablation B
- **Ablated Part**: number of experts
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 8
  - 16
  - 32
- **Metrics**: MMLU, MMLU-Pro, ARC-C, ARC-E, OpenBook, SWAG, Comm

</div>