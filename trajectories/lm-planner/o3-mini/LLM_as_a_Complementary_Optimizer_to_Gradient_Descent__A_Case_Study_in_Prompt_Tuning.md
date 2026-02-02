<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/LLM_as_a_Complementary_Optimizer_to_Gradient_Descent__A_Case_Study_in_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already provides ablations on key parameters such as the number of alternating rounds, iterations before LLM intervention, the distance function for token space projection, and prompt length. However, two important aspects have not been ablated. First, the method relies on selecting candidate prompts from the gradient-based optimization trajectory to feed into the LLM. The paper uses a Top-K strategy, but it is unclear how robust this method is compared to alternatives such as random sampling or a diversity-promoted sampling approach. Investigating different candidate sampling strategies would shed light on the contribution of the selection mechanism to the overall performance. Second, the current framework fully reinitializes the prompt parameters using the LLM-generated outputs after each round. This complete replacement may affect convergence stability and the balance between exploration and exploitation. An ablation that compares full replacement against alternative reinitialization strategies—such as interpolating the LLM-generated prompt with the current parameters or adding a perturbative update—could provide deeper insights into the role of the reinitialization mechanism. Both studies should report metrics such as accuracy, loss, and variance/stability across multiple random seeds.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Candidate Sampling Strategy Ablation
- **Ablated Part**: The candidate selection mechanism that extracts prompt candidates from the gradient-based optimization trajectory for LLM-based refinement
- **Action**: REPLACE
- **Replacement**: 
  - Top-K selection (baseline)
  - Random sampling
  - Diversity-promoted sampling
- **Metrics**: accuracy, loss, std of performance

### Reinitialization Strategy Ablation
- **Ablated Part**: The reinitialization method for prompt parameters using LLM-generated outputs
- **Action**: REPLACE
- **Replacement**: 
  - Full replacement (baseline)
  - Interpolation between LLM output and current parameters
  - Perturbative update (LLM suggestion + noise)
- **Metrics**: accuracy, loss, convergence stability

</div>