<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Finetuning_CLIP_to_Reason_about_Pairwise_Differences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Finetuning CLIP to Reason about Pairwise Differences" proposes PC-CLIP, a method to finetune CLIP by aligning the difference between image embeddings with the text embedding of LLM-generated descriptions of those differences. The core components involve generating synthetic comparative text data using LLMs and finetuning CLIP's text encoder with a contrastive loss on image pairs and their corresponding difference descriptions.

The paper includes several ablation studies and comparisons:
1.  Comparison against baseline CLIP, CLIP finetuned on COCO with standard captions, and CLIP finetuned on LLM-rewritten captions (non-comparative). This demonstrates the benefit of the comparative finetuning objective itself.
2.  An ablation on filtering the LLM-generated data (Appendix B), showing that filtering improves performance but unfiltered data is still effective.
3.  An ablation on the dataset used for generating comparatives (COCO vs. CUB) (Appendix G.1), showing the impact of the data distribution.
4.  An ablation on the loss function used for finetuning (contrastive vs. MSE) (Appendix G.2), showing similar performance.
5.  Linear probe results (Appendix D) and results with a larger CLIP model (Appendix E) explore the learned features and scalability.

While these ablations cover important aspects, two key areas related to the method's core design choices are not fully explored:

1.  **The choice of LLM for generating the synthetic comparative data:** The quality and nature of the LLM-generated descriptions are fundamental to the PC-CLIP finetuning. The paper uses LLaMA2-13B-chat-hf for generating the finetuning data and GPT-4 for generating comparative prompts used in evaluation. An ablation comparing different LLMs for the *finetuning data generation* would reveal how sensitive the method is to the LLM's capabilities and potentially identify better LLMs for this task.
2.  **The scope of finetuning:** The paper explicitly states that only the text encoder is finetuned for computational efficiency. While linear probe results on the image encoder are provided, the impact of finetuning the image encoder, or both encoders, with the PC-CLIP objective is not evaluated. This ablation would clarify whether finetuning the image encoder provides additional benefits in aligning the image difference space, albeit at a higher computational cost.

These two missing ablations are crucial for understanding the robustness of the method to the data generation process and the contribution of finetuning different parts of the CLIP model to the observed performance gains. The metrics used in the paper to evaluate the finetuned model's capabilities (difference-based classification accuracy, standard zeroshot classification accuracy, and embedding quality metrics like cosine distance) are appropriate for evaluating these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### LLM for Comparative Generation
- **Ablated Part**: Large Language Model used to generate synthetic comparative text descriptions for finetuning data.
- **Action**: REPLACE
- **Replacement**: 
  - GPT-3.5
  - GPT-4
  - Other LLaMA variants
- **Metrics**: Difference-based classification accuracy, Standard zeroshot classification accuracy, Embedding Quality (Cosine Distance)

### Finetuning Scope
- **Ablated Part**: Which part(s) of the CLIP model are finetuned with the PC-CLIP objective.
- **Action**: REPLACE
- **Replacement**: 
  - Text Encoder Only
  - Image Encoder Only
  - Both Encoders
- **Metrics**: Difference-based classification accuracy, Standard zeroshot classification accuracy, Embedding Quality (Cosine Distance)

</div>