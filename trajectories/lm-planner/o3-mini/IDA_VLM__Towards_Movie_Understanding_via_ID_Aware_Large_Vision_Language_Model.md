<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/IDA_VLM__Towards_Movie_Understanding_via_ID_Aware_Large_Vision_Language_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper provides ablation studies on the dual-stage instruction tuning and on the effect of the proposed ID-Former module. However, two critical aspects are missing. First, the role of the visual component of ID references is not isolated. That is, how important is the explicit usage of cropped ID images (paired with names) compared to relying solely on textual identity cues? Removing the visual component in the ID reference can reveal its importance for aligning and memorizing character identities. Second, the paper does not explore the impact of varying the number of ID images provided per character. In movies, characters may be seen in different poses or under various conditions; thus, assessing whether a single ID image versus multiple ID images per identity affects performance is crucial for understanding the robustness of the method. These ablations would provide insights into the sensitivity of the system to the format and quantity of ID references.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Visual Component in ID Reference
- **Ablated Part**: Visual ID images in the instruction tuning process, which provide character appearance cues
- **Action**: REMOVE
- **Metrics**: Matching, Location, Q&A, Caption

### Ablation: Vary Number of ID Reference Images
- **Ablated Part**: The number of ID images provided per character in the ID reference
- **Action**: REPLACE
- **Replacement**: 
  - Single ID image
  - Multiple ID images
- **Metrics**: Matching, Location, Q&A, Caption

</div>