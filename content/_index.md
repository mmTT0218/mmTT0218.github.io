---
title: ''
summary: ''
date: 2026-10-09
type: landing

sections:
  # ── プロフィール（data/authors/me.yaml と data/ja/authors/me.yaml を参照）
  - block: resume-biography-3
    content:
      username: me
      text: ''
      # CV をダウンロードさせる場合は，PDF を static/uploads/ に置いて
      # 下の3行のコメントを外す
      #button:
      #  text: CV をダウンロード
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

  # ── 研究紹介（本文は履歴書の研究概要をもとにしています）
  - block: markdown
    content:
      title: '研究テーマ'
      subtitle: 'パララックスバリア方式 裸眼3Dディスプレイ'
      text: |-
        専用の眼鏡を使わずに立体映像を見られる裸眼3Dディスプレイの画質改善に取り組んでいます。
        対象とする方式では、パララックスバリアと呼ばれる光学部品によって、左右の目に異なる映像を提示します。
        しかし、この部品とディスプレイ画面の貼り合わせ時に回転ズレが生じると、左右の映像が混ざり、二重像が発生するという課題があります。

        そこで、回転ズレに応じて映像を補正する手法と、その補正に必要な回転ズレ量を撮影画像から推定する手法を提案しました。
        特に、画質劣化の原因となる縞模様（モアレ）を、回転ズレを測る手がかりとして活用した点が特徴です。
        撮影したモアレの周期と方向を画像解析し、推定した回転ズレ量に基づいて映像を補正することで、
        左右の映像が混ざる現象（クロストーク）を低減しました。

        今後は、微小な回転ズレが縞模様の大きな変化として現れるモアレの特性を活用し、より高感度で安定した推定手法へ発展させます。
        あわせて、推定精度や再現性、適用条件を検証する予定です。
        将来的には、脱着可能なパララックスバリアに本手法を適用し、
        必要に応じて2D表示と3D表示を切り替えられる裸眼3Dディスプレイの実現を目指しています。
    design:
      columns: '1'

  # ── 主要業績（front matter に featured: true を付けたもの）
  - block: collection
    id: papers
    content:
      title: 業績
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2
      show_read_time: false

  # ── 業績一覧
  - block: collection
    id: publications
    content:
      title: 文献リスト
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation

  # ── 学会発表の一覧を別枠で出したい場合は，content/events/ に項目を追加して
  #    下のコメントを外してください（現在は業績一覧に統合しています）
  #- block: collection
  #  id: talks
  #  content:
  #    title: 学会発表
  #    filters:
  #      folders:
  #        - events
  #  design:
  #    view: card

  # ── お知らせを出したい場合は，content/blog/ に記事を追加して
  #    下のコメントを外してください
  #- block: collection
  #  id: news
  #  content:
  #    title: お知らせ
  #    page_type: blog
  #    count: 5
  #    order: desc
  #  design:
  #    view: card
---
