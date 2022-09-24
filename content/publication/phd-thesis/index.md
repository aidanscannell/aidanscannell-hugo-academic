---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Bayesian Learning for Control in Multimodal Dynamical Systems"
authors: ["Aidan Scannell"]
date: 2022-09-24T23:02:01+03:00
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: 2022-09-24T23:02:01+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["7"]

# Publication name and optional abbreviated publication name.
publication: "University of Bristol"
publication_short: ""

abstract: |
      Over the last decade, *learning-based control* has become a popular paradigm for controlling dynamical systems. Although recent algorithms can find high-performance controllers, they typically only consider unimodal systems and cannot correctly identify multimodal dynamical systems. The main goal of this thesis is to control *unknown*, *multimodal* dynamical systems, to a target state, whilst *avoiding inoperable or undesirable dynamics modes*. Further to this, deploying learning algorithms in the real world requires handling the uncertainties inherent to the system, as well as the uncertainties arising from learning from observations. To this end, we consider the model-based reinforcement learning (MBRL) setting, where an explicit dynamics model -- that includes uncertainties -- is used to plan trajectories to a target state. 
        
        Motivated by synergising model learning and control, we introduce a Mixtures of Gaussian Process Experts (MoGPE) method for learning dynamics models, which infers latent structure regarding how systems switch between their underlying dynamics modes. We then present three trajectory optimisation algorithms which, given this learned dynamics model, find trajectories to a target state with *mode remaining guarantees*. Initially, the agent’s dynamics model will be highly *uncertain* — due to a lack of training observations — so these algorithms cannot guarantee mode remaining navigation with high confidence. When this is the case, the agent actively explores its environment, collects data and updates its dynamics model. We introduce an explorative trajectory optimisation algorithm that explicitly reasons about the uncertainties in the dynamics model. As a result, it can explore the environment whilst guaranteeing that the agent remains in the desired dynamics mode with high probability. Finally, we consolidate the work in this thesis into a MBRL algorithm, which solves the mode remaining navigation problem, whilst guaranteeing that the controlled system remains in the desired dynamics mode with a high probability.


# Summary. An optional shortened abstract.
summary: "Mode remaining navigation (and exploration) in unknown multimodal dynamical systems via model-based reinforcement learning."

tags: ["machine-learning", "reinforcement-learning", "gaussian-processes", "probabilistic-modelling", "approximate-inference", "variational-inference", "geometry", "control", "ai", "JAX", "TensorFlow", "python"]
categories: []
featured: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

# TODO update pdf to point to final submission
url_pdf: https://github.com/aidanscannell/phd-thesis/releases/download/initial-submission/phd-thesis-signed-submitted.pdf
url_code: https://github.com/aidanscannell/modeopt
url_dataset:
url_poster:
url_project:
url_slides: talk/phd-thesis-bayesian-learning-for-control-in-multimodal-dynamical-systems/slides.pdf
url_source: https://github.com/aidanscannell/phd-thesis
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
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
