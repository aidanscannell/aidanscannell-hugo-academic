---
# Documentation: https://wowchemy.com/docs/managing-content/

draft: false

title: "Entropy Regularized Task Representation Learning for Offline Meta-Reinforcement Learning"
authors: [Mohammadreza Nakhaei, Aidan Scannell, Joni Pajarinen]
# author_notes:
# - "Equal contribution"
# - "Equal contribution"
# date: 2023-04-27T21:01:09+03:00
date: 2025-01-20
#date: 2024-07-15
doi: 

# Schedule page publish date (NOT publication's date).
publishDate: 2023-10-19T16:01:09+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: "Proceedings of the AAAI Conference on Artificial Intelligence"
#publication_short: "AAAI 2025"


abstract: "Offline meta-reinforcement learning aims to equip agents with the ability to rapidly adapt to new tasks by training on data from a set of different tasks. Context-based approaches utilize a history of state-action-reward transitions – referred to as the context – to infer representations of the current task, and then condition the agent, i.e., the policy and value function, on the task representations. Intuitively, the better the task representations capture the underlying tasks, the better the agent can generalize to new tasks. Unfortunately, contextbased approaches suffer from distribution mismatch, as the context in the offline data does not match the context at test time, limiting their ability to generalize to the test tasks. This leads to the task representations overfitting to the offline training data. Intuitively, the task representations should be independent of the behavior policy used to collect the offline data. To address this issue, we approximately minimize the mutual information between the distribution over the task representations and behavior policy by maximizing the entropy of behavior policy conditioned on the task representations. We validate our approach in MuJoCo environments, showing that compared to baselines, our task representations more faithfully represent the underlying tasks, leading to outperforming prior methods in both in-distribution and out-of-distribution tasks."

# Summary. An optional shortened abstract.
summary: ""

tags: ["reinforcement-learning","offline-rl","meta-rl","representation-learning"]
categories: []
featured: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
#  - name: Website
#    url: https://aaltoml.github.io/sfr
# - name: Follow
#   url: https://twitter.com/scannell_aidan/status/1617792928646311937
#   icon_pack: fab
#   icon: twitter


url_pdf: https://arxiv.org/pdf/2412.14834
url_code: https://github.com/MohammadrezaNakhaei/ER-TRL
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
