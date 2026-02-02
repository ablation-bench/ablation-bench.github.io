<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/BiAssemble__Learning_Collaborative_Affordance_for_Bimanual_Geometric_Assembly

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "BiAssemble: Learning Collaborative Affordance for Bimanual Geometric Assembly" proposes a framework for robotic geometric assembly using learned point-level affordances aware of bimanual collaboration and long-horizon actions. The method consists of several key components: a Disassembly Predictor, a Transformation Predictor, and a BiAffordance Predictor, which guides the pick-up action considering subsequent alignment and assembly steps. The BiAffordance Predictor is designed with a conditional structure for bimanual coordination and trained with a signal reflecting the success of the entire long-horizon task.

The paper includes several ablation studies:
1.  `w/o SE(3)`: Replaces the SO(3)-equivariant encoder in the Disassembly Predictor with a standard PointNet++. This tests the importance of the specific network architecture for handling rotations.
2.  `w/ GT target`: Provides ground-truth disassembly direction and transformation, evaluating the impact of errors from the Disassembly and Transformation Predictors.
3.  `w/o Affordance Network`: Removes the learned Affordance Network during inference, using random sampling for grasp points. This highlights the importance of the affordance prediction itself.
4.  `w/o Transformation Predictor`: Removes the Transformation Predictor during inference, testing its role in determining alignment poses.
5.  `w/ heuristic disassembly direction v`: Replaces the learned Disassembly Predictor with a simple heuristic, assessing the value of learning this prediction.

While these ablations cover the individual prediction modules and the benefit of learning vs. heuristics/GT, they do not directly ablate two core claims of the BiAssemble method:
1.  **The specific mechanism for learning *bimanual collaboration* within the BiAffordance Predictor:** The paper describes a conditional structure (M2 conditioned on M1) and a training strategy where M2 guides M1. An ablation comparing this explicit collaborative learning approach to simply training two independent single-arm policies would demonstrate the benefit of their specific bimanual coordination design.
2.  **The *long-horizon awareness* incorporated into the BiAffordance training signal:** The paper states that the affordance is trained to be aware of subsequent alignment and assembly steps, distinguishing it from short-term affordance methods like DualAfford. An ablation comparing the current training signal (based on full assembly success) to a simpler, short-term signal (e.g., just successful grasping or short-term manipulation) would quantify the value of training for long-horizon success.

These two aspects are central to the paper's contribution (collaborative affordance for long-horizon assembly) and are not directly isolated in the current ablation studies. Therefore, I suggest adding ablation studies to investigate these specific design choices. The primary metric used throughout the paper is "Success Rate", which is appropriate for these ablations as well.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### w/o Bimanual Coordination
- **Ablated Part**: Explicit bimanual coordination learning mechanism (conditional prediction and M2-guides-M1 training) in the BiAffordance Predictor
- **Action**: REPLACE
- **Replacement**: 
  - Train two independent single-arm affordance/actor networks
- **Metrics**: Success Rate

### w/o Long-Horizon Affordance Training
- **Ablated Part**: Training signal for BiAffordance Predictor incorporating subsequent alignment/assembly feasibility
- **Action**: REPLACE
- **Replacement**: 
  - Train BiAffordance Predictor with a short-term success signal (e.g., successful grasp)
- **Metrics**: Success Rate

</div>