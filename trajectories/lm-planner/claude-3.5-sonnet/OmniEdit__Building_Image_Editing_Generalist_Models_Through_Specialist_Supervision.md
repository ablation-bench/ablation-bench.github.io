<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/OmniEdit__Building_Image_Editing_Generalist_Models_Through_Specialist_Supervision

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while the authors conducted several ablation studies focusing on the importance sampling and EditNet architecture, there are still some critical components that weren't thoroughly investigated. Let me explain my reasoning for suggesting two important missing ablation studies:

1. Specialist Model Selection Impact:
- The paper uses 7 different specialist models for different editing tasks but doesn't investigate how the choice and number of specialists affect the final performance
- This is crucial since the specialist supervision is a core contribution of the paper
- No ablation was done to understand if all specialists are equally important or if some could be removed without significant performance degradation

2. GPT-4o vs InternVL2 Scoring:
- The authors mention using GPT-4o for initial scoring and then distilling to InternVL2 for efficiency
- However, there's no ablation study comparing the quality difference between using GPT-4o directly versus the distilled InternVL2
- This is important since the quality control through importance sampling is another major contribution

The paper uses several metrics for evaluation including Perceptual Quality (PQ), Semantic Consistency (SC), and Overall Score (O), which I'll include in the suggested ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Specialist Impact Study
- **Ablated Part**: number and combination of specialist models used for supervision
- **Action**: REPLACE
- **Replacement**: 
  - using all 7 specialists
  - using top-4 specialists
  - using top-2 specialists
- **Metrics**: PQ, SC, O

### Scoring Model Comparison
- **Ablated Part**: importance scoring model
- **Action**: REPLACE
- **Replacement**: 
  - GPT-4o direct scoring
  - distilled InternVL2
  - CLIP score baseline
- **Metrics**: PQ, SC, O

</div>