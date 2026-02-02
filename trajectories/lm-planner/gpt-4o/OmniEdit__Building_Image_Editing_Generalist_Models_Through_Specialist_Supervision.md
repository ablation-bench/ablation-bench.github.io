<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/OmniEdit__Building_Image_Editing_Generalist_Models_Through_Specialist_Supervision

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "OmniEdit: Building Image Editing Generalist Models Through Specialist Supervision" introduces several key innovations to improve instruction-guided image editing. The main contributions include the use of specialist models for supervision, importance sampling with large multimodal models, a novel EditNet architecture, and support for various aspect ratios. The existing ablation studies in the paper focus on the importance of sampling and the architectural design of EditNet.

To suggest missing ablation studies, we need to consider other critical components of the method that have not been thoroughly analyzed. One potential area is the use of specialist models for supervision. The paper claims that using multiple specialist models improves task coverage, but it does not provide an ablation study to quantify the impact of this choice. Another area is the importance sampling mechanism, specifically the choice of using large multimodal models like GPT-4o for scoring. While the paper discusses the effectiveness of this approach, it does not explore alternative scoring mechanisms or the impact of different threshold values for filtering data.

Therefore, I suggest two missing ablation studies: one focusing on the impact of using multiple specialist models versus a single specialist model, and another examining the effect of different scoring mechanisms and threshold values in the importance sampling process.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Specialist Model Supervision Ablation
- **Ablated Part**: use of multiple specialist models for supervision
- **Action**: REPLACE
- **Replacement**: 
  - single specialist model
  - randomly selected specialist models
- **Metrics**: VIEScore (GPT4o), VIEScore (Gemini), Human Evaluation (SCavg, PQavg, Oavg, Accavg)

### Importance Sampling Scoring Mechanism Ablation
- **Ablated Part**: use of GPT-4o for scoring in importance sampling
- **Action**: REPLACE
- **Replacement**: 
  - CLIP-score
  - DINO-score
  - lower threshold values (e.g., 7, 8)
- **Metrics**: VIEScore (GPT4o), VIEScore (Gemini), Human Evaluation (SCavg, PQavg, Oavg, Accavg)

</div>