<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/NextBestPath__Efficient_3D_Mapping_of_Unseen_Environments

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "NextBestPath: Efficient 3D Mapping of Unseen Environments" introduces a novel method (NBP) for active 3D mapping that predicts long-term goals and obstacle maps. The method consists of a Mapping Progress Encoder, a Coverage Gain Decoder, and an Obstacle Map Decoder, trained using online data collection, data augmentation (Dijkstra sub-paths), curriculum learning, and multi-task learning.

The paper includes several ablation studies in Section 5.3 and Appendix C:
1.  **Spatial range of long-term goal:** Evaluates the impact of the input crop size for the encoder.
2.  **Oracle obstacle map:** Compares using the predicted obstacle map vs. the ground truth obstacle map during inference.
3.  **Multi-task training:** Compares joint training of the two decoders vs. separate training.
4.  **Inference Strategy:** Compares updating the long-term goal upon path completion vs. at each step.

These ablations provide insights into the spatial scale of prediction, the accuracy of the obstacle map prediction, the benefit of multi-task learning, and the goal update frequency during inference. The authors conclude that the value map prediction is the main bottleneck.

However, several key components and training strategies of the NBP method are not ablated. Based on the method description, two important missing ablation studies are:

1.  **Impact of the Historical Trajectory Input:** The Mapping Progress Encoder takes both projected point cloud images and a historical trajectory image as input. The paper doesn't show the individual contribution of these inputs. Ablating the historical trajectory input would reveal whether the model primarily relies on the current scene reconstruction state (from the point cloud) or if the history of visited locations provides significant additional value for predicting coverage gain and obstacles. This is a fundamental aspect of the encoder's input representation.
2.  **Impact of Data Augmentation (Dijkstra Sub-paths):** The paper highlights the data augmentation technique using Dijkstra sub-paths as a way to efficiently generate training data from a single trajectory. This technique is presented as a key part of the training procedure. An ablation study removing this specific data augmentation would demonstrate its effectiveness and necessity for achieving the reported performance.

These two ablations are important because they investigate core aspects of the model's input representation and its training data generation strategy, respectively, which are not covered by the existing ablations. They would help attribute the performance gains to these specific design choices. I will prioritize the ablation of the encoder input as it directly relates to the model architecture's information processing. The metrics used in the paper's ablations ("Final Cov." and "AUCs") should be used for consistency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No Trajectory Input
- **Ablated Part**: Historical trajectory image input to the Mapping Progress Encoder
- **Action**: REMOVE
- **Metrics**: Final Cov., AUCs

### Ablation: No Sub-path Augmentation
- **Ablated Part**: Data augmentation using Dijkstra sub-paths during training
- **Action**: REMOVE
- **Metrics**: Final Cov., AUCs

</div>