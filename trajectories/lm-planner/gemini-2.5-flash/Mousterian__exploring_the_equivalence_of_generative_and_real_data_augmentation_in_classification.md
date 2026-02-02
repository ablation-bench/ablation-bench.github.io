<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Mousterian__exploring_the_equivalence_of_generative_and_real_data_augmentation_in_classification

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Mousterian: exploring the equivalence of generative and real data augmentation in classification" conducts a comprehensive empirical study on using synthetic data for image classification. The authors investigate the effectiveness of generative data augmentation using models trained solely on the internal dataset and models trained on external large-scale data. They analyze the relationship between the amount of real and synthetic data, the quality of synthetic data, and the size of the base training set, providing empirical formulas for data equivalence.

The paper includes several experiments that function as ablations or comparisons:
1.  Comparing internal vs. external generative models (Vanilla-DDPM/EDM vs. CIFAKE/Stable Diffusion).
2.  Comparing different qualities of synthetic data (Vanilla-DDPM vs. EDM; SD2 vs. SD3).
3.  Varying the amount of base real data (CIFAR-Small, Half, Full; different per-class counts on ImageNet).
4.  Varying the ratio of synthetic to real data in mixed training.
5.  Comparing supervised and zero-shot classification settings.
6.  Domain classification experiments to quantify the real/synthetic data gap.
7.  An experiment showing limited benefit when fine-tuning a strong pre-trained model (ViT-L/16) with synthetic data.

Based on the paper's focus and common practices in the field, two important missing ablation studies are identified:

1.  **Fine-tuning External Generative Models on the Target Dataset:** The paper explicitly mentions that prior work fine-tunes external generative models on the target dataset (lines 73-74) but chooses *not* to do this in their main experiments, instead focusing on models trained *solely* internally or *solely* externally. Fine-tuning an external model on the target dataset is a crucial step to adapt the generative model to the specific data distribution of the classification task, potentially bridging the domain gap highlighted in the paper (Figure 1a, 1b, Figure 11). Ablating this step would directly show the benefit (or lack thereof) of adapting the powerful external generative models to the target domain before generating augmentation data. This is highly relevant to understanding the optimal way to leverage external generative models for classification.

2.  **Mixed Training Sampling Strategy:** The paper uses a simple mixed training strategy by concatenating real and synthetic datasets and using PyTorch's `RandomSampler` (lines 1070-1072). While they extensively study the *ratio* of real to synthetic data, the *method* of sampling from the combined dataset is not explored. Alternative sampling strategies, such as class-balanced sampling (especially relevant if synthetic data generation quality varies by class), weighted sampling (e.g., giving more weight to real data or hard synthetic examples), or curriculum learning approaches (e.g., introducing synthetic data gradually or later in training), could potentially impact performance and sample efficiency. Ablating the sampling strategy would provide insights into how to best utilize the combined dataset during training.

Both of these ablations address key aspects of the paper's investigation: the generative process (fine-tuning) and the training process using the generated data (sampling strategy). The fine-tuning ablation is arguably more fundamental to the data generation side, which is a primary focus, making it slightly more important. The metrics used in the paper for classification performance are Top-1 and Top-5 accuracy, which should be used for these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### External Gen Model Fine-tuning
- **Ablated Part**: Using an external generative model without fine-tuning on the target dataset
- **Action**: REPLACE
- **Replacement**: 
  - External generative model fine-tuned on target dataset
- **Metrics**: Top-1 Acc, Top-5 Acc

### Mixed Training Sampling
- **Ablated Part**: Sampling strategy for combined real and synthetic dataset during mixed training (currently random sampling)
- **Action**: REPLACE
- **Replacement**: 
  - Class-balanced sampling
  - Weighted sampling
  - Curriculum learning
- **Metrics**: Top-1 Acc, Top-5 Acc

</div>