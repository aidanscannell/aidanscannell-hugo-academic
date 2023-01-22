---
# Documentation: https://wowchemy.com/docs/managing-content/


title: "Mode-Constrained Model-Based Reinforcement Learning via Gaussian Processes"
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
publication: "26th International Conference on Artificial Intelligence and Statistics"
publication_short: "AISTATS 2023"

abstract: "Model-based reinforcement learning (MBRL) algorithms do not typically consider environments -- subject to multiple dynamics modes -- where it is beneficial to avoid inoperable or undesirable dynamics modes. We present a MBRL algorithm that avoids entering such inoperable or undesirable dynamics modes, by constraining the controlled system to remain in a single dynamics mode with high probability. This is a particularly difficult problem because the mode constraint is unknown a priori. We propose to jointly infer the mode constraint, along with the underlying dynamics modes. Importantly, our method infers latent structure that our planning scheme leverages to 1) enforce the mode constraint with high probability, and to 2) target exploration where the mode constraint’s epistemic uncertainty is high. We validate our method by showing that it can navigate a simulated quadcopter -- subject to a turbulent dynamics mode -- to a target state, whilst remaining in the desired dynamics mode with high probability."

# Summary. An optional shortened abstract.
summary: ""

tags: ["model-based reinforcement learning", "gaussian-processes", "bayesian-inference", "variational-inference", "machine-learning", "approximate-inference"]
categories: []
featured: True

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

#url_pdf: "/publication/mode-constrained-mbrl/paper.pdf"
url_code: "https://github.com/aidanscannell/ModeRL"
url_dataset:
url_poster:
url_project:
url_slides:
#url_source: https://github.com/aidanscannell/aistats-2023-mode-remaining-exploration
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
projects: [mode-remaining-exploration-for-model-based-reinforcement-learning]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---


<!-- ## Problem Statement -->
<!-- We consider multimodal, stochastic environments with -->
<!-- states $s_t \in \mathcal{S}$, actions $a_t \in \mathcal{A}$ and transition dynamics given by, -->
<!-- $$ -->
<!-- s_{t+1} = f_k(s_t, a_t) + \epsilon_{k,t}, \quad\text{if } \alpha(s_t) = k, -->
<!-- $$ -->
<!-- where the discrete mode indicator function $\alpha(s_t)$ -->
<!-- indicates which of the $K$ underlying dynamics modes -->
<!-- $\\{f_k : {\mathcal{S}}\_{k} \times \mathcal{A} \rightarrow \mathcal{S} \\}_{k=1}^{K}$ -->
<!-- and associated i.i.d. noise models ${\epsilon}\_{k, t}$ -->
<!-- governs the environment at a given time step $t$. -->

<!-- <\!-- We refer to the output of the mode indicator function as the mode indicator variable -\-> -->
<!-- <\!-- $\alpha_{\timeInd} = \alpha(\state_{\timeInd}) \in \{1,\ldots,\ModeInd\}$. -\-> -->
<!-- <\!-- # $\bm\epsilon_{\modeInd, \timeInd} \sim \mathcal{N}\left(\mathbf{0}, \bm\Sigma_{\mode{\bm\epsilon}} \right)$, -\-> -->

<!-- Given such transition dynamics, we seek to solve the mode constrained episodic RL problem, given by -->
<!-- $$ -->
<!-- \max_{\pi \in \Pi} J(\pi, f) \quad \text{s.t.} \quad \alpha(s_t) = k^* \quad \forall t \in \\{0, \ldots, T\\}, -->
<!-- $$ -->
<!-- where given a known transition dynamics model $f$, -->
<!-- the performance of a policy $\pi$ is the sum of rewards over the horizon, in expectation over the transition noise,  -->
<!-- $$ -->
<!-- J(\pi, f) = \mathbb{E}[\sum_{t=0}^{T} r(s_t, a_t) \mid s_0]. -->
<!-- $$ -->

