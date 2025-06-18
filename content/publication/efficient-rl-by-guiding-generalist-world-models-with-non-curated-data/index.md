---
# Documentation: https://wowchemy.com/docs/managing-content/

draft: false

title: Efficient Reinforcement Learning by Guiding Generalist World Models with Non-Curated Data
authors: [Yi Zhao, Aidan Scannell, Wenshuai Zhao, Cui Yuxin, Tianyu Cui, Le Chen, Arno Solin, Juho Kannala, Joni Pajarinen]
# author_notes:
# date: 2023-04-27T21:01:09+03:00
date: 2025-05-18
doi: 

# Schedule page publish date (NOT publication's date).
publishDate: 2025-05-18T16:01:09+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: "arXiv preprint arXiv:2502.19544v2"
#publication_short: ""


abstract: "Leveraging offline data is a promising way to improve the sample efficiency of online reinforcement learning (RL). This paper expands the pool of usable data for offline-to-online RL by leveraging abundant non-curated data that is reward free, of mixed quality, and collected across multiple embodiments. Although learning a world model appears promising for utilizing such data, we find that naive fine-tuning fails to accelerate RL training on many tasks. Through careful investigation, we attribute this failure to the distributional shift between offline and online data during fine-tuning. To address this issue and effectively use the offline data, we propose two essential techniques: i) experience rehearsal and ii) execution guidance. With these modifications, the non-curated offline data substantially improves RL’s sample efficiency. Under limited sample budgets, our method achieves a 102.8% relative improvement in aggregate score over learning from-scratch baselines across 72 visuomotor tasks spanning 6 embodiments. On challenging tasks such as locomotion and robotic manipulation, it outperforms prior methods that utilize offline data by a decent margin."

# Summary. An optional shortened abstract.
summary: ""

tags: []
categories: []
featured: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Website
#   url: https://aaltoml.github.io/sfr
# - name: Follow
#   url: https://twitter.com/scannell_aidan/status/1617792928646311937
#   icon_pack: fab
#   icon: twitter


url_pdf: https://arxiv.org/abs/2502.19544
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
