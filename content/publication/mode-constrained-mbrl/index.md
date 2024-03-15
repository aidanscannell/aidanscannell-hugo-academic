---
# Documentation: https://wowchemy.com/docs/managing-content/


title: "Mode-constrained Model-based Reinforcement Learning via Gaussian Processes"
authors: [Aidan Scannell, Carl Henrik Ek, Arthur Richards]
# date: 2023-04-27T21:01:09+03:00
date: 2023-04-27
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: 2022-10-16T21:01:09+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: "26th International Conference on Artificial Intelligence and Statistics (AISTATS)"
#publication_short: "AISTATS 2023"

abstract: "Model-based reinforcement learning (RL) algorithms do not typically consider environments with multiple dynamic modes, where it is beneficial to avoid inoperable or undesirable modes. We present a model-based RL algorithm that constrains training to a single dynamic mode with high probability. This is a difficult problem because the mode constraint is a hidden variable associated with the environment's dynamics. As such, it is 1) unknown a priori and 2) we do not observe its output from the environment, so cannot learn it with supervised learning. We present a nonparametric dynamic model which learns the mode constraint alongside the dynamic modes. Importantly, it learns latent structure that our planning scheme leverages to 1) enforce the mode constraint with high probability, and 2) escape local optima induced by the mode constraint. We validate our method by showing that it can solve a simulated quadcopter navigation task whilst providing a level of constraint satisfaction both during and after training."

# Summary. An optional shortened abstract.
summary: "We present a model-based RL algorithm that constrains training to a single dynamic mode with high probability. This is a difficult problem because the mode constraint is a hidden variable associated with the environment's dynamics. As such, it is 1) unknown a priori and 2) we do not observe its output from the environment, so cannot learn it with supervised learning."

tags: ["model-based reinforcement learning", "gaussian-processes", "bayesian-inference", "variational-inference", "machine-learning", "approximate-inference"]
categories: []
featured: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
 - name: Follow
   url: https://twitter.com/scannell_aidan/status/1617792928646311937
   icon_pack: fab
   icon: twitter

url_pdf: https://proceedings.mlr.press/v206/scannell23a.html
url_code: "https://github.com/aidanscannell/ModeRL"
url_dataset:
url_poster: "/publication/mode-constrained-mbrl/poster.pdf"
url_project:
url_slides:
url_source: https://github.com/aidanscannell/aistats-2023-mode-constrained-model-based-rl
url_video:

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: [mode-constrained-model-based-reinforcement-learning]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
# TODO adde new gifs
---
<!-- ## Experiments -->
<!-- Here we show visualisations of our experiments in the simulated quadcopter navigation problem. -->


<!-- <table class=".table" style="width:100%"> -->
<!--   <thead> -->
<!--   <tr> -->
<!--     <td>Experiment</td> -->
<!--     <td>Description</td> -->
<!--     </tr> -->
<!--   </thead> -->
<!--   <tbody> -->
<!--   <tr> -->
<!--     <td style="width:10%"> -->
<!-- {{< figure src="/mode-constrained-mbrl/greedy-no-constraint.gif" caption="<b>Greedy exploitation without mode constraint</b>" >}}</td> -->
<!--     <\!-- <td><img src="http://localhost:1313/publications/mode-constrained-mbrl/greedy-no-constraint.gif" alt="Greedy exploitation without mode constraint"></td> -\-> -->
<!--     <td style="width:10%"> -->
<!--      We are not able to solve our δ-mode-constrained navigation problem with the greedy exploitation strategy becaue it leaves the desired dynamics mode.</td> -->
<!--   </tr> -->
<!--   <tr> -->
<!--     <td style="width:10%"> -->
<!-- {{< figure src="/mode-constrained-mbrl/greedy-with-constraint.gif" caption="<b>Greedy exploitation with mode constraint</b>" >}}</td> -->
<!--     <td style="width:10%"> -->
<!--     Adding the δ-mode-constraint to the greedy exploitation strategy is still not able to solve our δ-mode-constrained navigation problem. This is because the optimisation gets stuck at a local optima induced by the constraint. -->
<!--      </td> -->
<!--   </tr> -->
<!--   <tr> -->
<!--     <td style="width:10%"> -->
<!-- {{< figure src="/mode-constrained-mbrl/moderl-exploration.gif" caption="<b>ModeRL (ours)</b>" >}}</td> -->
<!--     <td style="width:10%"> -->
<!--     Our strategy successfully solves our δ-mode-constrained navigation problem by augmenting the greedy exploitation objective with an intrinsic motivation term. Our intrinsic motivation uses the epistmic uncertainty associated with the learned mode constraint to escape local optima induced by the constraint. -->
<!--      </td> -->
<!--   </tr> -->
<!--   <tr> -->
<!--     <td style="width:10%"> -->
<!-- {{< figure src="/mode-constrained-mbrl/aleatoric-uncertainty.gif" caption="<b>Aleatoric uncertainty (ablation)</b>" >}}</td> -->
<!--     <td style="width:10%"> -->
<!-- Here we show the importance of using only the epistemic uncertainty for exploration. This experiment augmented the greedy objective with the entropy of the mode indicator variable. It cannot escape the local optimum induced by the mode constraint because the mode indicator variable's entropy is <b>always</b> high at the mode boundary. This motivated formulating a dynamics model which can disentangle the sources of uncertainty in the mode constraint. -->
<!--      </td> -->
<!--   </tr> -->
<!--   <tr> -->
<!--     <td style="width:10%"> -->
<!-- {{< figure src="/mode-constrained-mbrl/myopic-moderl.gif" caption="<b>Myopic exploration (ablation)</b>" >}}</td> -->
<!--     <td style="width:10%"> -->
<!--     Finally, we motivate why our intrinsic motivatin term considers the joint entroy over a trajectory, instead of summing the entropy at each time step (as is often seen in the literature). This experiment formulated the intrinsic motivation term as the sum of the gating function entropy at each time step. That is, it assumed each time step is independent and did not consider the information gain over an entire trajectory, i.e. the exploration is myopic (aka shortsighted). -->
<!--      </td> -->
<!--   </tr> -->
<!--   </tbody> -->
<!-- </table> -->

