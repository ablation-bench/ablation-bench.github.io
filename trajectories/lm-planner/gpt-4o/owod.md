<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/owod

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Towards Open World Object Detection" introduces a novel problem setting called Open World Object Detection (OWOD), which involves identifying unknown objects and incrementally learning them without forgetting previously learned classes. The proposed solution, ORE, is based on contrastive clustering and energy-based unknown identification. To suggest ablation studies, we need to focus on the key components of the ORE method and evaluate their contributions to the overall performance.

1. **Contrastive Clustering**: This is a crucial component that helps in separating known and unknown classes in the latent space. An ablation study could involve removing this component to see how it affects the model's ability to identify unknowns and learn incrementally.

2. **Energy-Based Unknown Identification**: This component is responsible for distinguishing between known and unknown instances using energy values. Replacing this with a simpler threshold-based method could help understand its importance.

3. **Auto-labelling Unknowns with RPN**: The method uses RPN to pseudo-label unknown instances. An ablation study could involve removing this auto-labelling mechanism to evaluate its impact on the identification of unknowns.

4. **Exemplar Replay for Alleviating Forgetting**: The paper uses a simple exemplar replay strategy to mitigate forgetting. Replacing this with a more complex method like parameter regularization could provide insights into the effectiveness of the chosen strategy.

5. **Temperature Parameter in Energy Calculation**: The temperature parameter in the energy-based model affects the separation of known and unknown classes. An ablation study could involve testing different values for this parameter to find its optimal setting.

These ablation studies will help attribute the performance of the ORE method to its major components and provide insights into potential improvements.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Contrastive Clustering
- **Action**: REMOVE
- **Metrics**: mAP, unknown detection rate, incremental learning accuracy

### Ablation 2
- **Ablated Part**: Energy-Based Unknown Identification
- **Action**: REPLACE
- **Replacement**: 
  - threshold-based method
- **Metrics**: mAP, unknown detection rate

### Ablation 3
- **Ablated Part**: Auto-labelling Unknowns with RPN
- **Action**: REMOVE
- **Metrics**: mAP, unknown detection rate

### Ablation 4
- **Ablated Part**: Exemplar Replay for Alleviating Forgetting
- **Action**: REPLACE
- **Replacement**: 
  - parameter regularization
- **Metrics**: incremental learning accuracy, mAP

### Ablation 5
- **Ablated Part**: Temperature Parameter in Energy Calculation
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: mAP, unknown detection rate

</div>