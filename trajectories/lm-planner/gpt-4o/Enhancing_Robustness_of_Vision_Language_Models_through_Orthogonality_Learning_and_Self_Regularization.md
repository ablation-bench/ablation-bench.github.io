<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Enhancing_Robustness_of_Vision_Language_Models_through_Orthogonality_Learning_and_Self_Regularization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Enhancing Robustness of Vision-Language Models through Orthogonality Learning and Self-Regularization" introduces a novel method called OrthSR, which incorporates orthogonal fine-tuning and self-regularization to improve the robustness and generalization of vision-language models like CLIP. The method involves injecting trainable orthogonal matrices into the transformer architecture and employing a self-regularization strategy to maintain zero-shot generalization capabilities. Additionally, attentive CutOut data augmentation is used to enhance sample diversity.

The existing ablation studies in the paper focus on evaluating the impact of orthogonal tuning on different encoders (image and text) and the effect of removing components like the Kullback-Leibler loss and CutOut augmentation. However, there are some missing ablation studies that could provide further insights into the method's components.

One potential missing ablation study is the effect of the orthogonality constraint itself. The paper emphasizes the importance of maintaining orthogonality to preserve hyperspherical energy and ensure stable convergence. An ablation study that removes or modifies the orthogonality constraint could help quantify its contribution to the overall performance.

Another missing ablation study could focus on the self-regularization strategy. The paper claims that this strategy helps retain the generalization of the model by using the pretrained weights as an anchor point. An ablation study that removes or alters the self-regularization component could provide insights into its effectiveness in maintaining zero-shot generalization.

These ablation studies would help attribute the method's performance to its major components and provide a more comprehensive understanding of the contributions of each part.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Orthogonality Constraint
- **Ablated Part**: orthogonality constraint in orthogonal fine-tuning
- **Action**: REMOVE
- **Metrics**: Base Acc., Novel Acc., HM

### Ablation of Self-Regularization
- **Ablated Part**: self-regularization strategy
- **Action**: REMOVE
- **Metrics**: Base Acc., Novel Acc., HM

</div>