---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Implicitly Quantized Representations for Reinforcement Learning"
summary: ""

authors: [Aidan Scannell, Kalle Kujanpää, Yi Zhao, Arno Solin, Joni Pajarinen]
tags: ["reinforcement-learning", "machine-learning", "representation-learning", "robotics", "python", "pytorch", "research"]
categories: []
date: 2024-03-24

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
#links:
# - name: Follow
#   url: https://twitter.com/scannell_aidan
#   icon_pack: fab
#   icon: twitter

url_code: https://github.com/aidanscannell/iqrl
url_source: 
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
Learning representations for reinforcement learning (RL) has shown much promise for continuous control. 
In this project, we investigate using vector quantization to prevent representation collapse when learning representations for RL using a self-supervised latent-state consistency loss. 
