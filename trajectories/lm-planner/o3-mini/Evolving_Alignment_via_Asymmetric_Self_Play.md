<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Evolving_Alignment_via_Asymmetric_Self_Play

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key design choice in eva is whether the creator and solver share the same model parameters or use independent networks. Although the paper mentions that they can share the same network or operate independently, no experiments are presented to show how this architectural decision impacts alignment performance. A dedicated ablation study comparing shared versus independent networks would help in understanding trade‐offs in flexibility, efficiency, and performance. 

Another potential missing ablation concerns the selection threshold in the creator’s “sample” step. Currently, eva uses an informativeness metric to weight prompts and selects a fixed fraction of highly informative prompts (e.g., 25%) to evolve further. However, the study does not explore how varying this sampling ratio (say, 10%, 25%, or 50%) might affect the curriculum quality and final alignment performance. This ablation would quantify the sensitivity of eva to the choice of this hyperparameter.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Shared vs. Independent Architectures
- **Ablated Part**: Creator-solver network architecture
- **Action**: REPLACE
- **Replacement**: 
  - shared network
  - independent networks
- **Metrics**: Arena-Hard WR, MT-Bench avg. score, AlpacaEval WR

### Ablation on Informative Sampling Ratio
- **Ablated Part**: Fraction of prompts selected by the informativeness metric in the creator step
- **Action**: REPLACE
- **Replacement**: 
  - 10%
  - 25%
  - 50%
- **Metrics**: Arena-Hard WR, MT-Bench avg. score, AlpacaEval WR

</div>