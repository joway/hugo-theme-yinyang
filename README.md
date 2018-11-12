# YinYang

[YinYang](https://en.wikipedia.org/wiki/Yin_and_yang) is a black-white theme for [Hugo](https://gohugo.io/).

[Demo](https://blog.joway.io)

## Feature

- minimalist
- multi-language support
- [disqus](https://disqus.com) support

## Installation

[Install and Use Theme](https://gohugo.io/themes/installing-and-using-themes/)

## Configuration

#### config.toml

```
baseURL = "https://blog.joway.io/"
languageCode = "en-us"
title = "Joway's Blog"
theme = "yinyang"
DefaultContentLanguage = "cn"

[author]
  name = "Joway Wang"
  homepage = "https://joway.io/"

[languages]
  [languages.en]
    contentDir = "content/en"
    languageName = "English"
    weight = 1
  [languages.cn]
    contentDir = "content/cn"
    languageName = "Chinese"
    weight = 2

[params]
disqus = "joway" # disqus account name
extraHead = '<script async src="https://www.googletagmanager.com/gtag/js?id=UA-53624533-8"></script><script src="https://joway.io/analytics.js"></script>'
[[params.socials]]
name = "About Me"
link = "https://joway.io"
[[params.socials]]
name = "Github"
link = "https://github.com/joway"
```
