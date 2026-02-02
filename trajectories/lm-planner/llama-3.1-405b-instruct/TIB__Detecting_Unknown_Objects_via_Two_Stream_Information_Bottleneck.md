<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/TIB__Detecting_Unknown_Objects_via_Two_Stream_Information_Bottleneck

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "TIB: Detecting Unknown Objects via Two-Stream Information Bottleneck" proposes a method for unsupervised out-of-distribution object detection (OOD-OD) using a two-stream information bottleneck (TIB) approach. The TIB consists of a standard information bottleneck (IB) and a dedicated reverse information bottleneck (RIB). The IB is used to extract instance-level features, while the RIB is used to generate simulative OOD features by reversing the optimization objective of the standard IB.

The paper presents several ablation studies to demonstrate the effectiveness of the proposed method. However, there are some missing ablation studies that could provide further insights into the method's performance.

One potential missing ablation study is an analysis of the impact of the number of IB branches on the performance of the TIB. The paper mentions that using 8 IB branches achieves the best performance, but it would be interesting to see how the performance changes with different numbers of IB branches.

Another potential missing ablation study is an analysis of the effect of the hyper-parameter β on the performance of the TIB. The paper mentions that β is set to 0.0001, but it would be interesting to see how the performance changes with different values of β.

Additionally, it would be interesting to see an ablation study on the impact of the RIB on the performance of the TIB. The paper mentions that the RIB is used to generate simulative OOD features, but it would be interesting to see how the performance changes without the RIB.

Overall, the paper presents a promising approach for OOD-OD, and further ablation studies could provide valuable insights into the method's performance and limitations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Number of IB branches
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
  - 6
  - 8
  - 10
- **Metrics**: FPR95, AUROC, mAP

### Ablation Study 2
- **Ablated Part**: Hyper-parameter β
- **Action**: REPLACE
- **Replacement**: 
  - 0.001
  - 0.0001
  - 1e-05
- **Metrics**: FPR95, AUROC, mAP

### Ablation Study 3
- **Ablated Part**: RIB
- **Action**: REMOVE
- **Metrics**: FPR95, AUROC, mAP

</div>