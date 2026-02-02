<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Local_Search_GFlowNets

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Local Search GFlowNets" introduces a novel approach to enhance the performance of Generative Flow Networks (GFlowNets) by incorporating local search techniques. The method involves three iterative steps: sampling trajectories, refining them using local search, and training the GFlowNets with the revised trajectories. The local search is guided by backward and forward policies, which help in exploring high-reward regions more effectively.

The paper includes several ablation studies, such as the comparison between deterministic and stochastic filtering strategies, the effect of the number of revision steps (I) and candidate samples (M), and the impact of the number of destruction and reconstruction steps (K). These studies aim to understand the contribution of different components and hyperparameters to the overall performance of the method.

However, there are some missing ablation studies that could provide further insights into the method's performance. One potential ablation study could involve the removal of the backward policy (P<sup>B</sup>) to assess its impact on the local search process. Since the backward policy is crucial for backtracking in the local search, understanding its contribution could highlight its importance in the method. Another possible ablation study could involve replacing the deterministic filtering strategy with a purely random acceptance strategy to evaluate the role of the filtering mechanism in the local search process.

These ablation studies would help in attributing the method's performance to its major components and provide a deeper understanding of the local search mechanism's effectiveness in improving GFlowNets.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Backward policy (P<sup>B</sup>) in the local search process
- **Action**: REMOVE
- **Metrics**: accuracy, number of modes discovered, top 100 reward, top 100 diversity

### Ablation Study 2
- **Ablated Part**: Deterministic filtering strategy in the local search process
- **Action**: REPLACE
- **Replacement**: 
  - random acceptance strategy
- **Metrics**: accuracy, number of modes discovered, top 100 reward, top 100 diversity

</div>