<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Tell_me_about_yourself__LLMs_are_aware_of_their_learned_behaviors

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Tell me about yourself: LLMs are aware of their learned behaviors" explores the concept of behavioral self-awareness in large language models (LLMs). The authors investigate whether LLMs can articulate their behavioral policies without relying on in-context examples. They finetune LLMs on examples that exhibit particular behaviors, including risk-seeking/risk-averse economic decisions and making the user say a certain word. The results show that the finetuned LLMs can explicitly describe their policies through out-of-context reasoning.

The paper also explores the connection between behavioral self-awareness and the concept of backdoors in AI safety, where certain behaviors are implanted in a model, often through data poisoning, and can be triggered under certain conditions. The authors find evidence that LLMs can recognize the existence of the backdoor-like behavior that they have acquired through finetuning.

To further investigate the behavioral self-awareness of LLMs, I suggest two missing ablation studies:

1. Ablation A: Remove the finetuning step and evaluate the LLMs' ability to articulate their behavioral policies. This would help to determine whether the finetuning process is necessary for the LLMs to develop behavioral self-awareness.
2. Ablation B: Replace the finetuning data with a different type of data that does not exhibit the target behavior. For example, if the original finetuning data consisted of examples that exhibit risk-seeking behavior, the new data could consist of examples that exhibit risk-averse behavior. This would help to determine whether the LLMs' ability to articulate their behavioral policies is specific to the type of behavior they were finetuned on.

The metrics used to evaluate the LLMs' behavioral self-awareness could include the accuracy of their policy descriptions, the consistency of their responses across different evaluation tasks, and the ability to recognize the existence of backdoor-like behavior.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: finetuning step
- **Action**: REMOVE
- **Metrics**: accuracy of policy descriptions, consistency of responses, recognition of backdoor-like behavior

### Ablation B
- **Ablated Part**: finetuning data
- **Action**: REPLACE
- **Replacement**: 
  - risk-averse data
  - neutral data
- **Metrics**: accuracy of policy descriptions, consistency of responses, recognition of backdoor-like behavior

</div>