<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Mitigating_Dataset_Bias_by_Using_Per_Sample_Gradient

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a debiasing algorithm leveraging gradient called Per-sample Gradient-based Debiasing (PGD). PGD is comprised of three steps: (1) training a model on uniform batch sampling, (2) setting the importance of each sample in proportion to the norm of the sample gradient, and (3) training the model using importance-batch sampling, whose probability is obtained in step (2). The paper also provides theoretical understandings of how PGD can mitigate dataset bias.

To suggest missing ablation studies for the research, we need to analyze the method and pay attention to the ablation section which is usually under the experiment section or in the appendix.

The paper source is provided below, after all of the instructions.

INSTRUCTIONS:
Now, you're going to suggest UP TO 2 missing ablation studies in the given paper on your own, in a JSONL format.
You need to rank the output ablation studies by their importance, and you should only include the most important ones.
A missing ablation refers to an experiment that you believe should have been conducted, in which a specific component, module, feature, or design choice is removed, replaced, or altered in order to assess its impact on the method's performance.
You must clearly indicate that such an ablation study is missing from the given paper.
Each suggestion should include the following fields in a separate JSON:

1. "name": name of the ablation experiment.
2. "ablated_part": high-level description of the part of the method in the research that you want to ablate.
3. "action": the action you want to take on the ablated part (REMOVE, REPLACE, ADD). If the action is REPLACE or ADD please add a field named "replacement" and specify a list of possible replacements/additions, for example if you want to change the value of a parameter please specify a list of values to test.
4. "metrics": a list of metrics to report of the ablation experiment. Please pay special attention and use the metrics that are also used in the paper.

When you're satisfied with your ablation studies plan, you can submit your plan.

GENERAL IMPORTANT TIPS:

1. The paper source is provided below, after all of the instructions.

2. Remember that we are looking for _MISSING IMPORTANT ABLATIONS_, and as such they should attribute to the method's major components.

3. Less is more - don't aim to change completely the method, take the important parts and investigate them.


STRATEGY:

1. Read the paper sections, especially the method section, to understand the method, and pay attention to the ablation section which is usually under the experiment section or in the appendix.

2. You must first understand and extract the ablation studies that already exist in the paper (use them in your discussion field to better reason about missing ablations).

3. Then, look at the main components of the method and think about what would happen if you change them.

4. Keep in mind that ablation studies aim to attribute the method's performance to its major components, so think about what the ablation studies in the paper are currently missing.

5. Remember that ablation studies does not necessarily mean removing parts of the method, but also changing them.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: gradient norm
- **Action**: REPLACE
- **Replacement**: 
  - loss
  - accuracy
- **Metrics**: unbiased test accuracy

### Ablation B
- **Ablated Part**: importance-batch sampling
- **Action**: REMOVE
- **Metrics**: unbiased test accuracy

</div>