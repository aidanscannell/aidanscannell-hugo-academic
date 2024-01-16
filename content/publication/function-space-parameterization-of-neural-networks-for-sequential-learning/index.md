---
# Documentation: https://wowchemy.com/docs/managing-content/

draft: false

title: "Function-space Prameterization of Neural Networks for Sequential Learning"
authors: [Aidan Scannell, Riccardo Mereu, Paul Chang, Ella Tamir, Joni Pajarinen, Arno Solin]
author_notes:
- "Equal contribution"
- "Equal contribution"
# date: 2023-04-27T21:01:09+03:00
date: 2023-10-19
doi: 

# Schedule page publish date (NOT publication's date).
publishDate: 2023-10-19T16:01:09+03:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: "The Twelth International Conference on Learning Representations"
publication_short: "ICLR 2024"


abstract: "Sequential learning paradigms pose challenges for gradient-based deep learning due to difficulties incorporating new data and retaining prior knowledge. While Gaussian processes elegantly tackle these problems, they struggle with scalability and handling rich inputs, such as images. To address these issues, we introduce a technique that converts neural networks from weight space to function space, through a dual parameterization. Our parameterization offers: (i) a way to scale function-space methods to large data sets via sparsification, (ii) retention of prior knowledge when access to past data is limited, and (iii) a mechanism to incorporate new data without retraining. Our experiments demonstrate that we can retain knowledge in continual learning and incorporate new data efficiently. We further show its strengths in uncertainty quantification and guiding exploration in model-based RL."

# Summary. An optional shortened abstract.
summary: ""

tags: ["neural-networks", "bayesian-deep-learning", "gaussian-processes", "bayesian-inference", "machine-learning", "approximate-inference"]
categories: []
featured: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
 - name: Website
   url: https://aaltoml.github.io/sfr
# - name: Follow
#   url: https://twitter.com/scannell_aidan/status/1617792928646311937
#   icon_pack: fab
#   icon: twitter


url_pdf: https://openreview.net/pdf?id=2dhxxIKhqz
url_code: https://github.com/AaltoML/sfr
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
