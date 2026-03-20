# YinYang

[YinYang](https://en.wikipedia.org/wiki/Yin_and_yang) is a minimalist, elegant theme for [Hugo](https://gohugo.io/) with a warm, vintage aesthetic inspired by traditional Chinese philosophy.

[**Demo**](https://blog.joway.io)

## Features

- **Dual Theme Support** - Automatic light/dark mode with manual toggle (respects system preferences)
- **Multi-language Support** - Built-in support for multilingual content
- **Responsive Design** - Mobile-first design with flexbox grid
- **Disqus Comments** - Integrated comment system support
- **SEO Optimized** - JSON-LD structured data, Open Graph, and Twitter Cards
- **Gallery Layout** - Special layout for photo galleries
- **Related Posts** - Automatic related content suggestions
- **Code Copy Button** - Optional one-click code block copying
- **Lazy Loading** - Optional image lazy loading for better performance
- **Custom CSS/JS** - Easy addition of extra stylesheets and scripts
- **Vintage Aesthetic** - Warm color palette with serif typography (Lora & Playfair Display fonts)

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

### Basic Configuration

#### Head Title

```toml
[params]
headTitle = "Joway Wang"
```

The title displayed in the header. If not set, defaults to `.Site.Params.author.name`.

#### Main Section

Define which content sections to display on the homepage:

```toml
[params]
mainSections = ["posts"]
```

### Theme Switching

The theme automatically respects your system's dark/light mode preference and provides a manual toggle button (🌙/☀️) in the header. Theme preference is saved in localStorage.

### Multi-Language Support

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

Place your content files in the respective language directories (`content/en`, `content/cn`, etc.).

### Social Links & Footer

Add links to the header navigation:

```toml
[[params.socials]]
name = "About Me"
link = "https://joway.io"
[[params.socials]]
name = "Github"
link = "https://github.com/joway"
```

### Gallery Layout

Create a gallery page with a special layout:

```toml
+++
title = "My Gallery"
type = "gallery"

[[gallery]]
url = "/images/photo1.jpg"
name = "Photo 1 Description"

[[gallery]]
url = "/images/photo2.jpg"
name = "Photo 2 Description"
+++
```

### Related Posts

Related posts are automatically displayed at the bottom of each article. To customize the related posts algorithm, add to your config:

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

### Code Copy Button

Enable copy buttons on code blocks:

```toml
[params]
enableCopyCode = true
```

Can also be enabled per-page in front matter:

```yaml
---
enableCopyCode: true
---
```

### Lazy Loading Images

Enable lazy loading for images to improve page performance:

```toml
[params]
lazyImage = true
```

### Extra Head & Body Content

Add custom scripts or styles to the `<head>` or before closing `</body>` tag:

```toml
[params]
extraHead = '<script src="xxxx.js"></script>'
extraBody = '<script>console.log("Custom script")</script>'
```

### Extra CSS Files

Load additional CSS files (place them in your site's `static/` directory):

```toml
[params]
extraCSSFiles = ["css/foo.css", "css/bar.css"]
```

### Static Assets Prefix (CDN Support)

Use a CDN or custom domain for static assets:

```toml
[params]
staticPrefix = "https://cdn.jsdelivr.net/gh/username/repo"
```

### Favicon

```toml
[params]
favicon = "/logo.png"
```

### SEO & Analytics

#### Twitter Cards

Enable Twitter Card meta tags:

```toml
[params]
twitterCards = true
```

In a post's front matter, include images for Twitter Cards:

```yaml
---
images:
  - /images/post-image.jpg
---
```

#### Google Analytics

```toml
[services]
  [services.googleAnalytics]
    id = "G-XXXXXXXXXX"
```

### Content Injection

#### Per-Post Header/Footer Content

Inject content at the beginning or end of every post:

```toml
[params]
postHeaderContent = "<p>Support my work!</p>"
postFooterContent = "<p>Subscribe: <a href='https://example.com'>Newsletter</a></p>"
```

#### Post Advertisements

Insert ads or custom content in posts:

```toml
[params]
postAds = '<div class="ad-container">Your ad code here</div>'
```

### Disqus Comments

Enable Disqus comments:

```toml
[params]
disqus = "your-disqus-shortname"
```

## Complete Configuration Example

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
  [languages.en]
    contentDir = "content/en"
    languageName = "English"
    weight = 1
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
  disqus = "your-disqus-shortname"
  extraHead = ''
  favicon = "/logo.png" 
  headTitle = "Random Thoughts" 
  mainSections = ["posts"] 
  postFooterContent = '<p>Subscribe: <a target="_blank" href="https://example.com">Newsletter</a></p>' 
  postHeaderContent = "" 
  staticPrefix = ""
  lazyImage = true
  enableCopyCode = true
  twitterCards = true

# ---------- Analytics ----------
[services]
  [services.googleAnalytics]
    id = "G-XXXXXXXXXX"

# ---------- Author ----------
[params.author]
  homepage = "https://joway.io/"
  name = "Joway"

# ---------- Social Links ----------
[[params.socials]]
  link = "https://example.com/subscribe"
  name = "Subscribe"
[[params.socials]]
  link = "/about"
  name = "About"
[[params.socials]]
  name = "RSS"
  link = "/index.xml"

# ---------- Optional: Related Posts ----------
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

## License

MIT License - see [LICENSE.md](LICENSE.md) for details.

## Credits

- Original theme by [Joway Wang](https://joway.io)
- Fonts: [Lora](https://fonts.google.com/specimen/Lora) and [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) from Google Fonts
- Inspired by the philosophy of [Yin and Yang](https://en.wikipedia.org/wiki/Yin_and_yang)
