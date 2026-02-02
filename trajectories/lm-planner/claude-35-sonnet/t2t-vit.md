<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/t2t-vit

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, T2T-ViT has two main novel components that contribute to its performance:

1. The T2T module that progressively tokenizes images through multiple iterations of re-structurization and soft split operations. This is a key innovation that helps capture local structure.

2. The deep-narrow backbone architecture design that reduces redundancy while maintaining performance.

The most important ablation studies should focus on:

1. Testing the effectiveness of the T2T module by comparing against simple tokenization
2. Evaluating the impact of progressive tokenization iterations
3. Analyzing the importance of overlapping in soft split
4. Validating the benefits of the deep-narrow architecture
5. Testing different transformer variants in the T2T module

I'll rank these in order of importance and specify the exact experiments.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### T2T Module Ablation
- **Ablated Part**: T2T module
- **Action**: REPLACE
- **Replacement**: 
  - Simple tokenization (16x16 patches)
  - Single T2T iteration
  - CNN-based tokenization
- **Metrics**: Top-1 accuracy, Top-5 accuracy, Parameters (M), MACs (G)

### Soft Split Overlap
- **Ablated Part**: Overlapping in soft split operation
- **Action**: REPLACE
- **Replacement**: 
  - No overlap (s=0)
  - Small overlap (s=1)
  - Large overlap (s=4)
- **Metrics**: Top-1 accuracy, Top-5 accuracy, MACs (G)

### Architecture Depth
- **Ablated Part**: Deep-narrow architecture
- **Action**: REPLACE
- **Replacement**: 
  - Shallow-wide (fewer layers, more channels)
  - Balanced (equal layers and channels)
  - Ultra-deep (more layers, fewer channels)
- **Metrics**: Top-1 accuracy, Top-5 accuracy, Parameters (M), MACs (G)

### T2T Transformer Type
- **Ablated Part**: Transformer layer in T2T module
- **Action**: REPLACE
- **Replacement**: 
  - Standard Transformer
  - Performer
  - Linear Transformer
- **Metrics**: Top-1 accuracy, Top-5 accuracy, Memory usage, Training time

### Position Embedding
- **Ablated Part**: Sinusoidal position embedding
- **Action**: REPLACE
- **Replacement**: 
  - Learnable position embedding
  - Relative position encoding
  - No position embedding
- **Metrics**: Top-1 accuracy, Top-5 accuracy

</div>