<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/SKDream__Controllable_Multi_view_and_3D_Generation_with_Arbitrary_Skeletons

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents thorough ablation studies on the skeletal condition representation (CCE-D) and the design of the Skeletal Correlation Module (SCM) (comparing LN vs. AdaLN) as well as on the 3D appearance refinement stage. However, two important components remain uninvestigated. First, the fusion of camera pose information into the SCM via adaptive layer normalization is a novel design choice, and its isolated impact on view-dependent shape generation and overall alignment has not been studied. Removing the camera pose embedding may lead to degraded multi-view consistency and lower SKA, PickScore, and CLIP scores. Second, while the paper leverages multi-view conditioning—projecting the 3D skeleton into several 2D views—the effect of the number of conditioning views has not been evaluated. A controlled ablation that replaces the multi-view input with fewer views (e.g., a single or two views) can reveal the importance of multi-view signals on both the object-skeleton alignment and image quality. These two ablations are critical to pinpointing the contributions of the camera pose fusion and the multi-view design to the overall performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Camera Pose Embedding Ablation
- **Ablated Part**: Fusion of camera pose embedding in the Skeletal Correlation Module (SCM)
- **Action**: REMOVE
- **Metrics**: SKA Score, PickScore, CLIP Score

### Multi-view Conditioning Ablation
- **Ablated Part**: Number of skeletal condition views used during generation
- **Action**: REPLACE
- **Replacement**: 
  - single view
  - two views
  - standard multi-view (e.g., four views)
- **Metrics**: SKA Score, PickScore, CLIP Score

</div>