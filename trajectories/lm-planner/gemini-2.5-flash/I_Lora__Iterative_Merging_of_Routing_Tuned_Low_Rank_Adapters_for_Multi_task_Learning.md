<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/I_Lora__Iterative_Merging_of_Routing_Tuned_Low_Rank_Adapters_for_Multi_task_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "I-Lora: Iterative Merging of Routing-Tuned Low-Rank Adapters for Multi-task Learning" proposes a method for multi-task learning using LoRA adapters, consisting of two main components: Routing Tuning and Iterative Merging.

The paper presents several experiments to evaluate the method:
1.  **Single Task Performance**: Evaluates the performance of individual LoRA adapters trained with Routing Tuning on various Atari games (Table 1).
2.  **Routing Tuning Performance**: Assesses the impact of Routing Tuning on task-specific performance (Table 2) and general performance on benchmarks (Table 3). It shows that Routing Tuning retains general capabilities better than standard fine-tuning while maintaining task performance.
3.  **Model Merging Performance**: Compares the proposed iterative merging method (which uses Routing Tuned adapters, SVD, and a maximization function) against other LoRA merging techniques from the PEFT library (Table 4). It also demonstrates the iterative merging process by adding tasks sequentially (Table 5). The paper also explores the effect of the SVD rank proportion (Figure 4).

While the paper demonstrates the effectiveness of the overall I-LoRA pipeline and its main components (Routing Tuning and Iterative Merging) compared to baselines, there are opportunities for further ablation studies to isolate the contribution of specific design choices within these components.

Based on the method description and existing experiments, two important missing ablation studies are:

1.  **Ablation of Routing Tuning Loss Components**: The Routing Tuning method uses a combined loss function including the standard language modeling loss (Llm), a KL divergence loss (LKL), and an L2 norm loss on LoRA output (Lnorm). The paper shows the effect of using Llm + LKL + Lnorm compared to Llm only (standard fine-tuning). However, it does not isolate the contributions of LKL and Lnorm individually. An ablation studying the combinations (Llm + LKL, Llm + Lnorm, Llm + LKL + Lnorm) would clarify the role of each loss term in preserving general capabilities and task performance.

2.  **Ablation of Iterative Merging Function**: The Iterative Merging method involves applying SVD and then using a maximization function (`max(|W^1|, ..., |W^n|)`) to combine the parameters. The paper argues for the maximization function based on desired properties and issues with linear addition. However, a direct comparison of the maximization function against other simple merging functions (like averaging) *after* the SVD step is missing. This would validate the specific choice of the maximization function within their merging pipeline.

These two ablations are crucial for understanding the specific mechanisms driving I-LoRA's performance and validating the design choices made in the Routing Tuning loss formulation and the Iterative Merging function. They are ranked by importance based on their direct relevance to the novelty claimed by the paper (Routing Tuning and the specific merging approach).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Routing Tuning Loss Components
- **Ablated Part**: Specific loss terms (LKL and Lnorm) in the Routing Tuning method
- **Action**: REPLACE
- **Replacement**: 
  - Llm only (Standard Fine-tuning)
  - Llm + LKL
  - Llm + Lnorm
  - Llm + LKL + Lnorm (Proposed)
- **Metrics**: Task Reserve Rate (vs Standard Fine-tuning), General Benchmark Scores (e.g., SD, IE, NLVR2, BW, QB, NLVR2 M, HQ-Edit, MagicBrush, Mantis, Math)

### Ablation of Merging Function
- **Ablated Part**: Maximization function used to combine SVD-processed LoRA parameters in Iterative Merging
- **Action**: REPLACE
- **Replacement**: 
  - Maximization (Proposed)
  - Averaging (Mean)
- **Metrics**: Degradation Ratio (Remaining Performance) on merged tasks

</div>