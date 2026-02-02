<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/CABINET__Content_Relevance_based_Noise_Reduction_for_Table_Question_Answering

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two high‐priority ablation studies that have not been explored in the paper yet. First, while CABINET’s Unsupervised Relevance Scorer (URS) is trained end‐to‐end together with the QA LLM via a differentiable (joint) training scheme, it remains unclear how much benefit arises from this joint training as compared to using a fixed URS. In other words, if the URS is pre-trained separately and then frozen instead of receiving gradients from the QA loss, the system’s performance may drop. Evaluating this configuration will better isolate the contribution of the joint training approach and its indirect supervision signal via answer generation loss. Second, the framework leverages a weakly supervised Parsing Statement Generator (PSG) that is trained using only around 300 manually annotated parsing statements. However, the sensitivity of CABINET’s performance to the amount of annotated supervision has not been studied. Ablating the number of supervision samples—from no supervision to lower counts (e.g., 50 or 150 examples) versus the current 300—can provide valuable insight into the importance of the weak supervision used in identifying relevant cells. Both ablations are critical in understanding the dependency of CABINET’s overall performance on its major components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Impact of Joint Training for URS
- **Ablated Part**: Differentiable coupling between the Unsupervised Relevance Scorer (URS) and the QA LLM
- **Action**: REPLACE
- **Replacement**: 
  - Joint Training (default)
  - Fixed URS with pre-trained weights (non-differentiable)
- **Metrics**: Exact-Match Accuracy, S-BLEU

### Ablation 2: Effect of Supervision Size for Parsing Statement Generator
- **Ablated Part**: Amount of annotated parsing statements used to train the weakly supervised Parsing Statement Generator in the cell predictor
- **Action**: REPLACE
- **Replacement**: 
  - 0 samples (no supervision)
  - 50 samples
  - 150 samples
  - 300 samples (default)
- **Metrics**: Exact-Match Accuracy, S-BLEU

</div>