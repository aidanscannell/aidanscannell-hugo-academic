---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "PhD Thesis: Bayesian Learning for Control in Multimodal Dynamical Systems"
event: 
event_url:
location: "Aalto University, Finland"
address:
  street:
  city:
  region:
  postcode:
  country:
summary:
abstract: |
      Over the last decade, *learning-based control* has become a popular paradigm for controlling dynamical systems. Although recent algorithms can find high-performance controllers, they typically only consider unimodal systems and cannot correctly identify multimodal dynamical systems. The main goal of this thesis is to control *unknown*, *multimodal* dynamical systems, to a target state, whilst *avoiding inoperable or undesirable dynamics modes*. Further to this, deploying learning algorithms in the real world requires handling the uncertainties inherent to the system, as well as the uncertainties arising from learning from observations. To this end, we consider the model-based reinforcement learning (MBRL) setting, where an explicit dynamics model -- that includes uncertainties -- is used to plan trajectories to a target state. 
        
        Motivated by synergising model learning and control, we introduce a Mixtures of Gaussian Process Experts (MoGPE) method for learning dynamics models, which infers latent structure regarding how systems switch between their underlying dynamics modes. We then present three trajectory optimisation algorithms which, given this learned dynamics model, find trajectories to a target state with *mode remaining guarantees*. Initially, the agent’s dynamics model will be highly *uncertain* — due to a lack of training observations — so these algorithms cannot guarantee mode remaining navigation with high confidence. When this is the case, the agent actively explores its environment, collects data and updates its dynamics model. We introduce an explorative trajectory optimisation algorithm that explicitly reasons about the uncertainties in the dynamics model. As a result, it can explore the environment whilst guaranteeing that the agent remains in the desired dynamics mode with high probability. Finally, we consolidate the work in this thesis into a MBRL algorithm, which solves the mode remaining navigation problem, whilst guaranteeing that the controlled system remains in the desired dynamics mode with a high probability.

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: 2022-09-13T11:00:00+03:00
date_end: 2022-09-13T12:00:00+03:00
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: 2022-09-13T11:00:00+03:00

authors: []
tags: []

# Is this a featured talk? (true/false)
featured: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/scannell_aidan

# Optional filename of your slides within your talk's folder or a URL.
url_slides: talk/phd-thesis-bayesian-learning-for-control-in-multimodal-dynamical-systems/slides.pdf

url_code: "https://github.com/aidanscannell/modeopt.git"
url_pdf: talk/phd-thesis-bayesian-learning-for-control-in-multimodal-dynamical-systems/slides.pdf
url_video:

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
