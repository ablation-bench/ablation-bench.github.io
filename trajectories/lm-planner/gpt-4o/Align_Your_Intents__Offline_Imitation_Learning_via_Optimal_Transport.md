<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Align_Your_Intents__Offline_Imitation_Learning_via_Optimal_Transport

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Align Your Intents: Offline Imitation Learning via Optimal Transport" introduces AILOT, a method that leverages optimal transport to align the intents of an agent with those of an expert in a latent space. The method is designed to work without explicit rewards or action labels, using intrinsic rewards derived from optimal transport distances. The paper includes an ablation study on the number of expert trajectories, but it lacks ablations on other critical components of the method.

One potential missing ablation is the impact of the cost function used in the optimal transport computation. The paper uses a specific cost function that incorporates the intents of states, but it does not explore how different cost functions might affect performance. Testing alternative cost functions could provide insights into the robustness and sensitivity of the method to this choice.

Another missing ablation is the role of the isometric transformation used to map states to the intent space. The paper emphasizes the importance of this transformation for preserving temporal structure, but it does not investigate what happens if this transformation is altered or removed. Exploring this could help understand the necessity and impact of the isometric mapping on the overall performance of AILOT.

These ablations are crucial because they address fundamental components of the method that could significantly influence its effectiveness. By understanding the role of the cost function and the isometric transformation, the researchers can better attribute the success of AILOT to its core innovations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Cost Function
- **Ablated Part**: Cost function used in optimal transport computation
- **Action**: REPLACE
- **Replacement**: 
  - Euclidean distance
  - Cosine distance
  - Manhattan distance
- **Metrics**: Normalized score, Cumulative return

### Ablation on Isometric Transformation
- **Ablated Part**: Isometric transformation to intent space
- **Action**: REMOVE
- **Metrics**: Normalized score, Cumulative return

</div>