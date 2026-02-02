<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Memory_Proxy_Maps_for_Visual_Navigation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Memory Proxy Maps for Visual Navigation" introduces FeudalNav, a three-tiered hierarchical agent for visual navigation without relying on RL, graphs, odometry, or metric maps. The key components are the High-Level Manager (HLM) using a self-supervised Memory Proxy Map (MPM), the Mid-Level Manager (WayNet) trained via supervised learning on human point-click data to predict waypoints, and the Low-Level Worker trained as a classifier to execute actions towards the waypoint while avoiding obstacles. The agent also uses Superglue for goal image matching, which influences both the mid-level guidance and the stop condition.

The paper includes two main ablation studies in Section 6:
1.  **Different Network's Effects on the Memory Proxy Map:** This study compares different self-supervised feature extractors (SMoG, Moco, Resnet, Swav) to justify the choice of SMoG for learning the latent space used in the MPM, showing that SMoG features best preserve relative geometric distances between observations.
2.  **Full Hierarchy's Effect on Image-Goal Task Performance:** This comprehensive study evaluates the impact of different components and inputs on the final navigation performance (Success Rate and SPL). It ablates the presence and type of the MPM, different inputs to WayNet (RGB, RGBD, historical observations, with/without MPM), and the type of Low-Level Worker (deterministic vs. classifier).

While the existing ablations effectively demonstrate the value of the MPM (especially the Gaussian heatmap version) and the learned classifier worker, they do not fully isolate the contribution of two other key aspects:
1.  **The learned waypoint prediction policy of WayNet:** The current ablations show that using WayNet with certain inputs (like RGBD-M) is effective, but they don't compare the performance of this *learned policy* against a simpler, non-learned mid-level guidance strategy that could potentially use the same available information (like depth, goal image matches, or MPM density). Ablating WayNet's learned policy and replacing it with a heuristic would clarify the benefit of training WayNet on human data.
2.  **The Superglue-based goal guidance switching:** The method uses Superglue to match the current observation to the goal image and switches the mid-level target from the WayNet waypoint to the average goal keypoint location if the match confidence is high. This specific mechanism for integrating goal information into the guidance is not explicitly ablated. An ablation removing this switching logic (forcing the agent to always rely on WayNet for guidance, even when the goal is visible) would show the importance of this goal-directed override.

Based on this analysis, the two most important missing ablations are the evaluation of the learned WayNet policy against a heuristic alternative and the evaluation of the Superglue-based goal guidance switching mechanism. These experiments would provide deeper insight into the specific contributions of the learned mid-level strategy and the goal integration method to the overall SOTA performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### WayNet Learned Policy Ablation
- **Ablated Part**: Learned waypoint prediction policy of the Mid-Level Manager (WayNet)
- **Action**: REPLACE
- **Replacement**: 
  - Heuristic guidance (e.g., Superglue goal match if visible, otherwise simple exploration)
- **Metrics**: Succ↑, SPL↑

### Superglue Goal Guidance Ablation
- **Ablated Part**: Switching mechanism between WayNet prediction and Superglue goal match for guidance
- **Action**: REMOVE
- **Metrics**: Succ↑, SPL↑

</div>