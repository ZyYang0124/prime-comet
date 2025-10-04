---
# Leave the homepage title empty to use the site title
title:
date: 2022-10-24
type: landing

sections:
  - block: hero
    content:
      title: |
        Welcome Arachnology
        Research Group
      image:
        filename: lab.jpg
      text: |
        <br>
        
        Our lab is dedicated to the **integrative study of Arachnida**. 
        
        We combine approaches from morphological taxonomy, molecular phylogenetics, trait evolution, and comparative genomics to unravel the diversity, evolutionary history, and adaptive innovations of arachnids.
  
  - block: collection
    content:
      title: <b>Biodiversity and Systematics</b>
      subtitle:
      text: |
        <p><b>Biodiversity forms the foundation of processes that sustain all life on Earth. </b> Accurate description and classification are critical to understanding this diversity.</p>

        <p>Our laboratory is dedicated to the discovery and systematics of diverse arachnid lineages, with primary expertise in:</p>

        <ul class="mb-4">
          <li><strong><a href="/Tour/#Spider">Spiders</a></strong> (Araneae)</li>
          <li><strong>Pseudoscorpions</strong> (Pseudoscorpiones)</li>
          <li><strong>Harvestmen</strong> (Opiliones)</li>
          <li><strong>Scorpions</strong> (Scorpiones)</li>
          <li><strong>Sun spiders / Camel spiders</strong> (Solifugae)</li>
          <li><strong>Short-tailed whipscorpions</strong> (Schizomida)</li>
          <li><strong>Whip spiders / Tailless whipscorpions</strong> (Amblypygi)</li>
          <li><strong>Whip scorpions / Vinegaroons</strong> (Thelyphonida)</li>
        </ul>

        <p>Through integrative approaches—including field expeditions, morphological analyses, and molecular phylogenetics—we aim to discover new species, refine classification systems, and contribute to global biodiversity conservation strategies.</p>

      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: post
    design:
      view: card
      columns: '1'
  
  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: coders.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen

  - block: collection
    content:
      title: Latest Preprints
      text: ""
      count: 5
      filters:
        folders:
          - publication
        publication_type: 'article'
    design:
      view: citation
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
    design:
      columns: '1'
---