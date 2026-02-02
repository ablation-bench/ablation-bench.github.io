<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Hierarchical_Object_Oriented_POMDP_Planning_for_Object_Rearrangement

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a novel Hierarchical Object-Oriented POMDP Planner (HOO-POMDP) for solving multi-object rearrangement problems in partially observable, multi-room environments. The approach decomposes the complex task into a high-level abstract POMDP planner for generating sub-goals and low-level policies for execution. The paper evaluates the system on varying numbers of objects, rooms, and problem types in AI2-THOR simulated environments with promising results.

The ablation study in the paper compares the performance of the HOO-POMDP planner with different levels of information and difficulty of problems, as well as an ablation on hierarchy. The results show that the HOO-POMDP planner outperforms the baselines in terms of success rate and efficiency.

However, there are some missing ablation studies that could provide further insights into the performance of the HOO-POMDP planner. For example, it would be interesting to see how the planner performs with different object detectors or different levels of partial observability. Additionally, an ablation study on the importance of the hierarchical planning approach could provide more insights into the benefits of this approach.

Based on the paper, I suggest the following two missing ablation studies:

1. **Ablation on object detector**: This ablation study would evaluate the performance of the HOO-POMDP planner with different object detectors, such as a perfect detector or a detector with varying levels of accuracy. This would help to understand the impact of object detection accuracy on the planner's performance.
2. **Ablation on hierarchical planning**: This ablation study would evaluate the performance of the HOO-POMDP planner with and without hierarchical planning. This would help to understand the benefits of the hierarchical planning approach and how it contributes to the planner's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Object Detector
- **Ablated Part**: object detector
- **Action**: REPLACE
- **Replacement**: 
  - perfect detector
  - detector with 50% accuracy
  - detector with 25% accuracy
- **Metrics**: success rate, efficiency

### Ablation on Hierarchical Planning
- **Ablated Part**: hierarchical planning
- **Action**: REMOVE
- **Metrics**: success rate, efficiency

</div>