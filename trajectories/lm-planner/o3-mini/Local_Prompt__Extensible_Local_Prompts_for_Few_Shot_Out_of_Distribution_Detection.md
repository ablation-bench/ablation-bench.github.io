<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Local_Prompt__Extensible_Local_Prompts_for_Few_Shot_Out_of_Distribution_Detection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper thoroughly investigates the contribution of local prompts by analyzing various loss components, negative augmentation strategies, and the influence of training parameters. However, two important aspects remain unaddressed. First, the method currently fixes (freezes) the global prompts while only fine-tuning the local prompts. Since the global prompts are used both for guidance during negative augmentation and for computing the OOD score, it is important to understand if jointly fine‐tuning global and local prompts (or a controlled fine‐tuning of global prompts with a lower learning rate) would further enhance the performance—or perhaps introduce unwanted interference. Such an ablation would directly assess the impact of the chosen design to separate global and local information. Second, the proposed Regional OOD score employs a T_k mean aggregation function to combine local prompt responses. Exploring alternative aggregation strategies (for example, using max pooling, average pooling, or a weighted sum) could provide deeper insight into the effect of the aggregation choice on key metrics like FPR95 and AUROC. These two experiments are ranked in order of importance with the joint training ablation being the primary candidate.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Joint Training of Global and Local Prompts
- **Ablated Part**: Freezing of global prompts; assess the impact of jointly fine-tuning both global and local prompts on OOD detection and ID classification.
- **Action**: REPLACE
- **Replacement**: 
  - joint fine-tuning of global and local prompts
  - global prompts fine-tuned with a lower learning rate
- **Metrics**: FPR95, AUROC, ID accuracy

### Alternative Regional Aggregation Strategies
- **Ablated Part**: The T_k mean aggregation function used in computing the regional OOD score from local prompt responses.
- **Action**: REPLACE
- **Replacement**: 
  - max pooling
  - average pooling
  - weighted sum aggregation
- **Metrics**: FPR95, AUROC

</div>