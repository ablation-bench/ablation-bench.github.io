<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/PLLaVA__Parameter_efficient_LLaVA_Extension_from_Image_to_Video_Understanding

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "PLLaVA: Parameter-efficient LLaVA Extension from Image to Video Understanding" proposes a method to adapt image-based MLLMs to video understanding using a simple pooling strategy and post-training weight fusion. The core technical contributions highlighted are the pooling strategy to handle temporal information and mitigate dominant visual tokens, and the post-training optimization (weight fusion) to preserve language ability.

The paper includes several ablation studies:
1.  **Impact of Pooling Operation Design (Sec 4.2):** This study investigates different spatial pooling dimensions and temporal pooling rates using their proposed Adaptive Average Structure Pooling. It concludes that spatial pooling is beneficial (specifically 12x12), while temporal pooling is detrimental. It also shows the pooling's effect on visual token norms and generation length consistency.
2.  **Post Optimization Effects with LoRA α (Sec 4.4):** This study explores the effect of the fusion ratio (alpha) between the original image-trained LLM weights and the video-tuned LoRA weights. It shows that a combination of weights performs better than using either set exclusively, with optimal alpha values differing for different tasks (MVBench vs. VCG Score).

Based on the method description and existing ablations, I identify two important missing ablation studies:

1.  **Pooling Strategy Alternatives:** The paper proposes and analyzes the *parameters* of their Adaptive Average Structure Pooling. However, it does not compare this specific *type* of pooling to other common temporal aggregation or pooling methods (e.g., simple average pooling across time, max pooling, or even a simple temporal convolution/transformer layer before the projector). While they mention VideoChatGPT's averaging strategy, a direct comparison within their framework would strengthen the claim about the effectiveness of their chosen pooling method.
2.  **Multimodal Projector Architecture:** The paper uses a "Multimodal Projector" to map visual features to the LLM's embedding space. The specific architecture of this projector (e.g., a simple linear layer, an MLP, or a more complex structure like a Q-Former used in other MLLMs) is not detailed or ablated. The design of this interface is crucial for effectively transferring visual information to the language model, and comparing different architectures would help understand its impact on performance.

These two missing ablations are important because they investigate fundamental architectural choices (the type of temporal pooling and the visual-language interface) that are central to the proposed method's performance, beyond just tuning parameters or fusion strategies. Ablating these components would provide clearer evidence for their contribution.

I will prioritize the Pooling Type ablation slightly higher as the paper places significant emphasis on the pooling strategy as a solution to the observed failure modes.

The metrics used in the paper for evaluating overall performance are VCG Score (Avg) and MVBench (Avg), which cover generative and multi-choice tasks, respectively. These are suitable metrics for the proposed ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Pooling Type
- **Ablated Part**: Adaptive Average Structure Pooling module
- **Action**: REPLACE
- **Replacement**: 
  - Simple Average Pooling
  - Max Pooling
- **Metrics**: VCG Score (Avg), MVBench (Avg)

### Ablation: Projector Architecture
- **Ablated Part**: Multimodal Projector
- **Action**: REPLACE
- **Replacement**: 
  - Linear Layer
  - Q-Former
- **Metrics**: VCG Score (Avg), MVBench (Avg)

</div>