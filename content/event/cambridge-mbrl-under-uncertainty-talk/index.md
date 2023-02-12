---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Model-based reinforcement learning under uncertainty"
#event: [ML@CL](https://mlatcl.github.io)
event_url:
location: University of Cambridge
address: 
  street:
  city:
  region:
  postcode:
  country:
summary:
abstract: |
  In this talk I’ll present our recent paper that has just been accepted into AISTATS 2023, titled [Mode-Constrained Model-Based Reinforcement Learning via Gaussian Processes](./publication/mode-constrained-mbrl). I’ll then present some of my ongoing research in the area of model-based reinforcement learning under uncertainty.

  **Paper abstract:**
  Model-based reinforcement learning (MBRL) algorithms do not typically consider environments – subject to multiple dynamics modes – where it is beneficial to avoid inoperable or undesirable dynamics modes. We present a MBRL algorithm that avoids entering such inoperable or undesirable dynamics modes, by constraining the controlled system to remain in a single dynamics mode with high probability. This is a particularly difficult problem because the mode constraint is unknown a priori. We propose to jointly infer the mode constraint, along with the underlying dynamics modes. Importantly, our method infers latent structure that our planning scheme leverages to 1) enforce the mode constraint with high probability, and to 2) escape the local optima induced by the mode constraint by targeting exploration where the mode constraint's epistemic uncertainty is high. We validate our method by showing that it can navigate a simulated quadcopter – subject to a turbulent dynamics mode – to a target state, whilst remaining in the desired dynamics mode with high probability.

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: 2023-02-13T11:30:05Z
date_end: 2023-02-13T12:30:05Z
all_day: false

# Schedule page publish date (NOT event date).
publishDate: 2023-02-12T19:10:05Z

authors: ["Aidan Scannell"]
tags: ["machine-learning", "model-based-reinforcement-learning", "reinforcement-learning", "gaussian-processes", "bayesian-inference", "probabilistic-modelling", "talk"]

# Is this a featured event? (true/false)
featured: false

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

# Optional filename of your slides within your event's folder or a URL.
url_slides: https://docs.google.com/presentation/d/1orhgqPB1teHPGjedzvTQCrlIaRzfkGBiDYsNjOc5LQ8/edit?usp=sharing

url_code:
url_pdf:
url_video:

# Markdown Slides (optional).
#   Associate this event with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: [mode-constrained-model-based-reinforcement-learning]
---
