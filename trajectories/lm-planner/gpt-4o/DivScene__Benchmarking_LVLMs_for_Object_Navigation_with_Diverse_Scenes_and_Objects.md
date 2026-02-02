<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/DivScene__Benchmarking_LVLMs_for_Object_Navigation_with_Diverse_Scenes_and_Objects

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "DivScene: Benchmarking LVLMs for Object Navigation with Diverse Scenes and Objects" introduces a novel dataset and an end-to-end embodied agent, NatVLM, for object navigation tasks. The paper includes several ablation studies focusing on the efficacy of CoT explanation traces and different methods of position comparisons. However, there are some potential areas for further ablation studies that could provide additional insights into the model's performance.

1. **Ablation of the BFS-based Planner**: The current approach uses a BFS-based planner to generate shortest-path trajectories for imitation learning. An ablation study could investigate the impact of using different path planning algorithms or heuristics on the agent's performance. This would help understand the dependency of the model on the specific path planning strategy used during training.

2. **Ablation of the Number of Scene Types**: The dataset includes 81 different scene types. An ablation study could explore the impact of reducing the number of scene types on the model's generalization ability. This would help determine the importance of scene diversity in training robust navigation agents.

These ablation studies are not explicitly covered in the paper and could provide valuable insights into the robustness and adaptability of the proposed method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of BFS-based Planner
- **Ablated Part**: BFS-based planner used for generating shortest-path trajectories
- **Action**: REPLACE
- **Replacement**: 
  - A* algorithm
  - Dijkstra's algorithm
  - Random walk
- **Metrics**: Success Rate (SR), Success weighted by Path Length (SPL), Success weighted by Episode Length (SEL)

### Ablation of Number of Scene Types
- **Ablated Part**: Number of scene types in the DIVSCENE dataset
- **Action**: REPLACE
- **Replacement**: 
  - 40 scene types
  - 60 scene types
- **Metrics**: Success Rate (SR), Success weighted by Path Length (SPL), Success weighted by Episode Length (SEL)

</div>