<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/bbox-adapter

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies that target the core components of BBox-Adapter. First, the ranking‐based noise contrastive estimation (NCE) loss is the key innovation for distinguishing between the target and source domain responses. Evaluating this component by replacing it with a standard loss (e.g., masked language modeling loss) will quantify its contribution to model accuracy. Second, the online adaptation mechanism leverages iterative sampling and dynamic feedback for continuously refining the adapter. Removing this mechanism will reveal how much performance gain is due to online updates versus a one-shot adaptation. Third, the candidate sampling and update strategy – namely, how positive and negative samples are selected (via the SEL function) – is central to learning the correct energy function. Replacing the dynamic, feedback-based candidate updates with a fixed sampling strategy (e.g. using only ground-truth values) can help us understand the impact of this iterative selection process. Fourth, the incorporation of spectral normalization in the energy-based adapter stabilizes training. Ablating this normalization will expose its role in mitigating sharp gradients and ensuring training stability. Finally, given that BBox-Adapter uses a lightweight adapter (with sizes reported as 0.1B–0.3B), a systematic study that varies the adapter size (testing additional alternatives such as 0.05B and 0.5B) will elucidate the trade-off between performance and computational cost. Each study will be evaluated on key metrics such as task accuracy, cost efficiency, convergence or stability measures, and memory or inference cost where applicable.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Loss Function Replacement
- **Ablated Part**: Ranking-based NCE loss used for adapter updates
- **Action**: REPLACE
- **Replacement**: 
  - MLM loss
  - Standard NCE loss without ranking
- **Metrics**: Accuracy, Delta Improvement (%), Training Stability

### Ablation 2: Online Adaptation Removal
- **Ablated Part**: Online adaptation mechanism that iteratively updates positive and negative samples via feedback
- **Action**: REMOVE
- **Metrics**: Accuracy, Convergence Speed, Training Cost

### Ablation 3: Candidate Sampling Strategy
- **Ablated Part**: Dynamic candidate sampling and update (SEL function) for distinguishing positives and negatives
- **Action**: REPLACE
- **Replacement**: 
  - Fixed sampling using only ground-truth labels
  - Static candidate assignment from initial inference
- **Metrics**: Accuracy, Adaptation Cost

### Ablation 4: Spectral Normalization Effect
- **Ablated Part**: Spectral normalization applied to stabilize the energy-based adapter's training
- **Action**: REMOVE
- **Metrics**: Accuracy, Training Loss Variance, Stability Metrics

### Ablation 5: Adapter Size Variation
- **Ablated Part**: Size of the lightweight adapter model
- **Action**: REPLACE
- **Replacement**: 
  - 0.05B
  - 0.1B
  - 0.3B
  - 0.5B
- **Metrics**: Accuracy, Training/Inference Cost, GPU Memory Usage

</div>