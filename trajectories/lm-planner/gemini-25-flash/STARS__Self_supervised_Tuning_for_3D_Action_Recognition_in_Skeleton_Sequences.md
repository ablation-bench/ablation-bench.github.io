<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/STARS__Self_supervised_Tuning_for_3D_Action_Recognition_in_Skeleton_Sequences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "STARS: Self-supervised Tuning for 3D Action Recognition in Skeleton Sequences" proposes a two-stage self-supervised learning framework. The first stage uses a Masked Autoencoder (MAE) approach (specifically MAMP) to pretrain an encoder. The second stage then tunes this pretrained encoder using Nearest-Neighbor Contrastive Learning (NNCLR), along with training a projector and predictor head. A key aspect of the second stage is the *partial tuning* of the encoder using layer-wise learning rate decay and performing this tuning for "a few epochs".

The paper includes several ablation studies:
1.  Comparison of different tuning strategies (NNCLR vs. DINO, MoCo).
2.  Effect of data augmentation during tuning.
3.  Effect of layer-wise learning rate decay rate (alpha).
4.  Effect of queue size in NNCLR.
5.  Comparison of the proposed 2-stage design with a 3-stage design.
6.  Combining MAMP and NNCLR loss in the second stage.
7.  Training NNCLR from scratch (without the first stage).
8.  Using naive MAE instead of MAMP in the first stage.

While these ablations cover various aspects, two important design choices in the contrastive tuning stage (Stage 2) are not fully explored:

1.  **The extent of encoder tuning:** The paper states they tune the "second-half of the encoder parameters" using layer-wise decay. However, the ablation on layer-wise decay only varies the decay rate (alpha) for this fixed set of layers. It does not investigate whether tuning a different proportion of layers (e.g., only the last few, the last 75%, the entire encoder, or even the first half) would yield better or worse results. Understanding the sensitivity to *which* and *how many* layers are tuned is crucial for justifying the "partial tuning" approach and the specific choice of the "second-half".
2.  **The duration of the contrastive tuning stage:** The paper emphasizes that tuning is done for "a few epochs" (specifically 20 epochs in the experiments). This contributes to the efficiency claim compared to traditional contrastive learning methods that train for hundreds of epochs. However, the paper does not show an ablation on the number of tuning epochs. It's important to demonstrate whether 20 epochs is optimal and how performance changes with fewer or more epochs to validate the claim that only a short tuning phase is sufficient and beneficial.

These two missing ablations are important because they directly relate to the core novelty and efficiency claims of the STARS tuning stage. Ablating the proportion of tuned layers helps understand *where* the tuning is most effective within the encoder, while ablating the tuning duration confirms the efficiency and convergence properties of the second stage.

Based on their importance for understanding the tuning mechanism, I propose these two missing ablation studies. The metrics chosen are KNN (K=10), Linear Evaluation accuracy, and Few-shot average accuracy, as these are the primary evaluation protocols where the contrastive tuning is expected to show significant benefits over the MAMP baseline, as demonstrated in the paper's main results.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Encoder Tuning Proportion
- **Ablated Part**: Proportion of encoder layers tuned during the contrastive tuning stage
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.25
  - 0.5
  - 0.75
  - 1.0
- **Metrics**: KNN (K=10) NTU-60 XSub, Linear Eval NTU-60 XSub, Few-shot Avg NTU-120 XSub

### Contrastive Tuning Duration
- **Ablated Part**: Number of epochs for the contrastive tuning stage
- **Action**: REPLACE
- **Replacement**: 
  - 5
  - 10
  - 20
  - 40
  - 80
- **Metrics**: KNN (K=10) NTU-60 XSub, Linear Eval NTU-60 XSub, Few-shot Avg NTU-120 XSub

</div>