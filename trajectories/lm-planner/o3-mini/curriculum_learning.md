<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/curriculum_learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Below is our proposed list of five ablation studies ranked by their importance. The most critical experiment is to eliminate the curriculum learning mechanism entirely (i.e. revert to random data ordering) to gauge the overall benefit of curriculum-based training. Next, we investigate the adaptive component by removing the curriculum updates so that only a fixed ranking is used. Third, we assess the role of pacing by removing the pacing function, which gradually introduces harder samples, to examine if pacing is responsible for any observed improvements. Fourth, we replace the teacher’s difficulty scoring with alternative (non-teacher) ranking methods (e.g. random ranking or heuristic based on sample length) to check whether the backbone signals from the teacher are essential. Finally, we ablate the order direction by comparing an easy-to-difficult ordering with the reversed order (difficult-to-easy) to understand the effect of curriculum order on generalization. These studies target the major design components of the method while ensuring minimal changes to isolate each factor’s contribution.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Curriculum Learning Baseline
- **Ablated Part**: The entire curriculum ordering mechanism (ranking and pacing functions)
- **Action**: REMOVE
- **Metrics**: accuracy, in_domain_generalization, ood_generalization

### Fixed Curriculum Learning
- **Ablated Part**: Adaptive curriculum update mechanism (dynamic re-ranking based on learner state)
- **Action**: REMOVE
- **Metrics**: accuracy, overfitting, generalization

### No Pacing Function
- **Ablated Part**: Pacing function that gradually introduces more difficult samples
- **Action**: REMOVE
- **Metrics**: accuracy, convergence_speed, overfitting

### Alternative Difficulty Ranking
- **Ablated Part**: Teacher model based scoring (QAP, variability, energy) for determining sample difficulty
- **Action**: REPLACE
- **Replacement**: 
  - Random ranking
  - Heuristic ranking based on sample length
- **Metrics**: accuracy, in_domain_generalization, ood_generalization

### Reverse Curriculum Order
- **Ablated Part**: Direction of curriculum ordering (easy-to-difficult vs. difficult-to-easy)
- **Action**: REPLACE
- **Replacement**: 
  - Easy-to-difficult order
  - Difficult-to-easy order
- **Metrics**: accuracy, generalization, convergence

</div>