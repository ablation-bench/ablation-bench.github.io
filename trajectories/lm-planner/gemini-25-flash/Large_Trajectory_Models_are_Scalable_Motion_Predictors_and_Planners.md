<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Large_Trajectory_Models_are_Scalable_Motion_Predictors_and_Planners

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants me to identify up to two important missing ablation studies for the paper "Large Trajectory Models are Scalable Motion Predictors and Planners".

I have analyzed the paper, focusing on the proposed State Transformer (STR) method and the existing ablation study presented in Section 5.5.

The STR method formulates motion prediction and planning as a sequence modeling task, arranging Context, optional Proposal, optional Key Points, and Future States. It uses a causal Transformer backbone.
- Context includes map, past trajectories, traffic lights, and past ego states.
- Proposals are used for classifying future intentions/modalities.
- Key Points are specific future trajectory points used as anchors for long-term reasoning.
- Future States are the final predicted trajectories.

The paper evaluates STR on two tasks: motion planning (NuPlan) and motion prediction (WOMD).
- For NuPlan (planning), they use STR(CKS), including Context, Key Points, and States.
- For WOMD (prediction), they use STR(CPS), including Context, Proposals, and States.

The existing ablation study (Section 5.5) focuses *only* on the planning task (NuPlan) and investigates:
1.  The impact of adding Key Points (`STR(CS)` vs `STR(CKS)`).
2.  The order of Key Points generation (forward vs backward).
3.  The type of decoder for Key Points (MLP vs Diffusion).

Based on this analysis, two important components of the STR sequence formulation are the Proposal and Key Point components. The existing ablation only explores Key Points for the planning task.

Therefore, crucial missing ablations are:
1.  **Ablating the Proposal component:** The paper uses Proposals for the prediction task (WOMD) to handle multimodality but does not show an ablation demonstrating its contribution. Comparing the performance of STR(CPS) (with Proposals) against a version without Proposals (STR(CS)) on the WOMD dataset would clarify the necessity and impact of this component.
2.  **Adding Key Points to the Prediction task:** Key Points are shown to be beneficial for the planning task, which involves long-term reasoning. The prediction task also involves predicting trajectories up to 8 seconds. Evaluating whether adding Key Points to the prediction model (STR(CPS)) improves performance (creating STR(CPKS)) would show if the benefit of Key Points generalizes to the prediction task.

These two ablations directly address the contribution of the intermediate sequence components (Proposals and Key Points) in the context of the tasks where their impact hasn't been fully evaluated or where they weren't originally included.

I will prioritize these two as they are central to the STR sequence design and their impact is not fully understood from the current experiments. I will use the metrics reported for the respective tasks in the paper.

For Ablation 1 (Removing Proposals for WOMD), the action is REMOVE.
For Ablation 2 (Adding Key Points for WOMD), the action is ADD, and the replacement specifies adding the Key Points component with a suitable configuration (e.g., backward order, diffusion decoder, similar to the successful planning ablation).

The metrics for WOMD are mAP, minADE, minFDE, and MR.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Proposal Component (WOMD)
- **Ablated Part**: The Proposal component in the STR sequence for the motion prediction task.
- **Action**: REMOVE
- **Metrics**: mAP, minADE, minFDE, MR

### Adding Key Points to Prediction (WOMD)
- **Ablated Part**: The Key Points component in the STR sequence for the motion prediction task.
- **Action**: ADD
- **Replacement**: 
  - Add Key Points (e.g., 5 points at 8s, 4s, 2s, 1s, 0.5s, backward order) with a Diffusion decoder.
- **Metrics**: mAP, minADE, minFDE, MR

</div>