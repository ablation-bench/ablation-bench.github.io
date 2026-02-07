<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Memory_Proxy_Maps_for_Visual_Navigation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents a hierarchical (feudal) navigation approach with three main components:
1. High-level manager (HLM) with Memory Proxy Map (MPM)
2. Mid-level manager with Waypoint Network (WayNet) 
3. Low-level worker (LLW) with action classifier

The paper already includes ablations on:
1. Different types of MPM representations (binary vs gaussian)
2. Different input modalities for WayNet (RGB vs RGBD)
3. Different approaches for the low-level worker (deterministic vs classifier)

However, there are two important missing ablations that could provide valuable insights:

1. The most critical missing ablation is on the feature extractor used for the Memory Proxy Map. While they show qualitative comparisons between different feature extractors (SMoG, MoCo, ResNet, Swav) in Fig. 4, they don't provide quantitative results on how these different feature extractors affect the final navigation performance.

2. The second important missing ablation is on the hierarchical structure itself. While they use a three-tier architecture, they don't evaluate whether all three levels are necessary or if a simpler two-tier architecture could achieve similar performance. This is particularly important since most prior work uses two-tier architectures.

I'll focus on these two ablations as they target core components of the method and could provide important insights about the method's design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Feature Extractor Ablation
- **Ablated Part**: SMoG feature extractor used in the Memory Proxy Map
- **Action**: REPLACE
- **Replacement**: 
  - MoCo
  - ResNet-18
  - Swav
- **Metrics**: Success Rate, SPL

### Hierarchy Level Ablation
- **Ablated Part**: Three-tier hierarchical structure
- **Action**: REPLACE
- **Replacement**: 
  - Two-tier (remove mid-level)
  - Two-tier (remove high-level)
- **Metrics**: Success Rate, SPL

</div>