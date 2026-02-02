<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/robustvlm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes FARE, an unsupervised adversarial fine-tuning method for the CLIP vision encoder to improve its robustness while preserving its clean performance on downstream tasks like Large Vision-Language Models (LVLMs) and zero-shot classification. The core idea is to minimize the $\ell_2$ distance between the embedding of an adversarially perturbed image produced by the fine-tuned model ($\phi(z)$) and the embedding of the original clean image produced by the *original* CLIP model ($\phiorg(x)$). This is formulated as the loss $L_{\textrm{\ours}}(\phi,x)= \max_{\norm{z-x}_\infty \leq \epsilon} \norm{\phi(z)-\phiorg(x)}^2_2$.

Based on this, key components to ablate are:
1.  **The target embedding:** The method specifically targets the *original* CLIP embedding ($\phiorg(x)$). A natural ablation is to compare this to targeting the clean embedding of the *current* model being fine-tuned ($\phi(x)$), which is a more common approach in feature-level adversarial training. This would highlight the importance of preserving the original CLIP feature space for downstream compatibility.
2.  **The loss function/distance metric:** The method uses the $\ell_2$ distance between embeddings. The paper contrasts this with TeCoA, which implicitly uses cosine similarity via the cross-entropy loss on classification logits. Ablating the $\ell_2$ distance and replacing it with a cosine similarity-based loss (e.g., minimizing $1 - \cos(\phi(z), \phiorg(x))$) would test whether preserving the magnitude of the embedding (which $\ell_2$ does but cosine similarity does not) is crucial for the method's success, particularly for LVLMs that might use the unnormalized embeddings.

These two ablations directly investigate the novel aspects of the FARE method compared to existing approaches and standard adversarial training techniques. They are the most important experiments to understand *why* FARE works and what contributes to its ability to maintain clean performance while gaining robustness.

The metrics to report should align with those used in the paper, primarily focusing on the performance of LVLMs (OpenFlamingo, LLaVA) and zero-shot classification using the fine-tuned CLIP encoder. Table 1 provides average clean and robust performance metrics for LVLMs across multiple datasets (COCO, Flickr30k, TextVQA, VQAv2) for different $\ell_\infty$ perturbation sizes ($\epsilon=2/255, 4/255$). The paper also discusses zero-shot classification accuracy and robustness. Therefore, the metrics should include average VLM performance (clean and robust) and zero-shot classification accuracy (clean and robust).

I will propose two ablation studies based on these key components, ranked by their perceived importance in validating the core claims of the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Target Embedding Ablation
- **Ablated Part**: Target embedding for the unsupervised adversarial loss
- **Action**: REPLACE
- **Replacement**: 
  - Original CLIP embedding (phi_org(x))
  - Current model's clean embedding (phi(x))
- **Metrics**: Average VLM Clean Performance, Average VLM Robust Performance (l_inf, epsilon=2/255), Average VLM Robust Performance (l_inf, epsilon=4/255), Zero-shot Classification Clean Accuracy, Zero-shot Classification Robust Accuracy (l_inf, epsilon=2/255), Zero-shot Classification Robust Accuracy (l_inf, epsilon=4/255)

### Loss Function Ablation
- **Ablated Part**: Distance metric used in the unsupervised adversarial loss
- **Action**: REPLACE
- **Replacement**: 
  - L2 distance
  - Cosine similarity distance (1 - cos(phi(z), phi_org(x)))
- **Metrics**: Average VLM Clean Performance, Average VLM Robust Performance (l_inf, epsilon=2/255), Average VLM Robust Performance (l_inf, epsilon=4/255), Zero-shot Classification Clean Accuracy, Zero-shot Classification Robust Accuracy (l_inf, epsilon=2/255), Zero-shot Classification Robust Accuracy (l_inf, epsilon=4/255)

</div>