<!-- Given that neither the underlying dynamics modes $\\{f_k\\}_{k=1}^{K}$, nor how the system -->
<!-- switches between them $\alpha$, are *known a priori*, it is not possible to solve our mode constrained RL problem. -->
<!-- <\!-- Therefore, we relax the requirement to finding a mode-constrained policy with high probability. -\-> -->
<!-- <\!-- We formally define a $\delta-\text{mode-constrained}$ policy as follows. -\-> -->
<!-- <\!-- \begin{definition}[$\delta$-mode-constrained] \label{def-delta-mode-remaining} -\-> -->
<!-- <\!-- Let $\dynamicsFunc : \stateDomain \times \controlDomain \rightarrow \stateDomain$ denote a multimodal dynamical system -\-> -->
<!-- <\!-- and $\desiredMode$ a desired dynamics mode defined by its state domain $\desiredStateDomain = \{ \state \in \stateDomain \mid \modeVar(\state) = \desiredMode \}$. -\-> -->
<!-- <\!-- Given an initial state $\state_0 \in \desiredStateDomain$ and $\delta \in (0,1]$, -\-> -->
<!-- <\!-- a controlled system is said to be $\delta$-mode-constrained under the policy $\pi$ iff: -\-> -->
<!-- <\!-- \begin{align} \label{eq-mode-remaining-def-explore} -\-> -->
<!-- <\!-- \Pr( \forall \timeInd \in \{0,\ldots, \TimeInd \} : -\-> -->
<!-- <\!-- \dynamicsFunc(\state_{\timeInd}, \policy(\state_{\timeInd}, \timeInd)) &\in \stateDomain_{\desiredMode}) \geq 1 - \delta. -\-> -->
<!-- <\!-- \end{align} -\-> -->
<!-- <\!-- \end{definition} -\-> -->

<!-- <\!-- Policies satisfying this $\delta-\text{mode-constrained}$ definition -\-> -->
<!-- <\!-- should remain in the desired dynamics mode with probability up to $1-\delta$. -\-> -->
<!-- <\!-- It is worth noting that the agent would not be able to explore the environment without relaxing the -\-> -->
<!-- <\!-- mode constraint from cref:def-mode-remaining-main. -\-> -->
<!-- <\!-- Increasing $\delta$ promotes exploration but also increases the chance of violating the mode constraint. -\-> -->
<!-- <\!-- As such, $\delta$ can be viewed as setting the conservativeness of the agent's exploration. -\-> -->
<!-- {{< math >}} -->
<!-- $$a &= \\ a &=a $$ -->
<!-- {{< /math >}} -->

<!-- {{< math >}} -->
<!-- $ -->
<!-- \pi_{\text{greedy}}&= \max_{\pi \in \Pi} \underbrace{\mathbb{E}_{f_{k^*} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})} \left[ J(\pi, f_{k^*}) \right]}_{\text{greedy exploitation}} -->
<!-- \\ -->
<!-- \text{s.t. } &\underbrace{\mathbb{E}_{f_{k^*} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})}\left[ \Pr(\alpha_{t} = k^* \mid \mathbf{s}_t) \right] \geq 1-\delta}_{\delta \text{ mode constraint}}, \quad \forall t \label{eq-expected-constraint}, \in \{ 0, \ldots, T \} -->
<!-- $ -->
<!-- {{< /math >}} -->


<!-- {{< math >}} -->
<!-- $$ -->
<!-- \pi_{\text{greedy}}= \max_{\pi \in \Pi} \underbrace{\mathbb{E}_{f_{k^**} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})} \left[ J(\pi, f_{k^*}) \right]}_{\text{greedy exploitation}}, \quad  \text{s.t. } \underbrace{\mathcal{E}_{f_{k^*} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})}\left[ \Pr(\alpha_{t} = k^* \mid \mathbf{s}_t) \right] \geq 1-\delta}_{\delta \text{ mode constraint}}, \quad \forall t \label{eq-expected-constraint}, \in \{ 0, \ldots, T \} -->
<!-- $$ -->
<!-- {{< /math >}} -->

<!-- <\!-- \begin{align} -\-> -->
<!-- <\!-- &\pi_{\text{greedy}}= -\-> -->
<!-- <\!-- \max_{\pi \in \Pi} -\-> -->
<!-- <\!-- \underbrace{ {\mathbb{E}} [  ]\}\_{\text{greedy exploitation}}, \\ -\-> -->
<!-- <\!-- &\text{s.t. } {\mathbb{E}}\_{{f}_{k}} [ J(\pi, {f}\_{{k}\_{*}}) ] -\-> -->
<!-- <\!-- \geq 1-\delta, \quad \forall  t \in a \{ 0, \ldots, T \} -\-> -->
<!-- <\!-- \end{align} -\-> -->

