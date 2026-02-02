<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Object_Centric_Pretraining_via_Target_Encoder_Bootstrapping

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Object-Centric Pretraining via Target Encoder Bootstrapping" introduces OCEBO, a novel method for training object-centric models from scratch using a self-distillation setup. The method leverages an exponential moving average (EMA) update of the target encoder to incorporate object-centric inductive biases, addressing the limitations of frozen target encoders. The paper includes several ablation studies, such as the impact of cross-view patch filtering and the object-centric training objective. However, there are potential areas for further investigation.

One missing ablation study could focus on the impact of the EMA update rate on the target encoder. The EMA update rate is crucial as it determines how quickly the target encoder adapts to the object-centric model's encoder. Testing different EMA rates could provide insights into the balance between stability and adaptability of the target encoder.

Another potential ablation study could explore the effect of different initialization strategies for the target encoder. The paper mentions the random initialization of the target encoder, which can lead to slot collapse. Investigating alternative initialization methods, such as using a small pre-trained object-centric model or a different random seed, could help understand their impact on the model's performance and stability.

These ablations would provide a deeper understanding of the components that contribute to the success of OCEBO and could lead to further improvements in object-centric pretraining methods.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: EMA Update Rate
- **Ablated Part**: EMA update rate of the target encoder
- **Action**: REPLACE
- **Replacement**: 
  - 0.9
  - 0.95
  - 0.99
  - 0.999
- **Metrics**: FG-ARI, mBO

### Ablation 2: Target Encoder Initialization
- **Ablated Part**: Initialization strategy of the target encoder
- **Action**: REPLACE
- **Replacement**: 
  - small pre-trained object-centric model
  - different random seed
- **Metrics**: FG-ARI, mBO

</div>