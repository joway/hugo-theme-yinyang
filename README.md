# YinYang

[YinYang](https://en.wikipedia.org/wiki/Yin_and_yang) is a black-white theme for [Hugo](https://gohugo.io/).

[**Demo**](https://blog.joway.io)

## Features

- **Gallery Layout Type** - Special content type with responsive image grid
- **Code Copy Button** - One-click copy-to-clipboard for code blocks
- **Disqus Comments** - Integration with automatic ad removal
- **Year-based Archives** - Posts grouped by year with date catalogs
- **CJK Typography** - Optimized line-height for Chinese/Japanese/Korean text
- **SEO** - JSON-LD structured data, Open Graph, and Twitter Cards support

## Screenshot

![](./images/screenshot.png)

## Installation

From the root of your site:

```shell
git submodule add https://github.com/joway/hugo-theme-yinyang.git themes/yinyang
```

Change `config.toml`:

```toml
theme = "yinyang"
```

## Configuration

### Theme Parameters

| Parameter | Type | Description | Default |
|-----------|------|-------------|---------|
| `headTitle` | string | Site title shown in header | Falls back to `author.name` |
| `mainSections` | array | Sections to include in archives | `["posts"]` |
| `disqus` | string | Disqus account name | - |
| `lazyImage` | boolean | Enable lazy loading for images | `false` |
| `enableCopyCode` | boolean | Enable copy button on code blocks | `false` |
| `postHeaderContent` | string | HTML content above post body | - |
| `postFooterContent` | string | HTML content below post body | - |
| `postAds` | string | Ads HTML in post footer | - |
| `extraHead` | string | Custom HTML in `<head>` | - |
| `extraBody` | string | Custom HTML in `<body>` | - |
| `extraCSSFiles` | array | Additional CSS files to load | `[]` |
| `staticPrefix` | string | CDN prefix for static assets | `""` |
| `twitterCards` | boolean | Enable Twitter Cards meta tags | `false` |
| `author.name` | string | Author name | - |
| `author.homepage` | string | Author homepage URL | - |
| `socials` | array | Social links (name + link) | `[]` |

### Head Title

```toml
[params]
headTitle = "Joway Wang"
```

If there is no `headTitle` in params, use `.Site.Params.author.name`.

### Main section

Set your main section:

```toml
[params]
mainSections = ["posts"]
```

### Multi-Language

Hugo's multi-language support with theme providing:
- Language switcher in header
- Per-language content directories

```toml
[languages]
  [languages.en]
    contentDir = "content/en"
    languageName = "English"
    weight = 1
  [languages.cn]
    contentDir = "content/cn"
    languageName = "Chinese"
    weight = 2
```

### Footer

```toml
[[params.socials]]
name = "About Me"
link = "https://joway.io"
[[params.socials]]
name = "Github"
link = "https://github.com/joway"
```

### Extra Head

```toml
[params]
extraHead = '<script src="xxxx.js"></script>'
```

### Extra CSS files

```toml
[params]
extraCSSFiles = ["css/foo.css", "css/bar.css"]
```

### Twitter Cards

Add the following setting:

```toml
[params]
twitterCards = true
```

In a post's front matter, include a keyword `images` with a value of a list of
URLs of images that will be used for Twitter Cards.

### Code Copy Button

Enable copy-to-clipboard buttons on code blocks:

```toml
[params]
enableCopyCode = true
```

Can also be enabled per-post via front matter:

```yaml
---
enableCopyCode: true
---
```

### Lazy Image Loading

Enable lazy loading for images to improve performance:

```toml
[params]
lazyImage = true
```

### Gallery Layout

Create a gallery page by setting the type to `gallery` and adding images:

```yaml
---
type: gallery
title: "My Photo Gallery"
gallery:
  - url: "/images/photo1.jpg"
    name: "Photo 1 Description"
  - url: "/images/photo2.jpg"
    name: "Photo 2 Description"
---
```

### Dark Mode

- **Toggle button**: Header button with 🌙/☀️ indicator

No configuration needed - works out of the box!

### Insert content on every post

```toml
[params]
postHeaderContent = ""
postFooterContent = "<br/><br/><p>Subscribe：<a target='_blank' href='https://mailchi.mp/a1a0d59e7a19/joway'>Joway's Blog</a></p>"
```

### CDN/Static Prefix

Use a CDN for static assets:

```toml
[params]
staticPrefix = "https://cdn.jsdelivr.net/gh/username/repo"
```

### Related Posts Configuration

Theme shows up to 3 related posts. Configure Hugo's related content algorithm:

```toml
[related]
includeNewer = true
threshold = 80
toLower = false
[[related.indices]]
name = "date"
weight = 100
[[related.indices]]
name = "keywords"
weight = 100
```

### Complete Configuration Example

```toml
# ---------- Site ----------
baseURL = "https://blog.joway.io/"
languageCode = "en-us"
theme = "yinyang"
title = "Random Thoughts"
DefaultContentLanguage = "cn"
canonifyURLs = false
enableRobotsTXT = true

# ---------- Content Language ----------
[languages]
# [languages.en]
#   contentDir = "content/en"
#   languageName = "English"
#   weight = 1
[languages.cn]
contentDir = "content/cn"
languageName = "简体中文"
weight = 2

# ---------- URL ----------
[permalinks]
post = "/blog/:title/"

# ---------- Markdown / Highlight ----------
[markup]
[markup.goldmark]
[markup.goldmark.renderer]
unsafe = true
[markup.highlight]
guessSyntax = true
noClasses = false
style = "tango"
tabWidth = 2

# ---------- Theme Params ----------
[params]
description = "Log something useless, but interesting." 
disqus = "joway" # disqus account name
extraHead = ''
favicon = "/logo.png" 
headTitle = "Random Thoughts" 
mainSections = ["posts"] 
postFooterContent = '<br/><br/><p>Subscribe：<a target="_blank" href="https://mailchi.mp/a1a0d59e7a19/joway"><b>Mailchimp</b></a></p><br/><a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://blog.joway.io/images/cc.png" /></a>' 
postHeaderContent = "" 
staticPrefix = "https://cdn.jsdelivr.net/gh/joway/blog" 
# extraBody = '<script>(adsbygoogle = window.adsbygoogle || []).push({});</script>'
# postAds = '<ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-6400651395935595" data-ad-slot="5705651853" data-ad-format="auto" data-full-width-responsive="true"></ins>'
lazyImage = true
enableCopyCode = true

# ---------- Analytics ----------
[services]
  [services.googleAnalytics]
    id = "" # e.g. G-XXXXXXXXXX

# ---------- Author ----------
[params.author]
homepage = "https://joway.io/"
name = "Joway"

# ---------- Social Links ----------
# [[params.socials]]
# name = "Telegram"
# link = "https://t.me/biosthinking"

# [[params.socials]]
# name = "RSS"
# link = "/index.xml"

# [[params.socials]]
# name = "Slides"
# link = "/presentations"

[[params.socials]]
link = "https://mailchi.mp/a1a0d59e7a19/joway"
name = "Subscribe"
[[params.socials]]
link = "/travel"
name = "Travel"
[[params.socials]]
link = "https://joway.io"
name = "About"

# ---------- Optional: Related Posts ----------
# [related]
# includeNewer = true
# threshold = 80
# toLower = false
# [[related.indices]]
# name = "date"
# weight = 100
# [[related.indices]]
# name = "keywords"
# weight = 100
```

## License

MIT License - See LICENSE.md for details
