<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Emergent_Mixture_of_Experts__Can_Dense_Pre_trained_Transformers_Benefit_from_Emergent_Modular_Structures_

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Emergent Mixture-of-Experts: Can Dense Pre-trained Transformers Benefit from Emergent Modular Structures?" proposes Emergent Mixture-of-Experts (EMoE), a method to leverage implicit modular structures found in pre-trained dense transformers during fine-tuning. EMoE is constructed by partitioning the Feed-Forward Network (FFN) layers into experts based on clustering the FFN's key vectors and using an "avg-k" gating mechanism derived from these clustered keys. A key claim is that this approach, without adding parameters, improves generalization by mitigating negative transfer.

The paper includes several ablation studies in Section 5.2 and Appendix A.5.2. These ablations investigate:
1.  Comparing clustering-based expert construction with random construction, showing clustering is superior (Table 4, Table 17).
2.  Exploring different numbers of experts (N) and top-k values, demonstrating robustness to these hyperparameters (Figure 5, Table 19).
3.  Testing applying EMoE to different sets of layers (Table 19).
4.  Comparing the proposed "avg-k" gating with a learned gating mechanism (EMoE-learn), showing avg-k is often better or more stable (Tables 1, 2, 3, Figure 5, Figure 6, Figure 8).
5.  Analyzing the effect of EMoE during training vs. inference and showing it helps by masking neurons with negative transfer effects (Section 5.1, Table 16, Table 17).
6.  Evaluating performance with varying training data fractions, suggesting improved data efficiency (Figure 7, Table 20).

While these ablations cover important aspects like the necessity of clustering and the comparison with a learned gate, there are still opportunities to further probe the core components of EMoE: the specific clustering method used and the details of the non-learned gating mechanism derived from the clustered structure.

Specifically, the paper uses a particular "constrained clustering" method. An ablation exploring whether other standard clustering algorithms yield similar benefits would strengthen the claim that it's the *emergent structure* identified by clustering, rather than the specifics of this one algorithm, that is beneficial.

Furthermore, the "avg-k" gating is a specific design choice: deriving gate weights by averaging expert keys and using a binary Top-K selection. While compared to a learned gate, it's not compared to other non-learned or differently derived gating strategies that still leverage the clustered structure. Exploring alternative ways to derive the gate from the clustered experts could provide deeper insight into *how* the emergent modularity is utilized for routing.

Based on this analysis, I suggest the following two missing ablation studies, focusing on the core mechanisms of expert construction and gating derivation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Clustering Method
- **Ablated Part**: The specific constrained clustering method used to partition FFN key vectors into experts.
- **Action**: REPLACE
- **Replacement**: 
  - Standard K-Means
  - Spectral Clustering
- **Metrics**: Average GLUE ID Accuracy, GLUE-X OOD Friedman Rank

### Ablation: Gating Derivation from Experts
- **Ablated Part**: The method of deriving gating weights by averaging expert key vectors (Avg(K^i, dim=0)) for the avg-k gate.
- **Action**: REPLACE
- **Replacement**: 
  - Centroid of Expert Keys
  - Average of Expert Values
  - Random Initialization (non-learned gate)
- **Metrics**: Average GLUE ID Accuracy, GLUE-X OOD Friedman Rank

</div>