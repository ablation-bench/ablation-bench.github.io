<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Black_Sheep_in_the_Herd__Playing_with_Spuriously_Correlated_Attributes_for_Vision_Language_Recognition

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces two major modules: SPURIOUS ATTRIBUTE PROBING (SAP) for identifying and filtering spurious attributes and SPURIOUS ATTRIBUTE SHIELDING (SAS) to mitigate their influence via newly‐constructed pseudo categories. Although the experimental study is quite comprehensive, two important ablations are missing. First, it is critical to verify that the gains obtained by SAS truly stem from its spurious-attribute‐guided pseudo category generation. A randomized or uniform pseudo-category construction (i.e. replacing the carefully identified spurious attributes with a random selection from the attribute pool) would serve as an essential baseline. This ablation would clearly demonstrate that the specific selection strategy is crucial for the improved generalization performance. Second, the paper employs a selective optimization trick in SAS where only the top “10%” of categories (as measured by a spurious correlation ratio) are used to optimize the subsidiary task, thereby reducing computational overhead. However, the exact choice of this percentage is not systematically studied. A thorough ablation varying this parameter (e.g. testing 5%, 10%, and 20%) would shed more light on the trade-off between efficiency (training time) and effectiveness (generalization accuracy). These two experiments would provide clearer evidence of the core contributions of the proposed method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Spurious Attribute Guided vs Random Pseudo Categories
- **Ablated Part**: The pseudo-category construction mechanism in SAS that uses spurious attributes identified by SAP; testing whether using randomly selected attributes instead influences performance.
- **Action**: REPLACE
- **Replacement**: 
  - random selection of attributes
  - uniform pseudo-category generation
- **Metrics**: Base Accuracy, New Accuracy, Spurious Rate, Harmonic Mean Accuracy

### Selective Optimization Ratio Ablation
- **Ablated Part**: The selective optimization strategy in SAS that applies the subsidiary task to only a fixed top percentage of categories based on spurious correlation ratio (SCR).
- **Action**: REPLACE
- **Replacement**: 
  - 5%
  - 10%
  - 20%
- **Metrics**: Base Accuracy, New Accuracy, Harmonic Mean Accuracy, Training Time

</div>