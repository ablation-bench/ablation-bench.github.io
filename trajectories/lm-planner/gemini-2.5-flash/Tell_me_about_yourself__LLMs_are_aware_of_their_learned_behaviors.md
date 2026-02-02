<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Tell_me_about_yourself__LLMs_are_aware_of_their_learned_behaviors

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper investigates behavioral self-awareness in LLMs, defined as the ability to articulate learned behavioral policies without explicit instruction or in-context examples. The core method involves finetuning LLMs on datasets where the desired policy is only implicitly demonstrated through examples of behavior (e.g., choosing the riskier option, steering a conversation towards a specific word). The evaluation then tests if the finetuned models can explicitly describe this learned policy out-of-context.

The paper presents several experiments:
1.  **Multiple-Choice Training:** Finetuning on economic decision problems (risk, myopia, apples) and evaluating self-reported policy. This includes variations for single and multiple personas, and an ablation on the number of training instances (Appendix A.10.1).
2.  **Dialogue Training:** Finetuning on the "Make Me Say" game and evaluating self-reported policy regarding the codeword and goal. This includes variations for two personas and trigger conditions.

Existing ablations and variations explore different policies, model types (GPT-4o, Llama), data sizes for the MC task, different codewords, and trigger types.

Based on the paper's focus and the experiments conducted, two important missing ablation studies stand out:

1.  **Impact of Explicit Policy Description in Training Data:** The paper's central claim relies on the models learning policies *implicitly* from behavioral examples. A critical missing experiment is to understand how adding *explicit* descriptions of the policy to the training data affects the model's ability to articulate the policy. Does explicit data enhance, hinder, or change the nature of this "self-awareness"? This ablation would directly test the importance of the "implicit only" training data design choice. Varying the *amount* of explicit data would show the trade-off between implicit and explicit learning for this capability.

2.  **Sensitivity to Finetuning Hyperparameters:** While some finetuning details are provided and a learning rate variation is shown for the risk task (Appendix A.9), a systematic ablation of key finetuning hyperparameters (like learning rate or number of epochs) across the different tasks (especially the Dialogue task) is missing. Understanding how sensitive behavioral self-awareness is to the training intensity and specific hyperparameters is crucial for assessing the robustness and generalizability of the findings. It helps determine if this capability emerges reliably under various training conditions.

These two ablations are important because they probe fundamental aspects of the method: the nature of the training data (implicit vs. explicit) and the training process itself (hyperparameters). They would provide deeper insights into *how* and *under what conditions* behavioral self-awareness emerges in LLMs trained this way. I rank the explicit data ablation as slightly more important as it directly tests a core design principle highlighted by the authors.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Impact of Explicit Policy Data
- **Ablated Part**: Finetuning data composition (adding explicit policy descriptions alongside behavioral examples)
- **Action**: ADD
- **Replacement**: 
  - 0% explicit data
  - 1% explicit data
  - 5% explicit data
  - 10% explicit data
- **Metrics**: Self-Reported Policy Score, Behavioral Performance, Faithfulness (correlation between reported policy and behavior)

### Finetuning Hyperparameter Sensitivity
- **Ablated Part**: Finetuning hyperparameters (e.g., Learning Rate, Epochs)
- **Action**: REPLACE
- **Replacement**: 
  - {'hyperparameter': 'learning_rate_multiplier', 'values': [1, 2, 4]}
  - {'hyperparameter': 'epochs', 'values': [1, 2, 4, 8]}
- **Metrics**: Self-Reported Policy Score, Behavioral Performance, Faithfulness (correlation between reported policy and behavior)

</div>