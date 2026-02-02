<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Local_Prompt__Extensible_Local_Prompts_for_Few_Shot_Out_of_Distribution_Detection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Local-Prompt: Extensible Local Prompts for Few-Shot Out-of-Distribution Detection" proposes a novel approach to out-of-distribution (OOD) detection using local prompts. The authors argue that existing methods mainly focus on optimizing global prompts, ignoring refined utilization of local information with regard to outliers. To address this, they introduce Local-Prompt, a coarse-to-fine tuning paradigm that emphasizes regional enhancement with local prompts. The method comprises two integral components: global prompt guided negative augmentation and local prompt enhanced regional regularization.

The authors conduct comprehensive experiments to demonstrate the effectiveness of their method. They compare their approach with state-of-the-art methods in both OOD detection and ID accuracy evaluation under 4-shot tuning and 16-shot tuning settings. The results show that their method outperforms the state-of-the-art methods in both settings, exhibiting the superiority and potential of enhancing local prompts for OOD detection and ID classification ability.

However, the paper lacks ablation studies on the impact of the number of local prompts and the effect of different local prompt initialization methods. Additionally, the authors do not provide a thorough analysis of the computational cost of their method compared to other approaches.

To address these limitations, we suggest two missing ablation studies:

1. **Ablation Study 1:** Investigate the impact of the number of local prompts on the performance of the Local-Prompt method. This study will help understand how the number of local prompts affects the method's ability to detect OOD samples and its computational cost.
2. **Ablation Study 2:** Examine the effect of different local prompt initialization methods on the performance of the Local-Prompt method. This study will help understand how the initialization of local prompts affects the method's ability to detect OOD samples and its robustness to different initialization methods.

These ablation studies will provide valuable insights into the Local-Prompt method and help identify areas for further improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: number of local prompts
- **Action**: REPLACE
- **Replacement**: 
  - 10
  - 20
  - 50
  - 100
- **Metrics**: FPR95, AUROC

### Ablation Study 2
- **Ablated Part**: local prompt initialization method
- **Action**: REPLACE
- **Replacement**: 
  - random initialization
  - k-means initialization
  - pre-trained language model initialization
- **Metrics**: FPR95, AUROC

</div>