<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Shh__don_t_say_that__Domain_Certification_in_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Shh, don't say that! Domain Certification in LLMs" presents a novel framework for domain certification in large language models (LLMs). The authors propose a method called VALID, which provides adversarial bounds as a certificate for the model's behavior. The method uses a guide model G to approximate the oracle Ω, which assigns high likelihood to sentences in the target domain T and zero likelihood to elements in the forbidden set F.

The paper presents several ablation studies to evaluate the effectiveness of the proposed method. However, there are some missing ablation studies that could provide further insights into the method's performance.

One potential missing ablation study is an analysis of the impact of the guide model's size on the performance of the VALID method. The authors mention that they use a custom GPT-2 model with 184M parameters as the guide model, but they do not provide any results on how the size of the guide model affects the performance of the method.

Another potential missing ablation study is an analysis of the impact of the rejection threshold k on the performance of the VALID method. The authors mention that they set k to achieve a 10% false rejection rate (FRR) for in-domain samples, but they do not provide any results on how different values of k affect the performance of the method.

Overall, the paper presents a novel and interesting approach to domain certification in LLMs, but further ablation studies could provide more insights into the method's performance and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: guide model size
- **Action**: REPLACE
- **Replacement**: 
  - small
  - medium
  - large
- **Metrics**: FRR, constriction ratio

### Ablation Study 2
- **Ablated Part**: rejection threshold k
- **Action**: REPLACE
- **Replacement**: 
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: FRR, constriction ratio

</div>