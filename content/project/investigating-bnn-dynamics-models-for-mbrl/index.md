---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Investigating Bayesian Neural Network Dynamics Models for Model-Based Reinforcement Learning"
summary: ""
authors: [Aidan Scannell, Arno Solin, Joni Pajarinen]
tags: ["model-based-reinforcement-learning", "reinforcement-learning", "machine-learning", "bayesian-neural-networks", "gaussian-processes", "research"]
categories: []
date: 2022-11-19T15:44:57+02:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: "https://github.com/aidanscannell/unc-mbrl"
url_pdf: "project/investigating-bnn-dynamics-models-for-mbrl/poster-finnish-ai-day-2022.pdf"
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

This project seeks to evaluate and compare different approaches for learning dynamics models in model-based RL.
In particular, we plan to compare different approximate inference techniques (e.g. Laplace approximation, MC dropout, variational inference), as well as ensemble methods, to understand why they either succeed or fail in different environments.

<!-- In particular, we are interested in understanding why ensembles of neural networks appear to work well but also in what scenarios they fail. -->
<!-- This project seeks to evaluate and compare different approximate inference schemes for learning dynamics models in model-based RL using Bayesian neural networks. -->


<!-- different approximate inference techniques (e.g. Laplace approximation, MC dropout), as well as ensemble methods, to understand why they either succeed or fail in different environments. -->

<!-- learning dynamics models for model-based RL using Bayesian neural networks and comparing them to ensemble methods. In particular, we seek to compare different approximate inference techniques (e.g. Laplace approximation, MC dropout), as well as ensemble methods, to understand why they either succeed or fail in different environments. -->
<!-- This work seeks to investigate approximate -->

<!-- Model-based reinforcement learning (MBRL) algorithms are more sample-efficient than their model-free counterparts. However, MBRL algorithms often fail, or perform poorly, due to their decision-making strategy (e.g. planning or policy optimization) exploiting inaccuracies in the learned dynamics model. These inaccuracies arise because the dynamics model is learned from a state transition data set representing only a small subset of the environment. As such, the dynamics model cannot be confident in making predictions far away from these state transitions. This concept is known as epistemic uncertainty. In the limit of infinite data, i.e. a data set containing all possible state transitions for an environment, the dynamics model's epistemic uncertainty is reduced. However, in MBRL an agent should only visit regions of the state-action space which lead to high rewards. As a result, an agent's dynamics model will always be subject to epistemic uncertainty. If the dynamics model knows what it does not know, this information can be used to prevent the decision-making strategy from exploiting the model's inaccuracies. Based on this intuition, recent algorithms leverage ensembles of neural networks to quantify the epistemic uncertainty associated with learning dynamics models from observations, i.e. to quantify what it does not know.  -->

<!-- In this work, we are interested in learning dynamics models using Bayesian neural networks and comparing them to ensemble methods. In particular, we seek to compare different approximate inference techniques (e.g. Laplace approximation, MC dropout), as well as ensemble methods, to understand why they either succeed or fail in different environments. -->
