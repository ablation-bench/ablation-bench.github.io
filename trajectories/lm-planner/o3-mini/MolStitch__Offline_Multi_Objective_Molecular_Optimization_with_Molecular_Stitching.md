<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/MolStitch__Offline_Multi_Objective_Molecular_Optimization_with_Molecular_Stitching

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that would further illuminate the impact of key design choices in MolStitch. First, although the paper shows the effectiveness of using StitchNet via its self‐supervised training process, it does not specifically isolate the contribution of the chemical feedback component. In the current design, StitchNet leverages the offline dataset’s objective scores as chemical supervision when combining fragments, which is expected to better align generated molecules with desirable properties. An ablation study that removes this chemical feedback (i.e. training StitchNet solely with the rule‐based crossover signal or using only maximum likelihood pre-training) would quantify its contribution. We recommend using metrics such as Hypervolume (HV), R2 indicator, average property score (APS), and diversity measures to evaluate how performance and molecular diversity drop if the chemical feedback is omitted.

Second, priority sampling is implemented through a Dirichlet distribution with a fixed concentration parameter (α=1.0) to generate diverse weight configurations for stitching. However, a sensitivity analysis on the concentration parameter is missing. Replacing the fixed α value with a set of candidate values (e.g., 0.5, 1.0, 2.0) would help understand its impact, as the Dirichlet shape determines the balance diversity in sampled weight configurations. Metrics like HV, R2, and diversity (e.g., Tanimoto-based diversity or scaffold diversity) should be reported to assess which α setting leads to better performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Remove Chemical Feedback from StitchNet
- **Ablated Part**: the chemical feedback component in the self-supervised training of StitchNet (i.e. using objective scores from the offline dataset as chemical feedback for stitched molecules)
- **Action**: REMOVE
- **Metrics**: Hypervolume (HV), R2 indicator, Average Property Score (APS), Molecular Diversity Metrics

### Vary Dirichlet Concentration Parameter in Priority Sampling
- **Ablated Part**: the fixed Dirichlet concentration parameter (α) used in priority sampling for selecting weight configurations for molecular stitching
- **Action**: REPLACE
- **Replacement**: 
  - 0.5
  - 1.0
  - 2.0
- **Metrics**: Hypervolume (HV), R2 indicator, Diversity Metrics

</div>