<!-- <\!-- %\mathbb{E}_{f_{k^*} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})} [ J(\pi, f_{k^*}) ], \\ -\-> -->

<!-- ## Greedy exploitation -->
<!-- Given this approach for making multi-step dynamics predictions, we formulate a relaxed version of the mode-constrained problem in cref:eq-main-problem, -->
<!-- \begin{subequations} \label{eq-greedy-objective} -->
<!-- \begin{align} -->
<!-- &\pi_{\text{greedy}}= -->
<!-- \max_{\pi \in \Pi} -->
<!-- \underbrace{\mathbb{E}_{f_{k^**} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})} \left[ J(\pi, f_{k^*}) \right]}_{\text{greedy exploitation}}, \\ -->
<!-- &\text{s.t. } \underbrace{\mathcal{E}_{f_{k^*} \sim p(f_{k^*} \mid \mathcal{D}_{0:i})} -->
<!-- \left[ \Pr(\alpha_{t} = k^* \mid \mathbf{s}_t) \right] -->
<!-- \geq 1-\delta}_{\delta \text{ mode constraint}}, \quad \forall t \label{eq-expected-constraint}, -->
<!-- \in \{ 0, \ldots, T \} -->
<!-- \end{align} -->
<!-- \end{subequations} -->

<!-- The expectations are taken over the desired mode's $\dynamicsFunc_{\desiredMode}$ \acrshort{gp} dynamics. -->
<!-- This approach has the added benefit that we can calculate the expected mode constraint in closed form and -->
<!-- given a quadratic reward function, we can also calculate the objective in closed form. -->
<!-- Importantly, the expected mode constraint considers the /epistemic uncertainty/ in both the desired dynamics mode -->
<!-- $p(\dynamicsFunc_{\desiredMode}(\singleInput) \mid \singleInput, \dataset_{0:i})$ -->
<!-- and in the gating network $p(\GatingFunc(\state_{\timeInd}) \mid \state_{\timeInd}, \dataset_{0:i})$. -->
<!-- This ensures that the controlled system is $\delta-\text{mode-constrained}$ (cref:def-delta-mode-remaining) under the uncertainty of -->
<!-- the learned dynamics model. -->
<!-- Intuitively, it will remain where the dynamics model's /epistemic uncertainty/ is low -->
<!-- because the expectation results in lower proababilities for more uncertain states. -->

## Experiments
Here we show visualisations of our experiments in the simulated quadcopter navigation problem.
<!-- **Greedy exploitation** -->
<!-- The greedy exploitation strategy with the mode constraint gets stuck at a local optima induced by the constraint. -->
<!-- ![Greedy exploitation with mode constraint](/mode-constrained-mbrl/greedy-with-constraint.gif) -->

<!-- **Greedy exploitation (no mode constraint)** -->
<!-- The greedy exploitation strategy without the mode constraint leaves the desired dynamics mode. -->
<!-- ![Greedy exploitation without mode constraint](/mode-constrained-mbrl/greedy-no-constraint.gif)  -->

<!-- **ModeRL** -->
<!-- ![ModeRL](/mode-constrained-mbrl/moderl-exploration.gif) -->
<!-- Joint gating function entropy -->

<!-- **Aleatoric uncertainty** -->
<!-- Using the entropy of the mode indicator variable for exploratin is not able to escape the local optimum induced by the mode constraint.                                                   -->
<!-- ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif) -->

<!-- **Myopic exploration** -->
<!-- ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif) -->
<!-- Mean of independent gating function entropy -->



<!-- | GIF                                                                                             | Description                                                                                    | -->
<!-- |------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------| -->
<!-- | ![Greedy exploitation with mode constraint](/mode-constrained-mbrl/greedy-with-constraint.gif)  |                                                  | -->
<!-- | ![Greedy exploitation without mode constraint](/mode-constrained-mbrl/greedy-no-constraint.gif) | The greedy exploitation strategy without the mode constraint leaves the desired dynamics mode. | -->
<!-- | ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif)             | Using the entropy of the mode indicator variable for exploratin is not able to escape the local optimum induced by the mode constraint.                                                   | -->
<!-- | ![ModeRL](/mode-constrained-mbrl/moderl-exploration.gif)                                        | Joint gating function entropy. <br><br> Mode constraint.                                       | -->
<!-- | ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif)                        | Mean of independent gating function entropy. <br><br> Mode constraint.                         | -->


