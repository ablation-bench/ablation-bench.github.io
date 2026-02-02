<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Memory_Proxy_Maps_for_Visual_Navigation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Memory Proxy Maps for Visual Navigation" presents a novel approach to visual navigation using a three-tiered agent with a memory proxy map (MPM) and a waypoint network (WayNet). The MPM is a self-supervised latent space that serves as a simplified memory, approximating what the agent has seen. The WayNet outputs intermediate subgoals, or waypoints, imitating human waypoint selection during local navigation. The paper demonstrates that recording observations in this learned latent space is an effective and efficient memory proxy that can remove the need for graphs and odometry in visual navigation tasks.

The paper already presents some ablation studies, including the effect of different network architectures on the memory proxy map and the full hierarchy's effect on image-goal task performance. However, there are still some missing ablation studies that could provide further insights into the method's performance.

One potential missing ablation study is the effect of the MPM's size on the navigation performance. The paper uses a fixed-size MPM, but it would be interesting to see how the performance changes with different MPM sizes. This could help understand the trade-off between memory usage and navigation performance.

Another potential missing ablation study is the effect of the WayNet's architecture on the navigation performance. The paper uses a modified Resnet-18 architecture, but it would be interesting to see how other architectures perform. This could help understand the importance of the WayNet's architecture on the overall navigation performance.

Additionally, it would be interesting to see an ablation study on the effect of the number of waypoints on the navigation performance. The paper uses a fixed number of waypoints, but it would be interesting to see how the performance changes with different numbers of waypoints. This could help understand the trade-off between the number of waypoints and navigation performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: MPM size
- **Action**: REPLACE
- **Replacement**: 
  - 128
  - 256
  - 512
- **Metrics**: success rate, SPL

### Ablation B
- **Ablated Part**: WayNet architecture
- **Action**: REPLACE
- **Replacement**: 
  - Resnet-18
  - Resnet-50
  - DenseNet-121
- **Metrics**: success rate, SPL

### Ablation C
- **Ablated Part**: number of waypoints
- **Action**: REPLACE
- **Replacement**: 
  - 3
  - 5
  - 10
- **Metrics**: success rate, SPL

</div>