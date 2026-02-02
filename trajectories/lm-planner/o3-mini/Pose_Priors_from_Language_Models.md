<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Pose_Priors_from_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The proposed missing ablation studies focus on two crucial components that are central to the method but not explicitly evaluated in the paper. The first ablation targets the chain-of-thought prompting used with the LMM when generating contact constraints. Although the method leverages a chain-of-thought process to improve the clarity and consistency of the structured output, the paper does not compare this strategy against a direct prompt without such reasoning. This ablation would replace the chain-of-thought prompt with a direct constraint-generation prompt and measure how the difference affects the joint PA-MPJPE and Average PCC metrics.

The second ablation addresses the chirality disambiguation mechanism. In the paper, when the LMM outputs ambiguous references (e.g., omitting left/right indicators), the system enforces constraints on both symmetric limbs by taking the minimum loss across both possibilities. However, failure cases indicate that this approach may sometimes lead to incorrect or suboptimal contact placements. By removing or altering this disambiguation step (for example, not replicating ambiguous constraints and using a default or oracle-based assignment), we can assess how crucial this strategy is for accurate pose estimation. The metrics for both ablations would be the same as those used in the paper—joint PA-MPJPE and Average PCC—to ensure consistency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Chain-of-Thought Ablation
- **Ablated Part**: The chain-of-thought reasoning in the LMM prompt used to generate structured contact constraints
- **Action**: REPLACE
- **Replacement**: 
  - Direct prompt without chain-of-thought
  - Prompt with chain-of-thought (baseline)
- **Metrics**: joint PA-MPJPE, Average PCC

### Chirality Handling Ablation
- **Ablated Part**: The chirality disambiguation mechanism that replicates ambiguous constraints to cover symmetric body parts
- **Action**: REPLACE
- **Replacement**: 
  - No replication for ambiguous (left/right) cues
  - Current minimum loss across both sides (baseline)
- **Metrics**: joint PA-MPJPE, Average PCC

</div>