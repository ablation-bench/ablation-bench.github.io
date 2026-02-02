<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Active_Fine_Tuning_of_Generalist_Policies

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two ablation experiments that we believe are currently missing from the paper. First, while the paper relies on an information‐gain–based task selection criterion to actively choose which tasks to demonstrate, it does not compare this strategy against a simpler uncertainty‐only baseline. Replacing the mutual information criterion with a task selection method based solely on the policy’s uncertainty (for example, selecting the task with the highest posterior entropy) would help clarify the added value of the full information gain measurement over a simpler surrogate. We suggest an ablation study in which the active fine‐tuning framework uses a “uncertainty-only” criterion rather than the expected information gain.

Second, the demonstration length (i.e. the number of steps in each expert demonstration) is an important design parameter in the theoretical development (with H appearing in several bounds), yet its influence on performance is not explicitly studied in the experiments. Conducting an ablation over different demonstration lengths (e.g., very short, medium, long, and very long) would reveal how the richness of each demonstration affects sample efficiency, convergence speed, and final multi‐task performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Uncertainty-Only Task Selection Ablation
- **Ablated Part**: The active task selection mechanism that uses expected information gain on the expert policy
- **Action**: REPLACE
- **Replacement**: 
  - select task based solely on highest policy entropy
  - select task based solely on posterior uncertainty
- **Metrics**: multi-task return, policy entropy reduction, sample efficiency (number of demos to reach performance threshold)

### Demonstration Length Ablation
- **Ablated Part**: The demonstration trajectory length (H) used during fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - short demonstrations (e.g., 5 steps)
  - medium demonstrations (e.g., 25 steps)
  - long demonstrations (e.g., 50 steps)
  - very long demonstrations (e.g., 100 steps)
- **Metrics**: multi-task return, convergence speed, sample efficiency

</div>