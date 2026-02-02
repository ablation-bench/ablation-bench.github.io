<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Can_pre_trained_models_assist_in_dataset_distillation_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Can pre-trained models assist in dataset distillation?" explores the use of Pre-trained Models (PTMs) to guide the dataset distillation process. The authors propose two loss terms, CLoM (Classification Loss of pre-trained Model) and CCLoM (Contrastive Classification Loss of pre-trained Model), to leverage PTMs as supervision signals. They conduct empirical studies on various aspects of PTMs, including initialization parameters (N<sup>m</sup>), model architecture diversity (N<sup>a</sup>), training epoch, and domain knowledge. The paper includes ablation studies on the hyperparameters (α) and the number of diverse initializations (N<sup>m</sup>) and architectures (N<sup>a</sup>).

While the paper provides valuable insights into how different PTM characteristics influence DD, there are a couple of important aspects related to the proposed methods themselves that could benefit from further ablation.

Firstly, the paper introduces two distinct loss functions, CLoM and CCLoM. CLoM is used when the PTM is trained on the *original* dataset, leveraging its classification output. CCLoM is introduced specifically to handle label mismatch when the PTM is trained on an *other* dataset, using feature-based contrastive learning. However, the paper does not directly compare CLoM and CCLoM under conditions where *both* could be applied, i.e., when using a PTM trained on the original dataset. An ablation comparing CLoM and CCLoM using the same PTM (trained on the original dataset) would help isolate the contribution of the loss function design itself (classification vs. contrastive feature matching) independent of the domain transfer scenario. This is a missing fundamental comparison between the paper's two proposed mechanisms for PTM guidance.

Secondly, the paper demonstrates that using multiple PTMs (diverse initializations or architectures) improves performance, attributing it to model ensemble effects. The description mentions updating the synthetic dataset using "one model at a time" from the pool of PTMs. This suggests a simple strategy like random selection or sequential iteration. The paper does not explore alternative strategies for combining the supervision signals from multiple PTMs. Investigating different ensemble methods, such as averaging the gradients or losses from multiple PTMs within a single optimization step, could potentially lead to further performance gains or provide deeper understanding of how the knowledge from diverse PTMs is best integrated. This ablation would assess the impact of the ensemble *strategy* rather than just the *number* or *diversity* of models.

Based on this analysis, I propose the following two missing ablation studies, ranked by importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### CLoM vs CCLoM on Original Domain PTM
- **Ablated Part**: Type of PTM supervision loss (classification vs. contrastive feature matching) when using a PTM trained on the original dataset.
- **Action**: REPLACE
- **Replacement**: 
  - CLoM
  - CCLoM
- **Metrics**: Classification Accuracy (ConvNet-3), Cross-architecture Generalization Accuracy (VGG-11, ResNet-18, AlexNet, ConvNet-4)

### Ensemble Strategy for Multiple PTMs
- **Ablated Part**: Method for combining supervision signals from multiple pre-trained models during synthetic data optimization.
- **Action**: REPLACE
- **Replacement**: 
  - Random/Sequential Selection (Current)
  - Averaging Gradients
  - Averaging Losses
- **Metrics**: Classification Accuracy (ConvNet-3), Cross-architecture Generalization Accuracy (VGG-11, ResNet-18, AlexNet, ConvNet-4)

</div>