<table class=".table" style="width:100%">
  <thead>
  <tr>
    <td>Experiment</td>
    <td>Description</td>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td style="width:10%">
{{< figure src="/mode-constrained-mbrl/greedy-no-constraint.gif" caption="<b>Greedy exploitation without mode constraint</b>" >}}</td>
    <!-- <td><img src="http://localhost:1313/publications/mode-constrained-mbrl/greedy-no-constraint.gif" alt="Greedy exploitation without mode constraint"></td> -->
    <td style="width:10%">
     We are not able to solve our δ-mode-constrained navigation problem with the greedy exploitation strategy becaue it leaves the desired dynamics mode.</td>
  </tr>
  <tr>
    <td style="width:10%">
{{< figure src="/mode-constrained-mbrl/greedy-with-constraint.gif" caption="<b>Greedy exploitation with mode constraint</b>" >}}</td>
    <td style="width:10%">
    Adding the δ-mode-constraint to the greedy exploitation strategy is still not able to solve our δ-mode-constrained navigation problem. This is because the optimisation gets stuck at a local optima induced by the constraint.
     </td>
  </tr>
  <tr>
    <td style="width:10%">
{{< figure src="/mode-constrained-mbrl/moderl-exploration.gif" caption="<b>ModeRL (ours)</b>" >}}</td>
    <td style="width:10%">
    Our strategy successfully solves our δ-mode-constrained navigation problem by augmenting the greedy exploitation objective with an intrinsic motivation term. Our intrinsic motivation uses the epistmic uncertainty associated with the learned mode constraint to escape local optima induced by the constraint.
     </td>
  </tr>
  <tr>
    <td style="width:10%">
{{< figure src="/mode-constrained-mbrl/aleatoric-uncertainty.gif" caption="<b>Aleatoric uncertainty (ablation)</b>" >}}</td>
    <td style="width:10%">
Here we show the importance of using only the epistemic uncertainty for exploration. This experiment augmented the greedy objective with the entropy of the mode indicator variable. It cannot escape the local optimum induced by the mode constraint because the mode indicator variable's entropy is <b>always</b> high at the mode boundary. This motivated formulating a dynamics model which can disentangle the sources of uncertainty in the mode constraint.
     </td>
  </tr>
  <tr>
    <td style="width:10%">
{{< figure src="/mode-constrained-mbrl/myopic-moderl.gif" caption="<b>Myopic exploration (ablation)</b>" >}}</td>
    <td style="width:10%">
    Finally, we motivate why our intrinsic motivatin term considers the joint entroy over a trajectory, instead of summing the entropy at each time step (as is often seen in the literature). This experiment formulated the intrinsic motivation term as the sum of the gating function entropy at each time step. That is, it assumed each time step is independent and did not consider the information gain over an entire trajectory, i.e. the exploration is myopic (aka shortsighted).
     </td>
  </tr>
  </tbody>
</table>


<!-- | GIF                                                                                             | Description                                                                                    | -->
<!-- |:------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------| -->
<!-- | ![Greedy exploitation without mode constraint](/mode-constrained-mbrl/greedy-no-constraint.gif) | **Greedy no constraint** - The greedy exploitation strategy without the mode constraint is not able to solve our mode-constrained navigation problem becaue it leaves the desired dynamics mode. | -->
<!-- | ![Greedy exploitation with mode constraint](/mode-constrained-mbrl/greedy-with-constraint.gif)  | **Greedy with constraint** - Simply using the greedy exploitation strategy with our mode constraint is still not able to solve our mode-constrained navigation problem. This is because the optimisation gets stuck at a local optima induced by the constraint.                                                 | -->
<!-- | ![ModeRL](/mode-constrained-mbrl/moderl-exploration.gif)                                        | **ModeRL (ours)** - Joint gating function entropy. <br><br> Mode constraint.                                       | -->
<!-- | ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif)                        | **Myopic exploration** - Mean of independent gating function entropy. <br><br> Mode constraint.                         | -->
<!-- | ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif)             | **Aleatoric uncertainty** - Here we show the importance of only using the epistemic ucnertainty for exploration. This figure show our objective with the entropy of the mode indicator variable. It shows that it is not able to escape the local optimum induced by the mode constraint because it .                                                   | -->


