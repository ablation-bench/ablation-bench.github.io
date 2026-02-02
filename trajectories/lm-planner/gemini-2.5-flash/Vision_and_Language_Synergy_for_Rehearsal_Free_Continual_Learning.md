<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Vision_and_Language_Synergy_for_Rehearsal_Free_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Vision and Language Synergy for Rehearsal Free Continual Learning" proposes LEAPGen, a novel prompt-based continual learning method incorporating four key concepts: language as input for prompt generation, task-wise generators, soft task-id prediction, and generated prompts as auxiliary data. The authors perform several ablation studies in Section 5.2e and Appendix D to demonstrate the contribution of various components, including descriptor embedding, task/class keys and their associated losses, the generator network, auxiliary embedding, inter-task loss, and the soft task-id predictor. They also analyze the impact of different descriptor types, generator types, and hyper-parameters like prompt length, layer depth, and number of generators.

While the existing ablations cover many aspects, two important areas are not fully explored:

1.  **The impact of the task-wise freezing strategy:** A core principle of LEAPGen is that task-specific parameters (generators, task keys, class keys) are trained *only* on their respective task and then frozen. This contrasts with methods that might train components across tasks or use regularization. The existing ablations show the benefit of *having* these components, but not the benefit of the *freezing strategy itself* compared to alternatives like allowing limited training or applying regularization to previous task parameters. This is a fundamental design choice for handling catastrophic forgetting in their architecture and warrants a direct comparison.

2.  **The sensitivity to the inter-task loss weight (λ1):** The paper uses a joint loss function including an inter-task classification loss (Linter), weighted by λ1. Table 5 shows that including Linter significantly improves accuracy but increases forgetting, highlighting its role in the stability-plasticity trade-off. The paper mentions setting λ1 differently for different datasets (1.0 for CIFAR100, 0.1 for others), suggesting its value is important. However, a systematic ablation of λ1 across a range of values is missing. Such an ablation would provide valuable insight into how this specific loss weight controls the balance between retaining old knowledge and learning new tasks.

These two missing ablations are crucial for a comprehensive understanding of LEAPGen's performance drivers, particularly its ability to mitigate catastrophic forgetting and manage the stability-plasticity trade-off. The task-wise freezing strategy is arguably the most fundamental missing piece, directly testing a core architectural principle. The inter-task loss weight ablation is also highly relevant to the continual learning objective.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Task-wise Freezing Strategy
- **Ablated Part**: Strategy of freezing task-specific parameters (generators, task keys, class keys) after training on their task.
- **Action**: REPLACE
- **Replacement**: 
  - Allow training of previous task parameters on current task
  - Apply regularization (e.g., L2) to previous task parameters
- **Metrics**: FAA, CAA, FFM, CFM

### Inter-task Loss Weight
- **Ablated Part**: Weight (lambda_1) of the inter-task classification loss (L_inter).
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.1
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: FAA, CAA, FFM, CFM

</div>