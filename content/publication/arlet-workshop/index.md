---
# Documentation: https://wowchemy.com/docs/managing-content/

draft: false

title: Quantized Representations Prevent Dimensional Collapse in Self-predictive RL
authors: [Aidan Scannell, Kalle Kujanpää, Yi Zhao, Mohammadreza Nakhaei, Arno Solin, Joni Pajarinen]
# author_notes:
# - "Equal contribution"
# - "Equal contribution"
# date: 2023-04-27T21:01:09+03:00
date: 2024-06-04
doi: 

# Schedule page publish date (NOT publication's date).
publishDate: 2023-10-19T16:01:09+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
#publication: "Proceedings of the 41st International Conference on Machine Learning (ICML)"
publication: "ICML Workshop on Aligning Reinforcement Learning Experimentalists and Theorists (ARLET)"
#publication_short: "ICML ARLET 2024"


abstract: "Learning representations for reinforcement learning (RL) has shown much promise for continuous control. We propose an efficient representation learning method using only a self-supervised latent-state consistency loss. Our approach employs an encoder and a dynamics model to map observations to latent states and predict future latent states, respectively. We achieve high performance and prevent representation collapse by quantizing the latent representation such that the rank of the representation is empirically preserved. Our method, named iQRL: implicitly Quantized Reinforcement Learning, is straightforward, compatible with any model-free RL algorithm, and demonstrates excellent performance by outperforming other recently proposed representation learning methods in continuous control benchmarks from DeepMind Control Suite."

# Summary. An optional shortened abstract.
summary: ""

tags: ["reinforcement-learning", "representation-learning", "self-supervised-learning", "continuous-control"]
categories: []
featured: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
# - name: Website
#   url: https://aaltoml.github.io/sfr
# - name: Follow
#   url: https://twitter.com/scannell_aidan/status/1617792928646311937
#   icon_pack: fab
#   icon: twitter


url_pdf: 
url_code: 
url_dataset:
url_poster: 
url_project:
url_slides:
url_source: 
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
