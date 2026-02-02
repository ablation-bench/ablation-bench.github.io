<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/3d-registration-with-maximal-cliques

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five key ablation studies that isolate the contributions of MAC’s critical components. The most central contribution of the paper is the relaxation of the maximum clique constraint; therefore, our first study investigates how replacing the maximal clique search by the traditional maximum clique approach affects registration performance. The second study examines the compatibility graph construction since the paper offers two approaches: the Second Order Graph (SOG) and the First Order Graph (FOG). Changing this component will reveal its impact on clique quality and efficiency. Next, we assess the benefit of the node‐guided clique selection, where the method filters the large set of maximal cliques; removing this step will help us quantify its influence on hypothesis quality and computational efficiency. The fourth ablation tests the SVD-based hypothesis generation by comparing the weighted SVD strategy with the instance‐equal SVD, thus isolating the contribution of leveraging correspondence weights. Lastly, we remove the normal consistency filtering step in the clique selection process to understand its improvement on eliminating spurious correspondences. Together, these ablations will measure the impact on key metrics such as registration recall, rotation error (RE), and translation error (TE), which are crucial as reported in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Maximal vs Maximum Clique
- **Ablated Part**: Clique selection strategy; comparing the relaxed use of maximal cliques versus enforcing the maximum clique constraint
- **Action**: REPLACE
- **Replacement**: 
  - maximum clique
  - maximal clique
- **Metrics**: registration recall, rotation error, translation error

### Graph Construction Method
- **Ablated Part**: Construction of the compatibility graph; comparing Second Order Graph (SOG) with First Order Graph (FOG)
- **Action**: REPLACE
- **Replacement**: 
  - SOG
  - FOG
- **Metrics**: registration recall, computation time, inlier count

### Node-Guided Clique Selection
- **Ablated Part**: The node-guided filtering of maximal cliques to select the best consensus sets
- **Action**: REMOVE
- **Metrics**: registration recall, computation time

### SVD Weighting Strategy
- **Ablated Part**: Hypothesis generation step; comparing the use of weighted SVD against instance-equal SVD
- **Action**: REPLACE
- **Replacement**: 
  - weighted SVD
  - instance-equal SVD
- **Metrics**: registration recall, rotation error, translation error, MAE, MSE

### Normal Consistency Filtering
- **Ablated Part**: The additional normal consistency check used during clique selection
- **Action**: REMOVE
- **Metrics**: registration recall, inlier count

</div>