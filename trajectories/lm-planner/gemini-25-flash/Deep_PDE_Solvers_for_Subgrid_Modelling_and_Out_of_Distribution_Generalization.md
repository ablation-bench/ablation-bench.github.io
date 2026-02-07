<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Deep_PDE_Solvers_for_Subgrid_Modelling_and_Out_of_Distribution_Generalization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel deep learning architecture for solving PDEs in a subgrid setting, specifically designed for climate and weather modeling challenges like out-of-distribution (OOD) generalization and respecting physical constraints. The architecture is motivated by properties of PDE solution operators, incorporating locality (via convolution), stability (via parameter bounding), linearity (in the data), and memory-less recurrence (shared weights).

The paper includes one ablation study (Section 5.3) which investigates the model's performance on data with varying Fourier spectra (data complexity), demonstrating its resilience compared to baselines. However, this ablation focuses on the data characteristics rather than the specific architectural components of the proposed model.

To understand which parts of the novel architecture contribute most to its claimed benefits (especially OOD generalization and physical constraint satisfaction), ablation studies on the architectural components themselves are crucial. Based on the paper's description, two key, theoretically motivated components stand out as important candidates for ablation:

1.  **The Stability Bounding Mechanism:** The paper explicitly bounds the learnable parameters using a scaled sigmoid function (`C_a * sigma(theta)`) derived from the PDE's stability constraint. This is a direct attempt to bake a physical/numerical property into the model. Ablating this mechanism would reveal its impact on stability, accuracy, and OOD performance.
2.  **The Fixed Laplacian Convolution Kernel:** The model uses a fixed, non-learnable kernel corresponding to the discrete Laplacian operator, with learnable parameters only scaling the output. This contrasts with standard convolutional networks where the kernel weights are fully learned. Ablating this by replacing the fixed kernel with a standard learnable convolutional kernel would test the hypothesis that using the PDE-inspired fixed kernel is beneficial.

These two ablations are missing from the current study and would provide valuable insights into the effectiveness of the proposed PDE-inspired architectural choices. The primary metric used in the paper is the relative L2 error, which should be used for these ablations as well, evaluated on training, in-distribution test, and OOD test data.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Stability Bounding
- **Ablated Part**: Scaled sigmoid function (C_a * sigma(theta)) used to bound parameters and enforce stability constraint
- **Action**: REPLACE
- **Replacement**: 
  - Identity (theta)
  - ReLU(theta)
- **Metrics**: Relative L2 error (Train), Relative L2 error (Test), Relative L2 error (OOD)

### Ablation: Fixed Laplacian Kernel
- **Ablated Part**: Fixed, non-learnable Laplacian convolution kernel (W_Lap,dim)
- **Action**: REPLACE
- **Replacement**: 
  - Learnable convolutional kernel of the same size
- **Metrics**: Relative L2 error (Train), Relative L2 error (Test), Relative L2 error (OOD)

</div>