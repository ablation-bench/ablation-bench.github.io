<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/BiAssemble__Learning_Collaborative_Affordance_for_Bimanual_Geometric_Assembly

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents BiAssemble, a framework for bimanual geometric assembly that consists of three main components:

1. Disassembly Predictor - Predicts feasible disassembly directions based on fracture geometry
2. Transformation Predictor - Predicts alignment poses for manipulation
3. BiAffordance Predictor - Predicts collaborative affordance and gripper actions

The paper includes several ablation studies:
- w/o SE(3) - Replaces SO(3)-equivariant encoder with PointNet++
- w/ GT Target - Uses ground truth disassembly direction and transformation
- w/o Affordance Network - Random contact point sampling instead of affordance prediction
- w/o Transformation Predictor - Removes transformation prediction component
- w/ heuristic disassembly direction - Uses heuristic instead of learned disassembly prediction

However, there are two important missing ablations that could provide additional insights:

1. The BiAffordance Predictor uses a conditional training strategy where M2 is trained first and then used to train M1. An ablation studying joint vs conditional training would help validate this design choice.

2. The framework uses a three-step decomposition (pick-up, alignment, assembly). An ablation comparing this to an end-to-end approach would help justify the decomposed pipeline.

These ablations would help better understand key architectural choices in the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Joint vs Conditional Training
- **Ablated Part**: Conditional training strategy of BiAffordance Predictor where M2 trains first then guides M1
- **Action**: REPLACE
- **Replacement**: 
  - Joint training of M1 and M2 simultaneously
- **Metrics**: Success rate on novel instances, Success rate on unseen categories

### Pipeline Decomposition
- **Ablated Part**: Three-step decomposition into pick-up, alignment and assembly
- **Action**: REPLACE
- **Replacement**: 
  - End-to-end prediction of full manipulation sequence
- **Metrics**: Success rate on novel instances, Success rate on unseen categories

</div>