<!-- | Name                  | GIF                                                                                             | Description                                                                                    | -->
<!-- |:----------------------|:------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------| -->
<!-- | Greedy                | ![Greedy exploitation with mode constraint](/mode-constrained-mbrl/greedy-with-constraint.gif)  | The greedy exploitation strategy with the mode constraint gets stuck at a local optima induced by the constraint.                                                 | -->
<!-- | Greedy unconstrained  | ![Greedy exploitation without mode constraint](/mode-constrained-mbrl/greedy-no-constraint.gif) | The greedy exploitation strategy without the mode constraint leaves the desired dynamics mode. | -->
<!-- | Aleatoric uncertainty | ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif)             | Using the entropy of the mode indicator variable for exploratin is not able to escape the local optimum induced by the mode constraint.                                                   | -->
<!-- | ModeRL                | ![ModeRL](/mode-constrained-mbrl/moderl-exploration.gif)                                        | Joint gating function entropy. <br><br> Mode constraint.                                       | -->
<!-- | Myopic                | ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif)                        | Mean of independent gating function entropy. <br><br> Mode constraint.                         | -->






<!-- <\!-- | Non-myopic exploration strategy      | Myopic exploration strategy | Aleatoric uncertainty     | -\-> -->
<!-- <\!-- | :---        |    :----   |          :--- | -\-> -->
<!-- <\!-- | ![Non-myopic exploration strategy](/mode-constrained-mbrl/moderl-exploration.gif) | ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif)| ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif)   | -\-> -->

<!-- <\!-- | Non-myopic exploration strategy      | Myopic exploration strategy | Aleatoric exploration strategy     | -\-> -->
<!-- <\!-- | :---        |    :----   |          :--- | -\-> -->
<!-- <\!-- | ![Non-myopic exploration strategy](/mode-constrained-mbrl/moderl-exploration.gif) | ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif)| ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif)   | -\-> -->


<!-- <\!-- ### Greedy Exploitation -\-> -->

<!-- <\!-- | WITHOUT mode constraint | WITH mode constraint | -\-> -->
<!-- <\!-- | :---        |    :---   | -\-> -->
<!-- <\!-- | ![Greedy exploitation without mode constraint](/mode-constrained-mbrl/greedy-no-constraint.gif) | ![Greedy exploitation with mode constraint](/mode-constrained-mbrl/greedy-with-constraint.gif)  | -\-> -->

<!-- <\!-- ### ModeRL -\-> -->
<!-- <\!-- ![Non-myopic exploration strategy](/mode-constrained-mbrl/moderl-exploration.gif) -\-> -->

<!-- <\!-- ![Myopic exploration strategy](/mode-constrained-mbrl/myopic-moderl.gif) -\-> -->
<!-- <\!-- ![Aleatoric exploration strategy](/mode-constrained-mbrl/aleatoric-uncertainty.gif) -\-> -->

<!-- <\!-- ### Greedy Exploitatin Failing -\-> -->

<!-- <\!-- ![Greedy exploitation with mode constraint](/mode-constrained-mbrl/greedy-with-constraint.gif) -\-> -->
<!-- <\!-- ![Greedy exploitation without mode constraint](/mode-constrained-mbrl/greedy-no-constraint.gif) -\-> -->


<!-- <\!-- ## Cite -\-> -->
<!-- <\!-- ``` -\-> -->
<!-- <\!-- @inproceedings{scannellMode2023, -\-> -->
<!-- <\!--   title = {Mode-Constrained Model-Based Reinforcement Learning via Gaussian Processes}, -\-> -->
<!-- <\!--   author = {Scannell, Aidan and Ek, Carl Henrik and Richards, Arthur}, -\-> -->
<!-- <\!--   booktitle = {Proceedings of The 26th International Conference on Artificial Intelligence and Statistics}, -\-> -->
<!-- <\!--   year = {2023}} -\-> -->
<!-- <\!-- ``` -\-> -->
