<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Memory_Proxy_Maps_for_Visual_Navigation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Memory Proxy Maps for Visual Navigation" introduces a novel approach to visual navigation using a three-tiered feudal learning framework. The key components of this method include the Memory Proxy Map (MPM), the Waypoint Network (WayNet), and a low-level worker agent. The MPM serves as a memory proxy, learned in a self-supervised manner, while WayNet outputs intermediate subgoals for navigation. The low-level worker agent is responsible for obstacle avoidance and movement towards waypoints.

The existing ablation studies in the paper focus on the effectiveness of different network architectures for the MPM and the impact of the hierarchical structure on navigation performance. However, there are some missing ablation studies that could provide further insights into the method's components.

One missing ablation study could involve the replacement of the self-supervised learning method used for the MPM. The paper uses Synchronous Momentum Grouping (SMoG) for learning the latent space. An ablation study could explore the impact of using different self-supervised learning methods, such as MoCo or SwAV, on the performance of the MPM and overall navigation.

Another potential ablation study could investigate the impact of the waypoint selection strategy in WayNet. The current method uses human point-click navigation trajectories for training. An ablation study could explore the effect of using alternative strategies, such as random waypoint selection or a heuristic-based approach, on navigation performance.

These ablation studies would help to attribute the method's performance to its major components and provide a deeper understanding of the design choices made in the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on Self-Supervised Learning Method
- **Ablated Part**: Self-supervised learning method for Memory Proxy Map (MPM)
- **Action**: REPLACE
- **Replacement**: 
  - MoCo
  - SwAV
- **Metrics**: Success Rate, SPL

### Ablation Study on Waypoint Selection Strategy
- **Ablated Part**: Waypoint selection strategy in WayNet
- **Action**: REPLACE
- **Replacement**: 
  - Random waypoint selection
  - Heuristic-based approach
- **Metrics**: Success Rate, SPL

</div>