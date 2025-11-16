## <img src="fig/owl.svg" width="40" alt="Owl Logo"> [AAAI2026]Causally-Grounded Dual-Path Attention Intervention for Object Hallucination Mitigation in LVLMs

![DPC](fig/565d4f952397b052549817ebab404338.jpg)
The official repo for Owl,a causally-grounded dual-path attention intervention method for mitigating object hallucination in large vision-language models.
Full paper can be found at: [https://arxiv.org/pdf/2511.09018](https://arxiv.org/pdf/2511.09018).

<div style='display:flex; gap: 0.25rem; '>
<a href='https://arxiv.org/pdf/2511.09018'><img src='https://img.shields.io/badge/Paper-PDF-red'></a>
<a href='LICENCE'><img src='https://img.shields.io/badge/License-Apache 2.0-g.svg'></a>
</div>

## 🗓 To-Do List
- ✅ Key code for editing attention released
- ✅ Preprint of the paper released, check it [here](https://arxiv.org/pdf/2511.09018)
- ⭕ English version of the introduction video: 
- ⭕ The video talk (Chinese version) is now public
- ⭕ Full code release (llava with vision)

## Intro
- We introduce a dual-path contrastive decoding strategy: one path enhances visually grounded predictions, while the other amplifies hallucinations - allowing the model to "let truth shine and hallucination collapse".
- The new **contrastive probability distribution** for decoding is formulated as:

$$
P_{\text{DCD}}(Y|X_V, X_I) = \text{Softmax} \Big[ (1+\lambda) \cdot \log p_{\theta}(y|X_{V\uparrow}, X_{T\downarrow}) - \lambda \cdot \log p_{\theta}(y|X_{V\downarrow}, X_{T\uparrow}) \Big]
$$

where:
- $(X_{V\uparrow}, X_{T\downarrow})$ denotes the **visual-favored** decoding setting,
- $(X_{V\downarrow}, X_{T\uparrow})$ denotes the **text-favored** decoding setting,
- $\lambda$ is a tunable contrastive weight.
 ## 🎯 Causal Modeling of Object Hallucination Process
The proposed SCM for hallucination analysis in LVLMs. Visual input ($X_V$) and text input ($X_T$) affect the output ($Y_T$) through visual ($A_V$) and text attention ($A_T$). Visual ($P_V$) and language priors ($P_T$) confound the attention paths and may cause hallucinations. Interventions on $A_V$ and $A_T$ help assess their causal impact.
![SCM](fig/scm.PNG)
isualization of dual-path attention intervention.Compared to the original attention, the visual and text favored paths highlight distinct modality preferences in token-level attention.
![attention](fig/59e7b5f4b41cd2856d7d94de818b015f.jpg)
