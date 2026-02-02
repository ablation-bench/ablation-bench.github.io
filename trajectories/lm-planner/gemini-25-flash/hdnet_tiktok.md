<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/hdnet_tiktok

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the paper "Learning High Fidelity Depths of Dressed Humans by Watching Social Media Dance Videos". The studies should be ranked by importance and formatted as JSONL, including the ablated part, action (REMOVE, REPLACE, ADD), potential replacements/additions, and relevant metrics from the paper.

I have identified the core components of the proposed method:
1.  Leveraging social media dance videos for self-supervision via temporal consistency (Lw loss).
2.  Jointly learning depth and surface normals and enforcing geometric consistency (Ls loss).
3.  Using a mix of supervised (3D scanned models, Lz, Ln losses) and self-supervised (video, Lw, Ls losses) data.
4.  Network architecture details, such as feeding predicted normals into the depth estimator.
5.  Specific techniques within the self-supervision, like part-based warping.

Based on the paper's emphasis and contributions, I prioritize the ablations as follows:

1.  **Ablating the temporal self-supervision (Lw):** This is presented as a key novelty enabling the use of the large video dataset. Removing this loss directly tests the value of this approach.
2.  **Ablating the geometric consistency loss (Ls):** The joint learning of depth and normals and their consistency is highlighted for capturing fine details. Removing Ls tests this aspect.
3.  **Ablating the supervised data (Ds):** The method uses both supervised and self-supervised data. Removing the supervised data from training shows the capability of the self-supervision alone.
4.  **Ablating the surface normal input to the depth estimator:** This is a specific architectural design choice that is claimed to be beneficial.
5.  **Ablating the part-based warping:** This is a detail of the temporal self-supervision mechanism. Replacing it with a simpler global warping can test its importance.

The metrics used in the paper's quantitative evaluation (Table 1) are "D. error", "N. error", and "R. error". I will use these metrics for all suggested ablations.

I will now format these into the required JSONL structure.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation_NoTemporalSelfSupervision
- **Ablated Part**: Temporal self-supervision loss (Lw) from video data
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

### Ablation_NoGeometricConsistency
- **Ablated Part**: Geometric consistency loss (Ls) between predicted and derived surface normals
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

### Ablation_NoSupervisedData
- **Ablated Part**: Training data from 3D scanned models (Ds) and corresponding losses (Lz, Ln)
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

### Ablation_NoNormalInputToDepth
- **Ablated Part**: Input of predicted surface normal to the depth estimator network
- **Action**: REMOVE
- **Metrics**: D. error, N. error, R. error

### Ablation_GlobalWarping
- **Ablated Part**: Part-based SE3 transformation for temporal warping
- **Action**: REPLACE
- **Replacement**: 
  - Global SE3 transformation
- **Metrics**: D. error, N. error, R. error

</div>