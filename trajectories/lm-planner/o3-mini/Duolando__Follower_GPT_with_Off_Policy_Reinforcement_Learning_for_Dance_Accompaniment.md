<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Duolando__Follower_GPT_with_Off_Policy_Reinforcement_Learning_for_Dance_Accompaniment

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that focus on core design choices of Duolando. The first study investigates the impact of the human‐defined reward function used in the off‐policy reinforcement learning stage – in particular, the penalty weight (η) applied in the lower body synchronization reward (Equation 6) that regulates the alignment between the predicted global translation and the lower body motion. Despite its central role in reducing skating artifacts, the paper fixes η at 100 without showing how sensitive the performance is to alternative scales. Testing a range (for example, 50, 100, and 150) will help quantify its effect on metrics such as kinematic quality (FIDk), interactive alignment (FIDcd, contact frequency CF), and the newly defined skating ratio (SR).

The second study targets the discrete representation aspect provided by the VQ-VAE modules. Duolando relies on tokenized motion representations obtained with a fixed codebook capacity (set to 512). However, the choice of codebook size has a direct impact on the granularity of motion representations, affecting both the reconstruction quality (and hence the FIDk and FIDg scores) and the diversity of the generated motions (Divk, Divg) as well as the coordination quality (FIDcd, Divcd). Exploring alternative codebook capacities (e.g., 256, 512, and 1024) will provide insight into how finely the motion space must be discretized to balance fidelity and diversity.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Reward Weight Sensitivity in Off-Policy RL
- **Ablated Part**: The human-defined reward function for lower body synchronization in the off-policy reinforcement learning stage (specifically the penalty weight η in Equation 6)
- **Action**: REPLACE
- **Replacement**: 
  - 50
  - 100
  - 150
- **Metrics**: FIDk, FIDcd, CF, Skating Ratio (SR), BED

### Ablation: VQ-VAE Codebook Capacity
- **Ablated Part**: The codebook capacity used for quantizing motion and relative translation representations in the VQ-VAE modules
- **Action**: REPLACE
- **Replacement**: 
  - 256
  - 512
  - 1024
- **Metrics**: FIDk, FIDg, Divk, Divg, FIDcd, Divcd

</div>