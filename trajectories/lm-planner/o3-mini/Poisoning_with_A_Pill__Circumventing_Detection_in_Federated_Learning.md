<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Poisoning_with_A_Pill__Circumventing_Detection_in_Federated_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key component of the proposed method is the design of the “pill blueprint” – that is, selecting a compact, specific subset of parameters (e.g. one neuron per layer in most layers) to be used as the attack “pill.” While the paper fixes this structure to achieve stealthiness and improved attack impact, it does not systematically explore the trade‐offs between pill size (i.e. how many neurons/channels are included per layer) and performance metrics such as error rate increase as well as the stealth indicators (cosine similarity score and distance score). Ablating the size of the pill (by varying the number of selected neurons per layer according to different blueprint designs) would isolate the effect that the “compression” of poison injection has on both attack effectiveness and detectability.

Another important component is the extra training rounds used in the pill poisoning stage. The method leverages an extra-trained model update from malicious clients to drive the poisoning process; however, while Figure 2 hints at the influence of extra training rounds (E_extra), a dedicated ablation study that varies the number of extra epochs (including the extreme case where no extra training is done) is missing. Such an ablation would help quantify how sensitive the overall attack enhancement is to the level of extra training applied. In both cases, the metrics to report would be the error rate on the global model (as used through the experiments), as well as stealth indicators such as cosine similarity and distance scores.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Pill Blueprint Size Ablation
- **Ablated Part**: The design of the pill blueprint (i.e., the number of selected neurons/channels per layer constituting the pill)
- **Action**: REPLACE
- **Replacement**: 
  - 1 neuron/channel per layer (baseline)
  - 2 neurons/channels per layer
  - 3 neurons/channels per layer
- **Metrics**: error rate, cosine similarity, distance score

### Extra Training Epoch Ablation
- **Ablated Part**: The number of extra training epochs used during the pill poisoning stage
- **Action**: REPLACE
- **Replacement**: 
  - 0 extra epochs
  - 1 extra epoch
  - 3 extra epochs
  - 5 extra epochs
- **Metrics**: error rate, cosine similarity, distance score

</div>