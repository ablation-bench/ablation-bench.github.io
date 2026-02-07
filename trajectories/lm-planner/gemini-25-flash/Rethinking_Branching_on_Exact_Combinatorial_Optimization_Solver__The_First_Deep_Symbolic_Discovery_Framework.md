<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Rethinking_Branching_on_Exact_Combinatorial_Optimization_Solver__The_First_Deep_Symbolic_Discovery_Framework

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Rethinking Branching on Exact Combinatorial Optimization Solver: The First Deep Symbolic Discovery Framework" proposes Symb4CO, a framework for discovering compact, interpretable symbolic branching policies for MILP solvers. The method uses a deep sequential model to search for symbolic expressions based on a fixed set of 91 features, trained via reinforcement learning to maximize behavioral cloning accuracy against a strong branching expert.

The paper includes ablation studies on the choice of mathematical operators and constants (Table 6) and the length constraints and soft length prior (Table C10). It also compares the hybrid deployment strategy (Symb4CO for shallow nodes, RPB for deep nodes) against using Symb4CO for all layers (Table C13).

While these ablations cover aspects of the symbolic expression space and training hyperparameters, there are two key components of the Symb4CO framework that are central to its design and performance but are not thoroughly ablated:

1.  **The Input Features:** Symb4CO relies on a predefined set of 91 features derived from previous work. The paper highlights that the learned policies are compact and involve only a "small set of active features" (Section 3.2, Table 5). However, there is no systematic study on the importance of different feature subsets or types (e.g., static vs. dynamic, or specific groups of features like pseudocosts, constraint statistics, etc.). An ablation studying the impact of using different subsets of these features would directly test the necessity of the full feature set and help understand which features are most crucial for learning effective symbolic policies, aligning with the paper's emphasis on interpretability and efficiency.

2.  **The Fitness Measure / Imitation Target:** Symb4CO is trained using behavioral cloning to match the decisions of a Full Strong Branching (FSB) expert, using classification accuracy as the fitness measure. The task of branching variable selection is inherently a ranking problem (scoring candidates and picking the best). While behavioral cloning accuracy is a common approach, using a ranking-based loss function might be a more appropriate training signal for learning a scoring function. Ablating the fitness measure by replacing the classification accuracy with a ranking loss would investigate the impact of the learning objective on the quality of the learned symbolic policies and their end-to-end performance.

Based on their importance to the core mechanism and claims of the paper (feature importance for interpretability/compactness, and the learning signal for policy quality), I propose these two missing ablation studies. The feature ablation is slightly more fundamental as it concerns the input representation itself.

The metrics used in these ablations should be consistent with those reported in the paper's main results and existing ablations: Time (s), Nodes, Wins (for end-to-end solver performance), and Imitation Learning Accuracy (for the learning process).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Feature Subset Ablation
- **Ablated Part**: The set of 91 input features used for the symbolic policy.
- **Action**: REPLACE
- **Replacement**: 
  - Static features only
  - Dynamic features only
  - Subset of features used in learned policies (Table 5)
  - Subset based on feature categories (e.g., LP solution features, constraint features)
- **Metrics**: Time (s), Nodes, Wins, Imitation Learning Accuracy

### Fitness Function Ablation
- **Ablated Part**: Behavioral cloning accuracy (classification loss) used as the fitness measure.
- **Action**: REPLACE
- **Replacement**: 
  - Ranking loss (e.g., pairwise or listwise)
- **Metrics**: Time (s), Nodes, Wins, Imitation Learning Accuracy

</div>