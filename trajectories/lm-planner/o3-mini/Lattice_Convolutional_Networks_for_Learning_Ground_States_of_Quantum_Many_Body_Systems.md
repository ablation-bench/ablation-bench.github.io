<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Lattice_Convolutional_Networks_for_Learning_Ground_States_of_Quantum_Many_Body_Systems

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first proposed ablation study targets the lattice augmentation module—a core innovation in LCN that inserts virtual vertices to convert non-square lattices into grid-like augmented lattices. Although the paper compares regular kernel designs (which use the augmented lattice) with special kernels on the original lattice, it does not explicitly ablate the augmentation operation itself. Removing the augmentation will reveal the direct effect of virtual vertex insertion on performance, particularly in terms of energy per site, ground state overlap, and convergence stability.

The second proposed ablation study examines whether integrating explicit, hand-crafted sublattice encoding (commonly required for GNNs) into LCN provides any additional benefits. Since one of the LCN’s claimed advantages is its ability to implicitly learn structure without prior physics knowledge, adding an explicit sublattice encoding (using various encoding schemes such as one-hot, sinusoidal, or learnable embeddings) can evaluate whether such domain-specific information further improves the network’s performance on metrics like energy per site, ground state overlap, and training convergence.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Lattice Augmentation
- **Ablated Part**: Lattice augmentation via virtual vertex insertion for converting non-square lattices into grid-like augmented lattices
- **Action**: REMOVE
- **Metrics**: energy per site, ground state overlap, convergence stability

### Incorporating Hand-crafted Sublattice Encoding
- **Ablated Part**: Implicit structure encoding by the network; adding explicit hand-crafted sublattice encoding
- **Action**: ADD
- **Replacement**: 
  - one-hot encoding
  - sinusoidal positional encoding
  - learnable embedding
- **Metrics**: energy per site, ground state overlap, training convergence

</div>