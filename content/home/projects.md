---
# An instance of the Portfolio widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: portfolio

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 65

title: Projects
subtitle: ''

# content:
#   # Filter on criteria
#   filters:
#     folders:
#       - project
#     tag: ''
#     category: ''
#     publication_type: ''
#     author: ''
#     exclude_featured: false
#     exclude_future: false
#     exclude_past: false
#   # Choose how many pages you would like to display (0 = all pages)
#   count: 2
#   # Choose how many pages you would like to offset by
#   offset: 0
#   # Page order: descending (desc) or ascending (asc) date.
#   order: desc

content:
  # Page type to display. E.g. project.
  page_type: project

  # Default filter index (e.g. 0 corresponds to the first `filter_button` instance below).
  # filter_default: 0
  filter_default: 1

  count: 2

  # Filter toolbar (optional).
  # Add or remove as many filters (`filter_button` instances) as you like.
  # To show all items, set `tag` to "*".
  # To filter by a specific tag, set `tag` to an existing tag name.
  # To remove the toolbar, delete the entire `filter_button` block.
  filter_button:
    - name: All
      tag: '*'
    - name: Research
      tag: research
    - name: Machine Learning
      tag: machine-learning
    - name: Robotics
      tag: robotics
    - name: Code
      tag: code
    # - name: Gaussian processes
    #   tag: gaussian-processes
    # - name: Python
    #   tag: python
    # - name: JAX
    #   tag: JAX
    # - name: Other
    #   tag: Demo

design:
  # Choose how many columns the section has. Valid values: '1' or '2'.
  columns: '1'
  # columns: '2'

  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   5 = Showcase
  view: 3

  # For Showcase view, flip alternate rows?
  flip_alt_rows: false
---
