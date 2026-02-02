<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Artificial_Kuramoto_Oscillatory_Neurons

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Artificial Kuramoto Oscillatory Neurons" introduces AKOrN, a novel neural network building block based on the Kuramoto model of coupled oscillators. The core idea is to use dynamical, oscillatory neurons (vectors on a hypersphere) that update iteratively based on interactions with other neurons (Jij term), a natural frequency term (Ωi), and conditional stimuli (ci). The updates involve a projection operator (Proj) and normalization (Π) to keep neurons on the unit sphere. The network consists of blocks with a Kuramoto layer and a readout module, processing inputs iteratively for T steps.

The paper presents several ablation studies and analyses, primarily in Appendix A and Section 6:
1.  **Projection Operator (A.1):** Evaluates performance with and without the projection operator.
2.  **Kuramoto vs. Residual Update (A.2):** Compares the full Kuramoto update rule (with Proj and Π) against a standard residual update. This is a crucial comparison showing the benefit of the core dynamics.
3.  **Number of Rotating Dimensions (N) (A.3):** Investigates the impact of the dimensionality of the oscillator vectors.
4.  **Bias Term C and Norm-Taking m (A.4):** Studies the contribution of the conditional stimuli C and the norm-based readout m.
5.  **Natural Frequency Term Ω (D.3.2):** Shows the effect of removing Ω on the energy landscape and energy-based voting in Sudoku.
6.  **Symmetric Constraint (D.4):** Compares AKOrN (asymmetric J, includes Ω and C) to symmetric models (Energy Transformer, Symmetrized AKOrN) in Sudoku.
7.  **Test-time Extension of Steps (6.2):** Analyzes the effect of increasing the number of Kuramoto steps during inference, particularly for Sudoku OOD.
8.  **Energy-based Voting (6.2):** Demonstrates how selecting predictions based on energy improves Sudoku performance.

While these studies cover several key aspects, some important design choices and hyperparameters related to the core iterative dynamics and state initialization are not fully ablated or compared against alternatives used in the literature.

Two important missing ablations are:

1.  **Effect of the Number of Training Steps (T):** The paper highlights the iterative nature and shows the benefit of *test-time* extension of steps (Teval) in Sudoku. However, the impact of the number of Kuramoto steps performed *during training* (T) on the final performance across tasks is not systematically explored. This is a fundamental hyperparameter governing the depth of the unrolled dynamics during learning. Varying T during training would reveal how much iteration is necessary or beneficial for learning the desired representations and solving tasks.
2.  **Oscillator Initialization Strategy (X(0)):** The paper mentions different initialization options for the initial oscillator states X(0) (C(0), learned embedding, random, mixture) but primarily uses random initialization on the sphere in experiments (except for fixed digits in Sudoku). A comparison of different initialization strategies for X(0) (e.g., random on sphere vs. learned constant vs. initialized from C(0)) would clarify the importance of the initial state and the specific random initialization choice.

These two ablations are crucial for understanding the contribution of the iterative dynamics depth during training and the role of the initial state of the oscillators, both of which are core to the AKOrN model's operation. I will prioritize these two for the suggestions.

For the metrics, I will use those reported in the paper for the relevant tasks: FG-ARI and MBO for object discovery (e.g., CLEVRTex), and Board Accuracy (ID/OOD) for Sudoku.

For the number of training steps (T), the paper uses T=8 or T=16. I will suggest testing a range including smaller (e.g., 4) and potentially larger values.
For the initialization strategy, I will suggest testing the alternatives mentioned in the paper against the default random initialization.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Effect of Training Steps T
- **Ablated Part**: Number of internal Kuramoto update steps (T) during training
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 8
  - 16
  - 32
- **Metrics**: Board Accuracy (OOD), FG-ARI, MBO

### Oscillator Initialization Strategy
- **Ablated Part**: Initialization strategy for the initial oscillator states X(0)
- **Action**: REPLACE
- **Replacement**: 
  - random uniform on sphere
  - learned constant vector
  - initialized from C(0)
- **Metrics**: Board Accuracy (OOD), FG-ARI, MBO

</div>