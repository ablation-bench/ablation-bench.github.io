<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Deep_PDE_Solvers_for_Subgrid_Modelling_and_Out_of_Distribution_Generalization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Deep PDE Solvers for Subgrid Modelling and Out-of-Distribution Generalization" presents a novel architecture for solving PDEs in climate and weather modeling, focusing on subgrid modeling and out-of-distribution (OOD) generalization. The architecture is designed to respect physical constraints and ensure numerical stability. The paper includes experiments comparing the proposed model with baseline models (fully connected and convolutional neural networks) and an ablation study on data complexity.

The existing ablation study in the paper focuses on data complexity, examining how the model performs with data of varying complexity. However, there are no ablation studies on the architectural components of the proposed model itself. The model is built on four theoretically desirable properties: locality, stability, linearity, and memory-less recurrence. Each of these properties is integrated into the model's architecture, and their impact on the model's performance is crucial to understand.

A missing ablation study could involve examining the impact of the stability constraint, which is implemented by bounding the model's parameters using a scaled sigmoid function. This constraint ensures that the model's parameters remain within the stability region of the PDE, which is critical for learning the physical process accurately. Ablating this component could reveal its importance in maintaining the model's performance, especially in OOD scenarios.

Another potential ablation study could focus on the memory-less property, which ensures that the model's layers are identical, reflecting the time-independence of the differential operator. This property might be crucial for the model's ability to generalize across different time steps and initial conditions. Ablating this property could help understand its role in the model's success in OOD generalization.

These ablation studies would provide insights into the contributions of these architectural components to the model's overall performance and its ability to generalize to OOD data.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Stability Constraint
- **Ablated Part**: Stability constraint implemented by bounding model parameters with a scaled sigmoid function
- **Action**: REMOVE
- **Metrics**: relative L2 error, training error, test error, OOD error

### Ablation of Memory-less Property
- **Ablated Part**: Memory-less property ensuring identical layers in the model
- **Action**: REMOVE
- **Metrics**: relative L2 error, training error, test error, OOD error

</div>