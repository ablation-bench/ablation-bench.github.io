<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/simcse

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, SimCSE has several key components that warrant investigation through ablation studies:

1. The dropout mechanism is crucial for the unsupervised approach - it acts as minimal data augmentation and prevents representation collapse. Testing different dropout configurations is important.

2. For supervised SimCSE, the use of entailment pairs as positives and contradiction pairs as hard negatives is a key design choice.

3. The temperature parameter τ in the contrastive learning objective affects performance.

4. The choice of encoder architecture (single vs dual) and pooling method impacts results.

5. The use of MLM as an auxiliary task shows improvements in some cases.

I'll suggest ablation studies focusing on these key components, ranked by importance:

1. Dropout ablation - most critical since it's the core mechanism
2. Positive/negative pairs configuration - key design choice for supervised version
3. Architecture choices - important for model design
4. Temperature parameter - affects contrastive learning effectiveness
5. Auxiliary task impact - potential performance improvement
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Dropout Impact
- **Ablated Part**: Dropout mechanism in unsupervised SimCSE
- **Action**: REPLACE
- **Replacement**: 
  - p=0.0
  - p=0.05
  - p=0.15
  - p=0.2
  - fixed mask
- **Metrics**: Spearman correlation on STS-B, alignment, uniformity

### Positive-Negative Pairs
- **Ablated Part**: Use of entailment/contradiction pairs in supervised SimCSE
- **Action**: REPLACE
- **Replacement**: 
  - entailment only
  - entailment+neutral
  - all NLI pairs
  - random negatives
- **Metrics**: Spearman correlation on STS tasks, STS-B development score

### Encoder Architecture
- **Ablated Part**: Single encoder architecture
- **Action**: REPLACE
- **Replacement**: 
  - dual encoder
  - cross-attention encoder
- **Metrics**: Spearman correlation on STS tasks, transfer task accuracy

### Temperature Parameter
- **Ablated Part**: Contrastive learning temperature τ
- **Action**: REPLACE
- **Replacement**: 
  - τ=0.01
  - τ=0.05
  - τ=0.1
  - τ=0.5
  - τ=1.0
- **Metrics**: STS-B development score, alignment, uniformity

### MLM Impact
- **Ablated Part**: MLM auxiliary task
- **Action**: REMOVE
- **Metrics**: Spearman correlation on STS tasks, transfer task accuracy

</div>