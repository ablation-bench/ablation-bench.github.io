<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/multiview2novelview

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel framework for multi-view novel view synthesis consisting of two main modules: a Flow Predictor and a Pixel Generator, combined using a self-learned confidence aggregation mechanism. The Pixel Generator is designed as a recurrent network to handle varying numbers of source images and progressively improve predictions.

To understand the contribution of each component, I propose a set of ablation studies focusing on the core novelties of the method:
1.  **The two-stream architecture:** The paper claims benefits from combining flow-based prediction (reusing pixels) and pixel generation (hallucinating missing parts). Ablating each stream individually will reveal their respective contributions to the final performance. Removing the Flow Predictor tests the capability of the Pixel Generator alone, while removing the Pixel Generator tests the effectiveness of relying solely on flow-based warping from multiple views.
2.  **Self-learned Confidence Aggregation:** This mechanism is introduced to intelligently merge the predictions from the multiple flow outputs and the pixel generator output. Replacing this learned aggregation with simpler, heuristic methods (like averaging or weighted averaging) will demonstrate the value of learning the confidence for fusion.
3.  **Recurrent Pixel Generator:** The use of ConvLSTM makes the Pixel Generator capable of handling a variable number of inputs and refining its output sequentially. Ablating the recurrent nature (e.g., replacing ConvLSTM with standard convolutional layers and processing inputs differently) will show the importance of this design choice for multi-view processing and progressive improvement.
4.  **Adversarial Loss:** The paper mentions using an adversarial loss for the Pixel Generator to encourage sharper images. Removing this loss term will quantify its impact on image quality metrics, particularly perceptual ones like LPIPS.

These ablations are ranked by their perceived importance in understanding the core contributions: the two-stream design and the intelligent aggregation mechanism are arguably the most central ideas, followed by the recurrent structure for multi-view handling, and finally the specific loss function component. The metrics used for evaluation in the paper (PSNR, SSIM, LPIPS) will be used to measure the performance impact of each ablation.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Flow Predictor
- **Ablated Part**: Flow Prediction Module
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS

### No Pixel Generator
- **Ablated Part**: Pixel Generation Module
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS

### Simple Aggregation
- **Ablated Part**: Self-learned Confidence Aggregation
- **Action**: REPLACE
- **Replacement**: 
  - Average predictions
  - Weighted average based on pose distance
- **Metrics**: PSNR, SSIM, LPIPS

### Non-Recurrent Pixel Generator
- **Ablated Part**: Recurrent layers (ConvLSTM) in Pixel Generator
- **Action**: REPLACE
- **Replacement**: 
  - Standard convolutional layers
- **Metrics**: PSNR, SSIM, LPIPS

### No Adversarial Loss
- **Ablated Part**: Adversarial Loss (λLG) for Pixel Generator
- **Action**: REMOVE
- **Metrics**: PSNR, SSIM, LPIPS

</div>