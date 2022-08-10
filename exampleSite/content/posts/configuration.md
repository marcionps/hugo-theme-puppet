+++
title = "Puppet - User Guide"
date = 2022-08-09T19:04:45+08:00
draft = true
header_img = "/img/home-bg.jpg"
subtitle = "say hello to the world"
short = true
toc = true
tags = ["documentation"]
categories = []
series = ["Themes Guide"]
+++

Customize the theme by editing the `config.toml` file.

<!--more-->

## Site Configuration

the complete configuration file is as follows:

```toml
baseURL = "http://localhost:1313/"
title = "Puppet Theme"
theme = "puppet"

paginate = 3 # Number of items per page in paginated lists
languageCode = "en"
defaultContentLanguage = "en"
# whether to include Chinese/Japanese/Korean
hasCJKLanguage = true
enableInlineShortcodes = true
enableEmoji = true
# prevent build failures when using Hugo's Instagram shortcode due to deprecated Instagram API.
# See https://github.com/gohugoio/hugo/issues/7228#issuecomment-714490456
ignoreErrors = ["error-remote-getjson"]

disqusShortname = ""
googleAnalytics = ""

[outputs]
home = ["HTML", "JSON", "RSS"]

# prevent build failures when using Hugo's template _internal/opengraph.html 
[taxonomies]
category = "categories"
tag = "tags"
series = "series"

[markup]
[markup.highlight]
codeFences = true
guessSyntax = true
lineNos = true
lineNumbersInTable = false
style = "dracula"

[markup.goldmark.renderer]
unsafe = true

[menu]
[[menu.main]]
identifier = "home" # the identifier of the menu item
name = "Home"
url = "/"
weight = -100 # the weight of the menu item. Less weight items will be displayed first.


[params]
author = "Puppet" # default author
description = "A simple and clean theme for Hugo" # site description
keywords = "blog,developer,personal"
img_home = "/img/home-bg.jpg" # home page header image
img_404 = "/img/404-bg.jpg" # 404 page background image

useFaviconGenerator = true # use favicon generator

custom_js = []
custom_css = [] # ["css/custom.css"]  Add your file to assets folder  [assets/css/custom.css]

[params.sidebar]
enable = true 
avatar = "/img/home-bg.jpg"
bio = "a personal website"

[params.social]
rss_enable = true
twitter = "johndoe"
facebook = "johndoe"
zhihu = "johndoe"
weibo = "johndoe"
github = "johndoe"
linkedin = "johndoe"

[[params.friends]]
name = "John Doe"
url = "https://gohugo.io"

# See https://giscus.app/
[params.giscus]
enable = true
repo = "roninro/hugo-theme-puppet"
repo_id = "R_kgDOHuvyhw"
category = "General"
category_id = "DIC_kwDOHuvyh84CQjDo"
input_position = "top"
theme = "light_tritanopia"
lang = "en"
```

## Favicons

### Not using favicon generator

Just put your `favicon.ico` files in the `static` folder of your site.

### Using favicon generator

1. Set the `useFaviconGenerator` parameter to `true` in the `config.toml` file.

    ```toml
    [params]
    useFaviconGenerator = true
    ```

2. Generate your favicon at [favicon.io](https://favicon.io/favicon-converter/).
3. Place the files in the `static` of your website root directory.
    
    - android-chrome-192x192.png
    - android-chrome-512x512.png
    - apple-touch-icon.png
    - favicon-16x16.png
    - favicon-32x32.png
    - favicon.ico
    - site.webmanifest

## Customization of CSS and JS

Add your file to assets folder. Filename must match with config params you set above

```
assets/scss/custom.scss
assets/css/custom.css
assets/js/custom.js
```
Add custom css and js files to `config.toml`

```toml
[params]
custom_css = ["css/custom.css"]
custom_js = ["js/custom.js", ...]
```

## Syntax Highlighting

This the default `highlight` configuration.

```toml
[markup]
[markup.highlight]
codeFences = true
guessSyntax = true
lineNos = true
lineNumbersInTable = false
style = "dracula"
```

### Customizing the Highlight Style

with `markup.highlight.noClasses=false` in your site config, you need a style sheet.

You can generate one with Hugo:

```bash
hugo gen chromastyles --style=dracula > syntax.css
```

You can also use the [Chroma Style Gallery](https://xyproto.github.io/splash/docs/all.html) to generate a style sheet.


## Search

In order to generate `index.json` for searching, add JSON output file type to the home of the outputs part in your site configuration.

```toml
[outputs]
  home = ["HTML", "RSS", "JSON"]
```

## Comments

Puppet Theme supports [Disqus](https://disqus.com/) and [Giscus](https://giscus.app/).


## Pages

### Regular Pages

a regular page can contain other pages, images etc. as resources Basically all files in the same folder and below will be part of a bundle.<br />
such as `content/posts/my-first-hugo-post.md` or `content/posts/my-first-hugo-post/index.md`

### Archive Page

The archive page is a list of all posts in your site. It is generated by the `layouts/section/archive.html` template.

Add `archive/_index.md` file to your `content` folder.

```markdown
+++
title = "Archive"
description = "Archive"
header_img = "/img/archive-bg.jpg"
short = true
+++
```

### About Page

like archive page, add `about/_index.md` file to your `content` folder.

```markdown
+++
title = "About"
description = "Hugo, the world's fastest framework for building websites"
header_img = "/img/about-bg.jpg"
short = false
+++

# About

content here
```