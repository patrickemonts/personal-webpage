---
title: Optimising Entanglement Distribution Policies under Classical Communication
  Constraints Assisted by Reinforcement Learning

# Authors
# A YAML list of author names
# If you created a profile for a user (e.g. the default `admin` user at `content/authors/admin/`), 
# write the username (folder name) here, and it will be replaced with their full name and linked to their profile.
authors:
- Jan Li
- Tim Coopmans
- Patrick Emonts
- Kenneth Goodenough
- Jordi Tura
- Evert van Nieuwenburg

# Author notes (such as 'Equal Contribution')
# A YAML list of notes for each author in the above `authors` list
author_notes: []

date: '2024-12-01'

# Date to publish webpage (NOT necessarily Bibtex publication's date).
publishDate: '2024-12-29T17:02:47.457934Z'

# Publication type.
# A single CSL publication type but formatted as a YAML list (for Hugo requirements).
publication_types:
- 0

# Publication name and optional abbreviated publication name.
publication: '*arXiv*'
publication_short: ''

doi: 10.48550/arXiv.2412.06938

abstract: "Quantum repeaters play a crucial role in the effective distribution of
  entanglement over long distances. The nearest-future type of quantum repeater requires
  two operations: entanglement generation across neighbouring repeaters and entanglement
  swapping to promote short-range entanglement to long-range. For many hardware setups,
  these actions are probabilistic, leading to longer distribution times and incurred
  errors. Significant efforts have been vested in finding the optimal entanglement-distribution
  policy, i.e. the protocol specifying when a network node needs to generate or swap
  entanglement, such that the expected time to distribute long-distance entanglement
  is minimal. This problem is even more intricate in more realistic scenarios, especially
  when classical communication delays are taken into account. In this work, we formulate
  our problem as a Markov decision problem and use reinforcement learning (RL) to
  optimise over centralised strategies, where one designated node instructs other
  nodes which actions to perform. Contrary to most RL models, ours can be readily
  interpreted. Additionally, we introduce and evaluate a fixed local policy, the `predictive
  swap-asap' policy, where nodes only coordinate with nearest neighbours. Compared
  to the straightforward generalization of the common swap-asap policy to the scenario
  with classical communication effects, the `wait-for-broadcast swap-asap' policy,
  both of the aforementioned entanglement-delivery policies are faster at high success
  probabilities. Our work showcases the merit of considering policies acting with
  incomplete information in the realistic case when classical communication effects
  are significant."

# Summary. An optional shortened abstract.
summary: ''

tags:
- Quantum Physics

# Display this page in a list of Featured pages?
featured: false

# Links
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

# Publication image
# Add an image named `featured.jpg/png` to your page's folder then add a caption below.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects: ['internal-project']` links to `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []
links:
- name: arXiv
  url: https://arxiv.org/abs/2412.06938
---