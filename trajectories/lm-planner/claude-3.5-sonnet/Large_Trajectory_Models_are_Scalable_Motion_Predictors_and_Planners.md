<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Large_Trajectory_Models_are_Scalable_Motion_Predictors_and_Planners

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Let me analyze the paper's existing ablation studies and suggest important missing ones:

1. From Table 3 in the paper, the existing ablations focus on:
- Testing STR with and without Key Points (CS vs CKS)
- Testing forward vs backward generation of Key Points
- Testing MLP vs Diffusion decoders for Key Points

2. The paper's main contributions revolve around:
- The sequence modeling formulation for motion prediction/planning
- The scalability of the model (model size and dataset size)
- The use of Key Points and Proposals for better trajectory generation

3. Looking at missing important ablations, I notice:
1) The paper doesn't ablate the impact of different sequence arrangements, which is crucial since this is one of their main claims.
2) While they test different model sizes, they don't ablate the impact of different transformer architectures, which could validate their choice of GPT-2.

I'll suggest these two ablations, ranked by importance:
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sequence Arrangement Ablation
- **Ablated Part**: The order and grouping of elements in the input sequence (Context, Proposal, Key Points, Future States)
- **Action**: REPLACE
- **Replacement**: 
  - Context->KeyPoints->Proposal->Future
  - Proposal->Context->KeyPoints->Future
  - Future->Context->Proposal->KeyPoints
- **Metrics**: 8sADE, 3sFDE, 5sFDE, 8sFDE, MR, OLS

### Transformer Architecture Ablation
- **Ablated Part**: The GPT-2 transformer backbone
- **Action**: REPLACE
- **Replacement**: 
  - BERT
  - T5
  - PaLM
- **Metrics**: 8sADE, 3sFDE, 5sFDE, 8sFDE, MR, OLS

</div>