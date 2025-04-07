---
# Leave the homepage title empty to use the site title
title:
date: 2022-10-24
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: Biography
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
  - block: experience
    id: education
    content:
      title: Education
      # Date format for experience
      #   Refer to https://wowchemy.com/docs/customization/#date-format
      date_format: Jan 2006
      # Experiences.
      #   Add/remove as many `experience` items below as you like.
      #   Required fields are `title`, `company`, and `date_start`.
      #   Leave `date_end` empty if it's your current employer.
      #   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
      items:
        - title: CZS Junior Research Group Leader
          date_start: '2025-04-01' 
          description: |2
            Focus on 
            * Tensor Networks
            * Quantum Information
            * Lattice Gauge Theories
          company: Ulm University, Institute for Complex Quantum Systems
          company_logo: logo-ulm
          company_url: https://www.uni-ulm.de/en/nawi/institute-for-complex-quantum-systems/welcome/
        - title: Postdoctoral Researcher
          date_start: '2022-01-07' 
          end_date: '2025-03-31' 
          description: |2
            Focus on 
            * Tensor Networks
            * Quantum Information
            * Lattice Gauge Theories
          company: Leiden University, aQa group
          company_logo: logo-leiden
          company_url: https://www.universiteitleiden.nl/en/science/physics
        - title: PhD in Physics
          date_start: '2017-10-15'
          date_end: '2022-09-23'
          description: |2
            Focus on 
            * Tensor Networks
            * Lattice Gauge Theories

            Thesis: ["Algorithms for Hamiltonian Lattice Gauge Theories"](https://mediatum.ub.tum.de/1657413)
          company: Max-Planck Institute of Quantum Optics, TU Munich
          company_logo: logo-max-planck
          company_url: https://www.mpq.mpg.de/en
        - title: MSc in Management
          date_start: '2018-10-01'
          date_end: '2020-08-01'
          description: |2
            Thesis: "Causal Inference in Applied Economics: An Example of Naming Strategies in German Food Processing"
          company: TU Munich
          company_logo: logo-tum
          company_url: https://www.tum.de/en/ 
        - title: MSc in Physics
          date_start: '2015-09-01'
          date_end: '2017-08-01'
          description: |2
            Focus on
            * quantum Monte Carlo
            * condensed matter physics, especially spin systems
            Thesis: "Monte Carlo Methods for the Quantum Ising Model on Frustrated Lattices"
          company: RWTH Aachen
          company_logo: logo-rwth
          company_url: https://www.rwth-aachen.de/go/id/a/?lidx=1
        - title: BSc in Physics
          date_start: '2012-10-01'
          date_end: '2015-09-01'
          description: |2
            Thesis: "Lateral Etching of Graphene Heterostructures"
          company: RWTH Aachen
          company_logo: logo-rwth
          company_url: https://www.rwth-aachen.de/go/id/a/?lidx=1
    design:
      columns: '2'
  - block: collection
    id: publications
    content:
      title: Recent Publications
      text: |-
        {{% callout note %}}
        You can also [search](./publication/) for a certain publication
        {{% /callout %}}
      filters:
        folders:
          - publication
        exclude_featured: true
    design:
      columns: '2'
      view: citation

  - block: collection
    id: posts
    content:
      title: Recent Posts
      subtitle: ''
      text: ''
      # Choose how many pages you would like to display (0 = all pages)
      count: 5
      # Filter on criteria
      filters:
        folders:
          - post
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
    design:
      # Choose a layout view
      view: compact
      columns: '2'

  - block: contact
    id: contact
    content:
      title: Contact
      subtitle:
      text: |-
        If you have questions or ideas feel free to contact me.
      # Contact (add or remove contact options as necessary)
      email: patrick.emonts@uni-ulm.de
#      phone: 888 888 88 88
      # appointment_url: 'https://calendly.com'
      address:
        street: Albert-Einstein-Allee 11
        city:  89069 Ulm
        country: Germany
        country_code: DE
    #   directions: Enter Building 1 and take the stairs to Office 200 on Floor 2
    # office_hours:
    #   - 'Monday 10:00 to 13:00'
    #   - 'Wednesday 09:00 to 10:00'
      contact_links:
      # Automatically link email and phone or display as text?
      autolink: true
    design:
      columns: '2'
---
