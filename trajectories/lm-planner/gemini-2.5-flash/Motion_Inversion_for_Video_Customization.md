<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Motion_Inversion_for_Video_Customization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Motion Inversion for Video Customization" proposes a novel method for motion customization in video generation using two types of Motion Embeddings: Motion Query-Key (MQK) and Motion Value (MV). These embeddings are learned from a reference video and integrated into the temporal transformer modules of a video diffusion model to modulate self-attention. The method also includes an inference strategy to debias appearance from the MV embedding.

The paper includes an ablation study (Section 4.3) that investigates two aspects:
1.  **Motion Embedding Design:** Compares different spatial dimensions for MQK and MV (1D vs 2D).
2.  **Inference Strategy:** Compares different debiasing methods for the MV embedding (differencing, normalization, none).

While these ablations are informative, they do not cover all critical aspects of the proposed method. Two important missing ablations are:

1.  **Individual Contribution of MQK and MV:** The method uses *both* MQK and MV embeddings, claiming they serve different purposes (global vs. local motion). The existing ablation compares *combinations* of their shapes but doesn't show the performance when *only* one type of embedding is used. Ablating each embedding type individually would clearly demonstrate their respective contributions to the overall performance and validate the design choice of using both. This is crucial for understanding if both are necessary and what specific role each plays.
2.  **Method of Embedding Integration:** The paper integrates the motion embeddings by *adding* them to the spatiotemporal feature tensor `F` *before* it is projected into Query, Key, and Value matrices (Equation 3). This is a specific design choice for how the embeddings modulate the temporal attention. An alternative could be to add them *after* the projection, or to use a different modulation mechanism (e.g., element-wise multiplication). Ablating this integration method would assess the effectiveness of the chosen approach compared to alternatives and confirm if adding before projection is optimal.

These two missing ablations are important because they directly probe the necessity and mechanism of the core components (the two embedding types and their integration method) that differentiate this work from others. Evaluating these would provide deeper insights into *why* the proposed method works and the specific roles of its key elements. The metrics used in the paper (Text Similarity, Motion Fidelity, Temporal Consistency, FID, User Preference) are suitable for evaluating these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Individual Motion Embedding Contribution
- **Ablated Part**: Using both Motion Query-Key (MQK) and Motion Value (MV) embeddings
- **Action**: REMOVE
- **Metrics**: Text Similarity, Motion Fidelity, Temporal Consistency, FID, User Preference

### Ablation of Motion Embedding Integration Method
- **Ablated Part**: Method of integrating motion embeddings into the temporal transformer (adding to feature tensor F before Q/K/V projection)
- **Action**: REPLACE
- **Replacement**: 
  - Add embeddings after Q/K/V projection
- **Metrics**: Text Similarity, Motion Fidelity, Temporal Consistency, FID, User Preference

</div>