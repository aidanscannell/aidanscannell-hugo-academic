---
title: "Vision Language Models as Reward Models"
author: ["Aidan Scannell"]
draft: false
summary: "Notes on using VLMs as reward models for RL"
type: "book"
---

Vision language models (VLMs) that have been trained on internet-scale text-image data sets have been used to formulate reward functions from language (<a href="#citeproc_bib_item_1">Kwon et al. 2022</a>; <a href="#citeproc_bib_item_4">Rocamonde et al. 2023</a>; <a href="#citeproc_bib_item_2">Mahmoudieh, Pathak, and Darrell 2022</a>).
For example,
Mahmoudieh, Pathak, and Darrell (<a href="#citeproc_bib_item_2">2022</a>);Rocamonde et al. (<a href="#citeproc_bib_item_4">2023</a>) use CLIP embeddings (<a href="#citeproc_bib_item_3">Radford et al. 2021</a>) to calculate the similarity between an image observation embedding and the goal text embedding.
Given a language goal \\(l\\), for example, \\(l=\text{Put the fork on the kitchen table}\\)" and an image observation \\(o\\), we can formulate a reward function as,

\begin{align}
R\_{\text{VLM}}(o,l) = \frac{\text{CLIP}\_{\text{v}}(o) \cdot \text{CLIP}\_{l}(l)}{\\| \text{CLIP}\_{\text{v}}(o) \\| \cdot \\| \text{CLIP}\_{\text{l}}(l) \\|},
\end{align}

where \\(\text{CLIP}\_{\text{l}}(\cdot)\\) is the language encoder and \\(\text{CLIP}\_{\text{v}}(\cdot)\\) is the vision encoder.
Intuitively, a higher similarity corresponds to higher reward, i.e. the observation is closer to the text goal.

It is worth noting that there are other ways to get reward functions from VLMS.
For example, Kwon et al. (<a href="#citeproc_bib_item_1">2022</a>) take an alternative approach and use LLMs to get reward signals.

## References

<style>.csl-entry{text-indent: -1.5em; margin-left: 1.5em;}</style><div class="csl-bib-body">
  <div class="csl-entry"><a id="citeproc_bib_item_1"></a>Kwon, Minae, Sang Michael Xie, Kalesha Bullard, and Dorsa Sadigh. 2022. “Reward Design with Language Models.” In <i>The Eleventh International Conference on Learning Representations</i>.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_2"></a>Mahmoudieh, Parsa, Deepak Pathak, and Trevor Darrell. 2022. “Zero-Shot Reward Specification via Grounded Natural Language.” In <i>Proceedings of the 39th International Conference on Machine Learning</i>, 14743–52. PMLR.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_3"></a>Radford, Alec, Jong Wook Kim, Chris Hallacy, Aditya Ramesh, Gabriel Goh, Sandhini Agarwal, Girish Sastry, et al. 2021. “Learning Transferable Visual Models From Natural Language Supervision.” arXiv. <a href="https://doi.org/10.48550/arXiv.2103.00020">https://doi.org/10.48550/arXiv.2103.00020</a>.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_4"></a>Rocamonde, Juan, Victoriano Montesinos, Elvis Nava, Ethan Perez, and David Lindner. 2023. “Vision-Language Models Are Zero-Shot Reward Models for Reinforcement Learning.” In <i>The Twelfth International Conference on Learning Representations</i>.</div>
</div>
