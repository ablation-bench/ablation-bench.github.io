<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Local_Prompt__Extensible_Local_Prompts_for_Few_Shot_Out_of_Distribution_Detection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Local-Prompt: Extensible Local Prompts for Few-Shot Out-of-Distribution Detection" introduces a novel approach to OOD detection by focusing on local prompts and regional enhancement. The method comprises two main components: global prompt guided negative augmentation and local prompt enhanced regional regularization. The paper includes several ablation studies to validate the effectiveness of these components, such as the influence of different negative augmentation strategies, the number of local negative prompts, and the effectiveness of loss components.

However, there are some potential areas where additional ablation studies could provide further insights into the method's performance. One such area is the impact of the regional number (k) used in the Regional-MCM score and local-aware score. The paper mentions that the selection of k is crucial for performance, but it does not provide a detailed ablation study on how different values of k affect the results. Another area is the integration of trained global prompts during inference. While the paper mentions that the method is extensible to trained global prompts, it does not explore the impact of different types of global prompts on the overall performance.

Therefore, I suggest two missing ablation studies: one focusing on the regional number (k) and another on the integration of different trained global prompts.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Regional Number
- **Ablated Part**: Regional number (k) used in Regional-MCM score and local-aware score
- **Action**: REPLACE
- **Replacement**: 
  - 5
  - 10
  - 20
  - 50
- **Metrics**: FPR95, AUROC, ID accuracy

### Ablation on Global Prompt Integration
- **Ablated Part**: Integration of trained global prompts during inference
- **Action**: REPLACE
- **Replacement**: 
  - hand-crafted global prompts
  - trained global prompts from different methods
- **Metrics**: FPR95, AUROC, ID accuracy

</div>