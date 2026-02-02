<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Poisoning_with_A_Pill__Circumventing_Detection_in_Federated_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a three-stage method to enhance poisoning attacks in federated learning through a "pill" (subnet) approach. The key components are:

1. Pill construction - Using dynamic subnetwork search to identify critical parameters
2. Pill poisoning - Applying existing attacks to the selected pill
3. Pill injection - Inserting the poisoned pill with two-step adjustment

The paper already includes several ablation studies:
- Testing different dynamic patterns for pill search (PATTERN1-6)
- Ablating the two-step adjustment (SimAdjust and DistAdjust)
- Testing different pill search algorithms (max vs min)
- Testing with different proportions of malicious clients
- Testing on different datasets and architectures

However, I notice two important missing ablations:

1. The impact of pill size - The paper uses a fixed pill blueprint with one neuron/channel per layer except the last two layers. Testing different pill sizes would help understand the trade-off between stealthiness and effectiveness.

2. The impact of pill location - The current method focuses on finding important parameters, but doesn't ablate whether the location of the pill in the network matters (e.g. early vs late layers).

These ablations would provide deeper insights into the key design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Pill Size Ablation
- **Ablated Part**: size of the pill blueprint
- **Action**: REPLACE
- **Replacement**: 
  - 0.5x current size
  - 2x current size
  - 4x current size
- **Metrics**: error rate, cosine similarity score, distance score

### Pill Location Ablation
- **Ablated Part**: layers where pill is inserted
- **Action**: REPLACE
- **Replacement**: 
  - only early layers (first 1/3)
  - only middle layers (middle 1/3)
  - only late layers (last 1/3)
- **Metrics**: error rate, cosine similarity score, distance score

</div>