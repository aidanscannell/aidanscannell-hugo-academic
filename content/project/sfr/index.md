---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Function-Space Bayesian Deep Learning for Sequential Learning"
summary: ""
authors: [Aidan Scannell, Riccardo Mereu, Paul Chang, Ella Tamir, Joni Pajarinen, Arno Solin]
tags: ["model-based-reinforcement-learning", "reinforcement-learning", "machine-learning", "bayesian-neural-networks", "gaussian-processes", "research"]
categories: []
date: 2024-01-10

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
links:
 - name: Website
   url: https://aaltoml.github.io/sfr/
   #icon_pack: fab
   #icon: twitter

url_code: "https://github.com/aaltoml/sfr"
url_pdf:  https://openreview.net/forum?id=2dhxxIKhqz&noteId=1udlCkoTob
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

Sequential learning paradigms pose challenges for gradient-based deep learning due to difficulties incorporating new data and retaining prior knowledge. While Gaussian processes elegantly tackle these problems, they struggle with scalability and handling rich inputs, such as images. To address these issues, we introduce a technique that converts neural networks from weight space to function space, through a dual parameterization. Our parameterization offers: (i) a way to scale function-space methods to large data sets via sparsification, (ii) retention of prior knowledge when access to past data is limited, and (iii) a mechanism to incorporate new data without retraining. Our experiments demonstrate that we can retain knowledge in continual learning and incorporate new data efficiently. We further show its strengths in uncertainty quantification and guiding exploration in model-based RL.
