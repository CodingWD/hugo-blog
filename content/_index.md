---
title: 欢迎来到我的博客
date: 2024-01-15
type: landing

sections:
  - block: hero
    content:
      title: |
        欢迎来到
        **我的个人博客**
      image:
        filename: welcome.jpg
      text: |
        这里是我分享技术见解、生活感悟和学习心得的地方。
        
        使用Hugo Blox Builder构建，支持丰富的内容展示方式。
    design:
      background:
        gradient_end: '#1976d2'
        gradient_start: '#004ba0'
        text_color_light: true
        
  - block: about.biography
    id: about
    content:
      title: 关于我
      username: admin
      
  - block: collection
    id: posts
    content:
      title: 最新文章
      subtitle: ''
      text: ''
      count: 5
      filters:
        folders:
          - posts
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      offset: 0
      order: desc
    design:
      columns: '2'
      view: compact
      
  - block: tag_cloud
    content:
      title: 热门标签
    design:
      columns: '2'
---