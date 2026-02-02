<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/memorizing-transformers-pytorch

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the Memorizing Transformers paper, I'll suggest ablation studies focusing on the key components of their method. Here's my reasoning:

1. The most critical component is the kNN-based memory mechanism, which is fundamental to the method's ability to memorize past inputs. Testing without it would establish its importance.

2. The gating mechanism that combines local and memory-based attention is another key architectural choice. Testing different combination strategies would help understand its importance.

3. The size of the memory is a crucial hyperparameter that directly affects performance. The paper shows improvements up to 262K tokens, but understanding the relationship between memory size and performance is important.

4. The key/query normalization is mentioned as important for handling "staleness" in the memory. Testing without it would help validate this claim.

5. The position of the kNN-augmented layer in the transformer stack could impact performance. The paper mentions putting it "near the top" but doesn't ablate this choice.

I'll rank these from most to least important for understanding the method's effectiveness.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Memory Ablation
- **Ablated Part**: kNN-based external memory mechanism
- **Action**: REMOVE
- **Metrics**: perplexity, accuracy

### Gating Mechanism
- **Ablated Part**: learned gate combining local and memory attention
- **Action**: REPLACE
- **Replacement**: 
  - fixed 0.5 weight
  - learned weighted sum
  - concatenation
- **Metrics**: perplexity, accuracy

### Memory Size
- **Ablated Part**: size of external memory
- **Action**: REPLACE
- **Replacement**: 
  - 8K
  - 32K
  - 131K
  - 262K
- **Metrics**: perplexity, accuracy

### Key/Query Normalization
- **Ablated Part**: normalization of keys and queries
- **Action**: REMOVE
- **Metrics**: perplexity, accuracy, training stability

### Layer Position
- **Ablated Part**: position of kNN-augmented layer
- **Action**: REPLACE
- **Replacement**: 
  - bottom layer
  - middle layer
  - top layer
  - multiple layers
- **Metrics**: perplexity, accuracy

</div>