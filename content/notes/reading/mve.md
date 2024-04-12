---
title: "Model-based value expansion"
author: ["Aidan Scannell"]
draft: false
summary: "Notes on model-based value expansion (MVE)"
type: "book"
---

Model-based value expansion (MVE) was first proposed by Feinberg et al. (<a href="#citeproc_bib_item_3">2018</a>).
They expand the critic's target value using a deterministic dynamics model.

Stochastic ensemble value expansion (STEVE) (<a href="#citeproc_bib_item_2">Buckman et al. 2018</a>) extend MVE by learning a dynamics model with an ensemble of probabilistic NNs.
It combines different length value expansions by weighting them according to the inverse-variance from the dynamics ensemble.

Stochastic value gradient (SVG) (<a href="#citeproc_bib_item_1">Amos et al. 2021</a>) uses a deterministic dynamics model for MVE of policy (actor) objective but not the critic.
It then uses SAC to get exploration using entropy.

Palenicek et al. (<a href="#citeproc_bib_item_4">2022</a>; <a href="#citeproc_bib_item_5">Palenicek, Lutter, and Peters 2022</a>) tried using the oracle dynamics (i.e. the simulator) for the model-based value expansion.
They found that even when using the oracle dynamics, model-based value expansion could not improve sample efficiency.
They suggest model-free value expansion (e.g. Retrace) is a strong baseline without the computational overhead of model-based methods.
I can't help but think they could increase the UTD when using MVE to see improvement in sample efficiency.

## References

<style>.csl-entry{text-indent: -1.5em; margin-left: 1.5em;}</style><div class="csl-bib-body">
  <div class="csl-entry"><a id="citeproc_bib_item_1"></a>Amos, Brandon, Samuel Stanton, Denis Yarats, and Andrew Gordon Wilson. 2021. “On the Model-Based Stochastic Value Gradient for Continuous Reinforcement Learning.” In <i>Proceedings of the 3rd Conference on Learning for Dynamics and Control</i>, 6–20. PMLR.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_2"></a>Buckman, Jacob, Danijar Hafner, George Tucker, Eugene Brevdo, and Honglak Lee. 2018. “Sample-Efficient Reinforcement Learning with Stochastic Ensemble Value Expansion.” In <i>Advances in Neural Information Processing Systems</i>. Vol. 31. Curran Associates, Inc.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_3"></a>Feinberg, Vladimir, Alvin Wan, Ion Stoica, Michael I. Jordan, Joseph E. Gonzalez, and Sergey Levine. 2018. “Model-Based Value Estimation for Efficient Model-Free Reinforcement Learning.” In <i>Proceedings of the 35th International Conference on Machine Learning</i>. <a href="https://doi.org/10.48550/arXiv.1803.00101">https://doi.org/10.48550/arXiv.1803.00101</a>.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_4"></a>Palenicek, Daniel, Michael Lutter, Joao Carvalho, and Jan Peters. 2022. “Diminishing Return of Value Expansion Methods in Model-Based Reinforcement Learning.” In <i>The Eleventh International Conference on Learning Representations</i>.</div>
  <div class="csl-entry"><a id="citeproc_bib_item_5"></a>Palenicek, Daniel, Michael Lutter, and Jan Peters. 2022. “Revisiting Model-based Value Expansion.” arXiv. <a href="https://doi.org/10.48550/arXiv.2203.14660">https://doi.org/10.48550/arXiv.2203.14660</a>.</div>
</div>
