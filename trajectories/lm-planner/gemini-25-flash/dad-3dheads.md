<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/dad-3dheads

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The DAD-3DNet model utilizes a multi-component loss function comprising a Shape+Expression Loss ($L_{3D}$), a Reprojection Loss ($L_{proj}$), a Landmark Regression Loss ($L_1$), and a Gaussian Heatmap Loss ($L_{AWing}$). The paper highlights that ablation studies demonstrate the importance of each of these components. Therefore, a crucial set of ablation studies involves systematically removing or modifying these loss terms to understand their individual contributions to the model's performance on 3D head alignment and reconstruction tasks.

Specifically, removing the $L_{3D}$ loss will evaluate the necessity of direct supervision on the normalized 3D shape and expression parameters. Removing the $L_{proj}$ loss will assess the impact of the reprojection constraint on learning accurate pose and overall 3D mesh alignment. Ablating the 2D landmark losses ($L_1$ and $L_{AWing}$) will reveal the contribution of the multi-task learning approach, where the 2D landmark prediction branch potentially aids the 3D reconstruction task through shared features or regularization. Finally, varying the relative weights of the primary 3D losses ($L_{3D}$ and $L_{proj}$) will explore the sensitivity of the model's performance to the balance between optimizing for intrinsic shape/expression accuracy and extrinsic pose/projection accuracy.

The proposed ablation studies are designed to isolate the effects of these key components of the objective function. The metrics chosen for evaluation are those reported in the paper across various tasks (3D shape reconstruction, 3D head pose estimation, and 3D dense head alignment), ensuring that the impact of each ablation can be measured using the established benchmarks and evaluation protocols.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No Shape+Expression Loss
- **Ablated Part**: Shape+Expression Loss (L_3D)
- **Action**: REMOVE
- **Metrics**: Median(mm), Mean(mm), Std(mm), Angle error (degrees), Reprojection NME, Z_n Accuracy

### Ablation: No Reprojection Loss
- **Ablated Part**: Reprojection Loss (L_proj)
- **Action**: REMOVE
- **Metrics**: Median(mm), Mean(mm), Std(mm), Angle error (degrees), Reprojection NME, Z_n Accuracy

### Ablation: No 2D Landmark Supervision
- **Ablated Part**: 2D Landmark Regression Loss (L_1) and Gaussian Heatmap Loss (L_AWing)
- **Action**: REMOVE
- **Metrics**: Median(mm), Mean(mm), Std(mm), Angle error (degrees), Reprojection NME, Z_n Accuracy

### Ablation: Vary L_3D and L_proj Weights
- **Ablated Part**: Weights of Shape+Expression Loss (lambda_1) and Reprojection Loss (lambda_3)
- **Action**: REPLACE
- **Replacement**: 
  - {'lambda_1': 50.0, 'lambda_3': 0.05}
  - {'lambda_1': 50.0, 'lambda_3': 0.5}
  - {'lambda_1': 5.0, 'lambda_3': 0.05}
- **Metrics**: Median(mm), Mean(mm), Std(mm), Angle error (degrees), Reprojection NME, Z_n Accuracy

</div>