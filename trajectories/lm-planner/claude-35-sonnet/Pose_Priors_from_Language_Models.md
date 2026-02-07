<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Pose_Priors_from_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents ProsePose, a method that uses LMMs to generate contact constraints for 3D pose estimation. The key components of the method are:

1. Using GPT4-V as the LMM to generate contact constraints from images
2. Converting natural language constraints into loss functions
3. Aggregating multiple samples from the LMM to handle hallucination
4. Using coarse-grained body regions instead of fine-grained ones

The paper already includes some ablations:
- Ablation of different loss components (Table 3)
- Impact of number of LMM samples (Figure 5)
- Using a different LMM (LLaVA) instead of GPT4-V (Section 7.4)

However, there are two important missing ablations that could provide valuable insights:

1. The impact of using coarse vs fine-grained body regions - this is a key design choice that affects how well the LMM can understand and describe contacts. The paper mentions this choice but doesn't evaluate its impact.

2. The effect of different prompting strategies - while the paper shows the final prompts used, it doesn't evaluate how different prompt designs affect the quality of the generated constraints. This is especially important since prompt engineering is crucial for LMM performance.

These ablations would help understand the robustness and generalizability of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Granularity Ablation
- **Ablated Part**: coarse-grained body region definitions
- **Action**: REPLACE
- **Replacement**: 
  - fine-grained regions (75 regions from Fieraru et al. 2020)
  - medium-grained regions (30-40 regions)
- **Metrics**: PA-MPJPE, PCC

### Prompt Design Ablation
- **Ablated Part**: LMM prompt template
- **Action**: REPLACE
- **Replacement**: 
  - zero-shot prompt without reasoning
  - few-shot prompt with examples
  - prompt without explicit region list
- **Metrics**: PA-MPJPE, PCC

</div>