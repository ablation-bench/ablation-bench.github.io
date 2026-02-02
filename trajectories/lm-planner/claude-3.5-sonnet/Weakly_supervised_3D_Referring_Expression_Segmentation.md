<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Weakly_supervised_3D_Referring_Expression_Segmentation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a Multi-Expert Network (MEN) for weakly supervised 3D referring expression segmentation, with two main components:

1. Multi-Expert Mining (MEM) module with three experts:
- Full-context expert: Uses Long-CLIP to process complete visual-language context
- Attribute expert: Focuses on fine-grained instance attributes
- Category expert: Handles semantic category matching

2. Multi-Expert Aggregation (MEA) module that consolidates the outputs from the three experts

The paper already includes ablation studies on:
- Different combinations of experts in MEM
- Different consolidation strategies in MEA (Max, Average, MEA)
- Image source selection for experts
- Long-CLIP vs other encoders
- Text attribute phrase extraction methods

However, I notice two important missing ablation studies:

1. The number of experts in MEM - The paper uses three specific experts but doesn't justify this choice. Testing different numbers/types of experts would help understand if this is optimal.

2. The architecture of the MEA module - While they test different consolidation strategies, they don't ablate the actual architecture design choices of the MEA module itself.

These ablations would provide important insights into the method's key design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Number of Experts Ablation
- **Ablated Part**: Number and types of experts in MEM module
- **Action**: REPLACE
- **Replacement**: 
  - Two experts (full-context + category)
  - Two experts (attribute + category)
  - Four experts (adding spatial relationship expert)
- **Metrics**: mIoU, R@1, IoU@0.25, R@1, IoU@0.5

### MEA Architecture Ablation
- **Ablated Part**: Architecture of the MEA module
- **Action**: REPLACE
- **Replacement**: 
  - Single layer MLP
  - Multi-layer transformer
  - Graph neural network
- **Metrics**: mIoU, R@1, IoU@0.25, R@1, IoU@0.5

</div>