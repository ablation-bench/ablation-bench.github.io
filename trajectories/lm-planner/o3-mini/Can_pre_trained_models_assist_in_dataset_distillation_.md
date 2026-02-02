<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Can_pre_trained_models_assist_in_dataset_distillation_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One important component of the paper is the loss term used for PTM supervision – the CLoM loss – which is currently defined using the cross-entropy loss. However, the ablation studies do not include any investigation into whether alternative loss formulations (such as KL divergence, mean squared error on logits, or even cosine distance on logits/features) might yield different or improved performance. Understanding how robust the synthetic dataset generation is to the choice of loss formulation could offer insights into the sensitivity of the approach and lead to further improvements.

A second potential missing ablation is the strategy for aggregating guidance when using multiple pre-trained models. In the current work, when multiple PTMs (obtained via diverse initializations or architectures) are available, the synthetic dataset is updated by using one randomly chosen PTM at each iteration. It would be informative to study the effect of instead aggregating the guidance—for example, by averaging losses computed from all PTMs simultaneously (i.e. ensemble guidance) versus sampling a single model per iteration. This ablation could reveal whether a more stable and potentially more robust supervision signal can be obtained by leveraging ensemble PTM outputs.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on PTM Loss Function Variants
- **Ablated Part**: The loss formulation used in the PTM supervision (CLoM)
- **Action**: REPLACE
- **Replacement**: 
  - Cross-Entropy Loss (baseline)
  - KL Divergence
  - Mean Squared Error (MSE) on logits
  - Cosine Similarity Loss
- **Metrics**: IPC Accuracy, Cross-architecture Generalization Gain

### Ablation on PTM Guidance Aggregation Strategy
- **Ablated Part**: The strategy to aggregate guidance from multiple pre-trained models
- **Action**: REPLACE
- **Replacement**: 
  - Single PTM Update (random selection per iteration)
  - Ensemble Averaged Update (averaging losses from all available PTMs)
- **Metrics**: IPC Accuracy, Cross-architecture Generalization Gain

</div>