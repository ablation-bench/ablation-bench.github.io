<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/TIB__Detecting_Unknown_Objects_via_Two_Stream_Information_Bottleneck

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "TIB: Detecting Unknown Objects via Two-Stream Information Bottleneck" introduces a novel method for unsupervised out-of-distribution object detection (OOD-OD) using a Two-Stream Information Bottleneck (TIB) approach. The method consists of a standard Information Bottleneck (IB) and a Reverse Information Bottleneck (RIB) to enhance the discrimination ability of object detectors by generating simulative OOD features. The paper includes several ablation studies, such as the analysis of the IB and RIB branches, the number of branches in the mixture of information bottlenecks (MIB), and the impact of hyper-parameters.

However, there are some potential missing ablation studies that could provide further insights into the method's performance. One such missing ablation is the impact of the backbone network on the performance of the TIB method. The paper uses ResNet-50 as the backbone, but it would be valuable to explore how different backbone architectures affect the performance, especially since the backbone is crucial for feature extraction. Another missing ablation is the effect of the gating mechanism used in the mixture of information bottlenecks. The paper mentions the use of a gating operation to aggregate information from different IB branches, but it does not explore the impact of this design choice on the overall performance.

These missing ablations are important because they can help understand the robustness and generalizability of the TIB method across different settings and design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Backbone Network Ablation
- **Ablated Part**: Backbone network architecture
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-101
  - EfficientNet-B0
  - MobileNetV2
- **Metrics**: FPR95, AUROC, mAP

### Gating Mechanism Ablation
- **Ablated Part**: Gating mechanism in the mixture of information bottlenecks
- **Action**: REPLACE
- **Replacement**: 
  - Simple mean operation
  - Max pooling
- **Metrics**: FPR95, AUROC, mAP

</div>