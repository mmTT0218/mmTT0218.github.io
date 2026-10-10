---
title: '経歴'
date: 2026-10-09
type: landing

design:
  spacing: '5rem'

# 内容は data/authors/me.yaml（共通・英語）と data/ja/authors/me.yaml（日本語）で管理する
sections:
  - block: resume-experience
    content:
      username: me
    design:
      date_format: '2006年1月'
      is_education_first: true
  - block: resume-skills
    content:
      title: スキル
      username: me
  - block: resume-awards
    content:
      title: 助成金および奨学金
      username: me
  # 資格は data/ja/authors/certifications.yaml（英語版は data/authors/）を読む
  - block: resume-awards
    content:
      title: 資格
      username: certifications
---
