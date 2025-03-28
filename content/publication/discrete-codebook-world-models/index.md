---
# Documentation: https://wowchemy.com/docs/managing-content/

draft: false

title: Discrete Codebook World Models for Continuous Control
authors: [Aidan Scannell, Mohammadreza Nakhaei, Kalle Kujanpää, Yi Zhao, Kevin Luck, Arno Solin, Joni Pajarinen]
# author_notes:
# - "Equal contribution"
# - "Equal contribution"
# date: 2023-04-27T21:01:09+03:00
date: 2025-01-28
doi: 

# Schedule page publish date (NOT publication's date).
publishDate: 2023-10-19T16:01:09+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: "The Thirteenth International Conference on Learning Representations (ICLR)"
#publication_short: "ICLR 2024"


abstract: "In reinforcement learning (RL), world models serve as internal simulators, enabling agents to predict environment dynamics and future outcomes in order to make informed decisions. While previous approaches leveraging discrete latent spaces, such as DreamerV3, have demonstrated strong performance in discrete action settings and visual control tasks, their comparative performance in state-based continuous control remains underexplored. In contrast, methods with continuous latent spaces, such as TD-MPC2, have shown notable success in state-based continuous control benchmarks. In this paper, we demonstrate that modeling discrete latent states has benefits over continuous latent states and that discrete codebook encodings are more effective representations for continuous control, compared to alternative encodings, such as one-hot and label-based encodings. Based on these insights, we introduce DCWM: Discrete Codebook World Model, a self-supervised world model with a discrete and stochastic latent space, where latent states are codes from a codebook. We combine DCWM with decision-time planning to get our model-based RL algorithm, named DC-MPC: Discrete Codebook Model Predictive Control, which performs competitively against recent state-of-the-art algorithms, including TD-MPC2 and DreamerV3, on continuous control benchmarks. See our project website [www.aidanscannell.com/dcmpc](https://www.aidanscannell.com/dcmpc)."

# Summary. An optional shortened abstract.
summary: ""

tags: ["world-models", "reinforcement-learning", "representation-learning", "self-supervised-learning", "continuous-control"]
categories: []
featured: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
- name: Website
  url: /dcmpc
# - name: Follow
#   url: https://twitter.com/scannell_aidan/status/1617792928646311937
#   icon_pack: fab
#   icon: twitter


url_pdf: https://openreview.net/forum?id=lfRYzd8ady
url_code: https://github.com/aidanscannell/dcmpc
url_dataset:
url_poster: 
url_project:
url_slides: slides.pdf
url_source: 
url_video: https://recorder-v3.slideslive.com/?share=98948&s=31e7f935-779c-446d-962d-be9ff1ddc366

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
