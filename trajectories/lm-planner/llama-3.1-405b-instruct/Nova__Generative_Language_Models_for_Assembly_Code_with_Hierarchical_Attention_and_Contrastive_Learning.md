<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Nova__Generative_Language_Models_for_Assembly_Code_with_Hierarchical_Attention_and_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Nova: Generative Language Models for Assembly Code with Hierarchical Attention and Contrastive Learning" presents a novel approach to developing a generative language model for assembly code. The authors propose a hierarchical attention mechanism that captures the semantics of assembly code at three levels of granularity: intra-instruction, preceding-instruction, and inter-instruction. Additionally, they introduce contrastive learning objectives to train the model to learn assembly optimization.

The paper demonstrates the effectiveness of the proposed approach through experiments on two downstream tasks: binary code decompilation and binary code similarity detection. The results show that Nova outperforms existing techniques on both tasks, achieving up to 14.84-21.58% higher Pass@1 and Pass@10 on binary code decompilation and up to 6.17% higher Recall@1 on binary code similarity detection.

To further evaluate the robustness of the proposed approach, we suggest two missing ablation studies:

1. **Ablation study on the impact of hierarchical attention on different layers**: The paper applies hierarchical attention to half of the attention heads at each layer. It would be interesting to investigate the impact of applying hierarchical attention to different layers or all layers.
2. **Ablation study on the effect of contrastive learning objectives on different optimization levels**: The paper uses two contrastive learning objectives: functionality contrastive learning and optimization contrastive learning. It would be useful to investigate the effect of these objectives on different optimization levels (e.g., O0, O1, O2, O3).

These ablation studies can provide a deeper understanding of the proposed approach and its components, which can help to identify potential areas for improvement and inform future research directions.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: Hierarchical Attention on Different Layers
- **Action**: REPLACE
- **Replacement**: 
  - Apply hierarchical attention to all layers
  - Apply hierarchical attention to different layers
- **Metrics**: Pass@1, Pass@10, Recall@1

### Ablation Study 2
- **Ablated Part**: Contrastive Learning Objectives on Different Optimization Levels
- **Action**: REMOVE
- **Metrics**: Pass@1, Pass@10, Recall@1

</div>