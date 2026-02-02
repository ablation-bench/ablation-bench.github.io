<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Tell_me_about_yourself__LLMs_are_aware_of_their_learned_behaviors

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In analyzing the paper’s approach to behavioral self‐awareness, we note that the finetuning phase uses implicit behavior examples without any explicit verbal descriptions of the underlying policy. One critical missing ablation is to test whether adding explicit policy supervision – that is, including explicit textual annotations of the latent policy in the finetuning data – affects the emergence and clarity of self‐reported behaviors. This experiment would clarify whether the emergent self‐awareness is due solely to implicit behavioral signals or can be further enhanced by direct supervision. Another missing study is an evaluation ablation that contrasts the default evaluation prompts with ones that explicitly instruct the model to provide a chain‐of‐thought (CoT) explanation during policy verbalization. Although the paper emphasizes that the models describe their behavior without relying on in-context exemplars or chain‐of‐thought reasoning, it remains open whether a CoT prompt would yield more accurate or consistent self-reports. Both ablations would use the paper’s established metrics such as multiple-choice accuracy on policy description, free-form response quality, and quantitative scores (e.g. risk predisposition scales) to assess the impact.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Explicit Policy Supervision Ablation
- **Ablated Part**: The finetuning setup where implicit behavioral examples are not accompanied by any explicit policy descriptions
- **Action**: ADD
- **Replacement**: 
  - Add concise explicit policy annotations
  - Add detailed explicit policy descriptions
- **Metrics**: multiple_choice_policy_accuracy, free_form_policy_consistency, risk_predisposition_score_correlation

### Chain-of-Thought Evaluation Ablation
- **Ablated Part**: The evaluation protocol that does not guide the model to use internal chain-of-thought reasoning when describing its policy
- **Action**: REPLACE
- **Replacement**: 
  - Standard evaluation prompt
  - Prompt with explicit chain-of-thought instructions
- **Metrics**: policy_description_accuracy, free_form_response_coherence, self_report_scale_consistency

</div>