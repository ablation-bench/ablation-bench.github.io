<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Guiding_Instruction_based_Image_Editing_via_Multimodal_Large_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We first analyzed the key components in MGIE and noted that the paper ablates the use of expressive instructions through different training schemes (FZ, FT, and E2E) but does not isolate two other major design choices. First, MGIE uses a set number of appended visual tokens ([IMG]) to bridge the language modality with visual guidance. However, the impact of the quantity of these tokens on editing performance remains unexplored. Varying the number of tokens (for example, from none to a larger set such as 0, 4, 8, or 16 tokens) would directly inform how much visual-related detail the model needs to generate proper latent guidance. Second, the method applies a pre-trained summarizer to distill raw MLLM outputs into concise expressive instructions. Although conciseness is argued to reduce redundancy and guide the editing process effectively, the paper does not compare this strategy against using the raw verbose output produced by the MLLM. Ablating the summarization step (i.e. replacing the summarizer with an identity function or testing both setups) could clarify its impact on image editing quality. We propose these two ablation studies to further isolate and understand the contributions of these design choices. The evaluation would use the same metrics as the paper (e.g., L1, SSIM, LPIPS, DINO CVS, and CTS), with additional human evaluation for instructive clarity when appropriate.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Visual Token Quantity
- **Ablated Part**: The appended visual tokens ([IMG]) that bridge the language and visual modalities in the edit head
- **Action**: REPLACE
- **Replacement**: 
  - 0 tokens
  - 4 tokens
  - 8 tokens
  - 16 tokens
- **Metrics**: L1, SSIM, LPIPS, DINO CVS, CTS

### Ablation: Role of Summarization in Expressive Instructions
- **Ablated Part**: The pre-trained summarizer that condenses raw MLLM outputs into concise expressive instructions
- **Action**: REPLACE
- **Replacement**: 
  - raw verbose instructions
  - summarized instructions
- **Metrics**: L1, SSIM, DINO CVS, LPIPS, CTS, Human Evaluation

</div>