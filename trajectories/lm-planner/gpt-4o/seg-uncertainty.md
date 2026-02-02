<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/seg-uncertainty

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces a novel method for unsupervised scene adaptation using memory regularization to exploit intra-domain knowledge. The key components of the method include the use of a primary and auxiliary classifier to reduce prediction inconsistency, memory regularization to align predictions within the same domain, and a two-stage training process involving adversarial alignment and self-training with pseudo labels. The ablation studies should focus on understanding the contribution of these components to the overall performance.

1. **Memory Regularization**: The core innovation of the paper is the memory regularization mechanism. An ablation study should investigate the impact of removing this component to understand its contribution to performance improvements.

2. **Auxiliary Classifier**: The method uses an auxiliary classifier to help reduce prediction inconsistency. An ablation study could explore the effect of removing the auxiliary classifier to see how it affects the model's ability to learn intra-domain knowledge.

3. **Adversarial Loss**: The adversarial loss is used to align the source and target domains. An ablation study could examine the effect of removing this loss to determine its importance in the domain adaptation process.

4. **Self-training with Pseudo Labels**: The second stage of training involves fine-tuning the model with pseudo labels. An ablation study could assess the impact of this stage by removing it and observing changes in performance.

5. **Combination of Classifier Outputs**: The final prediction combines outputs from both classifiers. An ablation study could test different combinations or rely solely on one classifier to evaluate the effectiveness of this strategy.

These ablation studies will help attribute the method's performance to its major components and provide insights into the importance of each part.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Memory Regularization
- **Action**: REMOVE
- **Metrics**: mIoU

### Ablation 2
- **Ablated Part**: Auxiliary Classifier
- **Action**: REMOVE
- **Metrics**: mIoU

### Ablation 3
- **Ablated Part**: Adversarial Loss
- **Action**: REMOVE
- **Metrics**: mIoU

### Ablation 4
- **Ablated Part**: Self-training with Pseudo Labels
- **Action**: REMOVE
- **Metrics**: mIoU

### Ablation 5
- **Ablated Part**: Combination of Classifier Outputs
- **Action**: REPLACE
- **Replacement**: 
  - Primary Only
  - Auxiliary Only
- **Metrics**: mIoU

</div>