<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/cet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Preserving Commonsense Knowledge from Pre-trained Language Models via Causal Inference" proposes Causal Effect Tuning (CET), a fine-tuning method based on a causal view of catastrophic forgetting. The core idea is to estimate and maximize the causal effect of pre-trained data by incorporating information from K-Nearest Neighbors (KNNs) in the objective function. The method's objective function (Eq 9) involves a weighted sum of likelihoods over the anchor sample and its KNNs, applied selectively based on a similarity threshold $\theta$. For Commonsense QA, a heuristic is used to find KNNs based on gold answer similarity, and a specific input format is used for KNNs.

The paper includes an ablation study (Section 4.3) that compares CET to vanilla fine-tuning ("w/o KNN"), and ablates the KNN search method ("w/o Answer Similarity"), the KNN input format ("w/o Question Augmentation"), and the similarity threshold ("w/o Threshold").

Based on the method description and the paper's existing ablations, the following aspects are key components or hyperparameters whose influence warrants further investigation:

1.  **The Weighting Parameter ($W_0$):** This parameter directly controls the balance between the anchor sample's likelihood and the neighbors' likelihoods in the causal objective term when neighbors are used. The paper implicitly tests $W_0=1$ (in "w/o KNN"), but exploring other values is crucial to understand the optimal balance.
2.  **The Number of Neighbors ($K$):** This hyperparameter determines how many neighbors contribute to the causal objective for samples above the similarity threshold. Testing different values shows the sensitivity to the amount of neighbor information.
3.  **The KNN Selection Strategy:** The method uses a similarity threshold ($\theta$) to decide which samples benefit from the neighbor-based objective. The paper removed the threshold entirely, but exploring different threshold values or alternative selection strategies (like selecting a fixed percentage of samples) can provide more granular insight into the importance of this selectivity.
4.  **The KNN Weighting Function:** The paper uses a simple weighting scheme ($W_0$ for the anchor, uniform for neighbors). Investigating a distance-based weighting scheme could reveal if this simple approach is sufficient or if incorporating distance information improves performance.
5.  **The Source of KNNs:** The paper finds KNNs from the training set. Exploring whether using a larger pool of data for KNN search (e.g., training + development sets) impacts performance can shed light on the importance of the data source for the "preserved knowledge" represented by the neighbors.

These five ablations cover the main hyperparameters of the objective ($W_0$, $K$), the mechanism for selecting and weighting neighbors, and the data source for finding them, providing a comprehensive analysis beyond the paper's existing ablations. The primary metric used in the paper for evaluating performance is Accuracy, which will be used for these ablations as well.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Anchor Weight W0
- **Ablated Part**: Weighting parameter W0 for the anchor sample in the causal objective term
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.25
  - 0.5
  - 0.75
  - 1.0
- **Metrics**: Accuracy

### Ablation: Number of Neighbors K
- **Ablated Part**: Maximum number of K-Nearest Neighbors (K) used in the causal objective term
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 5
  - 10
- **Metrics**: Accuracy

### Ablation: KNN Selection Strategy
- **Ablated Part**: Strategy for selecting samples to apply the causal objective (similarity threshold)
- **Action**: REPLACE
- **Replacement**: 
  - Original threshold (theta)
  - Fixed percentage of samples (e.g., top 25%)
  - Fixed percentage of samples (e.g., top 50%)
- **Metrics**: Accuracy

### Ablation: KNN Weighting Function
- **Ablated Part**: Weighting function W_ik for KNN samples in the causal objective term
- **Action**: REPLACE
- **Replacement**: 
  - Fixed W0 and uniform rest (original)
  - Distance-based weighting (e.g., inverse distance)
- **Metrics**: Accuracy

### Ablation: KNN Data Source
- **Ablated Part**: Data source for finding K-Nearest Neighbors
- **Action**: REPLACE
- **Replacement**: 
  - Training set (original)
  - Training + Development sets
- **Metrics**: Accuracy

</div>