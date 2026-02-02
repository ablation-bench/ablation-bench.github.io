<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Lattice_Convolutional_Networks_for_Learning_Ground_States_of_Quantum_Many_Body_Systems

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Lattice Convolutional Networks for Learning Ground States of Quantum Many-Body Systems" proposes LCN, a novel architecture for learning ground states on various lattice structures, including non-square ones. The core idea is to convert non-square lattices into grid-like augmented lattices using operations like augmentation (adding virtual vertices), boundary alignment, and periodic padding, allowing the application of regular convolutions. The network architecture also incorporates SE-Non-Local layers, combining Squeeze-and-Excitation and Non-local blocks with skip connections.

The paper includes several ablation studies:
1.  **Mask Operation (Appendix K.1):** Compares performance with and without the mask operation on Kagome 36.
2.  **Periodic Padding vs Zero Padding (Appendix F):** Demonstrates the importance of periodic padding on Honeycomb, Triangular, and Kagome lattices.
3.  **Regular Kernel vs Special Kernel (Table 2 & 3):** Compares using regular 3x3 kernels on augmented lattices against specially designed kernels on original lattices. This indirectly supports the augmentation idea but doesn't isolate the effect of the virtual vertices themselves.
4.  **Network Architecture Components (Table 4):** Shows the contribution of SE blocks and Non-local blocks to performance on Kagome 36 and 108, comparing Residual only, Residual+SE, Residual+Nonlocal, and Residual+SE+Nonlocal.
5.  **GNN with/without Sublattice Encoding (Table 11):** Shows the necessity of hand-crafted encoding for the GNN baseline.

Based on the method description and existing ablations, two important missing ablation studies are:

1.  **Ablation of Augmented Lattices (Virtual Vertices):** The paper's central claim for handling non-square lattices is the augmentation step, specifically adding virtual vertices to create a grid-like structure for regular convolutions. While Table 2 compares the *overall approach* (regular kernel on augmented lattice) to special kernels on original lattices, it doesn't isolate the contribution of the *virtual vertices themselves*. A direct ablation would involve applying the regular convolution mechanism (including BA and PP) to the non-square lattices *without* adding the virtual vertices. This would directly test if the virtual vertices are necessary for the regular convolution approach to work effectively on these lattices.
2.  **Ablation of Skip Connection in SE-Non-Local Layer:** The SE-Non-Local layer is a key building block of the LCN architecture, combining several components with a skip connection. Table 4 ablates the SE and Non-local blocks, showing their individual contributions. However, the skip connection itself is a standard and crucial component in modern deep networks (like ResNets) for enabling training of deeper models and improving performance. Ablating this skip connection within the proposed SE-Non-Local layer would demonstrate its importance to the network's ability to learn the wave function effectively.

These two ablations are important because they directly test core components of the proposed LCN method: the lattice augmentation strategy for non-square lattices and the structure of the main network building block. They would provide clearer evidence for the necessity and effectiveness of these specific design choices. I rank the ablation of augmented lattices as slightly more important as it pertains to the primary novelty of handling non-square lattices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Augmented Lattices
- **Ablated Part**: Augmented Lattices (Virtual Vertices)
- **Action**: REMOVE
- **Metrics**: Energy per site

### Ablation of Skip Connection in SE-Non-Local Layer
- **Ablated Part**: Skip connection within the SE-Non-Local Layer
- **Action**: REMOVE
- **Metrics**: Energy per site

</div>