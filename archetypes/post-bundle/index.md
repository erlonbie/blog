---
title: {{ slicestr (replace .Name "-" " ") 11 | title }}
date: {{ dateFormat "2006-01-02" .Date }}
canonicalURL: https://erlonbie.github.io/posts/{{.Name}}
tags: []
cover:
  image: images/cover.png
---
