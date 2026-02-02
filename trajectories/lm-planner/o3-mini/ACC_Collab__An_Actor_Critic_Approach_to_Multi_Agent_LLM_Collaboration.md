<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/ACC_Collab__An_Actor_Critic_Approach_to_Multi_Agent_LLM_Collaboration

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first key component in ACC-Collab is the guided‐collaboration mechanism. This mechanism actively generates off-policy trajectories by guiding the agents toward and away from the ground truth answer using tailored prompts. Although the paper shows that guided responses provide high-quality pairwise data, there is no explicit ablation study that investigates the effect of removing these guided trajectories from the training process. Removing this component would help understand the benefits provided by the guided-collaboration module on both the actor’s final answer accuracy as well as the overall deliberation process.

Another central component is the computation of partial trajectory rewards. The method relies on an one‐step rollout heuristic to estimate intermediate rewards for each round, which is then used to drive the training process. However, the paper does not include an ablation study that assesses the impact of instead using only the final round reward (or trying alternative reward estimation strategies such as multi-step rollouts). Ablating or replacing the partial trajectory reward computation could reveal its contribution to guiding the iterative updates of both actor and critic.

Thus, the two most important missing ablation studies are: (1) a study where the guided-collaboration mechanism is removed (so that only natural deliberation trajectories are used for training), and (2) a study that replaces the partial trajectory reward computation with alternative strategies (e.g., using only the final round reward or a multi-step rollout approach).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Guided-Collaboration Module Removal
- **Ablated Part**: Guided-collaboration trajectory generation mechanism including guided deliberation rounds and Δy/Δ!y based selection
- **Action**: REMOVE
- **Metrics**: final answer accuracy, process accuracy, per-round accuracy improvement

### Ablation: Partial Trajectory Reward Signal
- **Ablated Part**: Intermediate reward estimation (partial trajectory rewards) used at each deliberation round
- **Action**: REPLACE
- **Replacement**: 
  - final-round reward only
  - multi-step rollout reward estimation
- **Metrics**: final answer accuracy, process accuracy, per-round performance improvement

</div>