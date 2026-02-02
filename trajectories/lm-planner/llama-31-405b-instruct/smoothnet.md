<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/smoothnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

To design ablation studies for the SmoothNet paper, we need to identify the key components of the method and analyze their impact on the overall performance. The SmoothNet is a plug-and-play network for refining human poses in videos, which uses a temporal-only refinement approach to mitigate jitters. 

One potential ablation study is to analyze the effect of the motion-aware fully-connected network on the overall performance. This can be done by comparing the results of the basic SmoothNet with the motion-aware SmoothNet. 

Another potential ablation study is to investigate the impact of the long-range temporal receptive fields on the performance of the SmoothNet. This can be done by varying the length of the input sequence and analyzing the effect on the results.

Additionally, we can also analyze the effect of the loss function on the performance of the SmoothNet. This can be done by comparing the results of the SmoothNet trained with different loss functions, such as the mean per joint position error (MPJPE) and the mean per joint acceleration error (Accel).

Finally, we can also investigate the transferability of the SmoothNet across different datasets and estimators. This can be done by training the SmoothNet on one dataset and testing it on another dataset, or by using different estimators as input to the SmoothNet.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: motion-aware fully-connected network
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

### Ablation B
- **Ablated Part**: long-range temporal receptive fields
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 20
  - 30
  - 40
  - 50
- **Metrics**: MPJPE, Accel

### Ablation C
- **Ablated Part**: loss function
- **Action**: REPLACE
- **Replacement**: 
  - MPJPE
  - Accel
  - MPJPE+Accel
- **Metrics**: MPJPE, Accel

### Ablation D
- **Ablated Part**: transferability
- **Action**: REPLACE
- **Replacement**: 
  - Human3.6M
  - MPI-INF-3DHP
  - AIST
- **Metrics**: MPJPE, Accel

### Ablation E
- **Ablated Part**: estimator
- **Action**: REPLACE
- **Replacement**: 
  - RLE
  - VIBE
  - SPIN
- **Metrics**: MPJPE, Accel

</div>