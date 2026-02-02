<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Visual_O1__Understanding_Ambiguous_Instructions_via_Multi_modal_Multi_turn_Chain_of_thoughts_Reasoning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Visual-O1: Understanding Ambiguous Instructions via Multi-modal Multi-turn Chain-of-thoughts Reasoning" introduces a framework that enhances the understanding of ambiguous instructions by simulating human-like reasoning processes. The framework is designed to work with both high-intelligent and general-intelligent models, providing instantial and empirical experiences, respectively. The paper includes several ablation studies to demonstrate the effectiveness of its components, such as reasoning and reflection, and response synthesis.

Upon reviewing the paper, the existing ablation studies focus on the effectiveness of the reasoning and reflection components, the impact of response synthesis, and the generalizability of the framework across different intelligence levels and tasks. However, there are a few areas where additional ablation studies could provide further insights into the framework's performance.

One potential area for a missing ablation study is the impact of the number of reasoning-reflection iterations (budget) on the model's performance. The paper mentions that the budget is set to 10 for high-intelligent models and 3 for general-intelligent models, but it does not explore how varying these budgets might affect the results. An ablation study could investigate whether increasing or decreasing the number of iterations leads to better or worse performance, particularly for general-intelligent models that might struggle with longer reasoning chains.

Another potential ablation study could focus on the role of visual context in the reasoning process. The framework relies on visual context to disambiguate instructions, but the paper does not explore what happens if this visual context is altered or removed. An ablation study could examine the impact of using different types of visual context or even removing it entirely to understand its contribution to the overall performance.

These additional ablation studies would help to further attribute the method's performance to its major components and provide a more comprehensive understanding of the framework's capabilities and limitations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Reasoning-Reflection Iterations
- **Ablated Part**: number of reasoning-reflection iterations (budget)
- **Action**: REPLACE
- **Replacement**: 
  - 5
  - 7
  - 10
  - 15
- **Metrics**: accuracy, BLEU-1

### Ablation Study on Visual Context
- **Ablated Part**: visual context used in reasoning process
- **Action**: REMOVE
- **Metrics**: accuracy, BLEU-1

</div>