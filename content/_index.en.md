---
title: ''
summary: ''
date: 2026-10-09
type: landing

sections:
  - block: resume-biography-3
    content:
      username: me
      text: ''
      #button:
      #  text: Download CV
      #  url: uploads/cv.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      background:
        gradient_mesh:
          enable: true
      name:
        size: md
      avatar:
        size: medium
        shape: circle

  - block: markdown
    content:
      title: 'Research'
      subtitle: 'Parallax-Barrier Autostereoscopic 3D Displays'
      text: |-
        I work on improving the image quality of autostereoscopic 3D displays, which let viewers
        see stereoscopic images without special glasses. In the approach I study, an optical
        component called a parallax barrier presents a different image to each eye. When the
        barrier is bonded to the display panel, however, a small rotational misalignment makes
        the left and right images blend into each other and produces a doubled image.

        To address this, I have proposed a method that corrects the displayed images according
        to the misalignment, together with a method that estimates the misalignment angle from a
        captured photograph. The distinguishing idea is to use the moiré fringes — normally the
        very cause of the degradation — as the cue for measuring the misalignment. By analysing
        the period and orientation of the captured moiré and correcting the parallax images with
        the estimated angle, crosstalk between the left and right views is reduced.

        Next, I plan to exploit the property that a minute rotation appears as a large change in
        the moiré pattern, developing a more sensitive and more stable estimation method, and to
        evaluate its accuracy, reproducibility and operating conditions. In the longer term, I aim
        to apply the method to a detachable parallax barrier, so that a single display can switch
        between 2D and 3D presentation as needed.
    design:
      columns: '1'

  - block: collection
    id: papers
    content:
      title: Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2
      show_read_time: false

  - block: collection
    id: publications
    content:
      title: Bibliography
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation

  #- block: collection
  #  id: talks
  #  content:
  #    title: Talks
  #    filters:
  #      folders:
  #        - events
  #  design:
  #    view: card

  #- block: collection
  #  id: news
  #  content:
  #    title: News
  #    page_type: blog
  #    count: 5
  #    order: desc
  #  design:
  #    view: card
---
