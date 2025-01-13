# Hugo ATOM Feed

English | [中文](/README.md)

> Hugo theme component for ATOM feed custom Output Format.

This component enables ATOM feeds for your site.

## Install Component

The installation method is the same as [installing a theme](https://fixit.lruihao.cn/documentation/installation/). There are several ways to install, choose one, for example, install through Hugo Modules:

```diff
[module]
  [[module.imports]]
    path = "github.com/hugo-fixit/FixIt"
+ [[module.imports]]
+   path = "github.com/hugo-fixit/hugo-atom-feed"
```

## Configuration

Add "atom" to all the Page Kinds for which you want to create ATOM feeds:

```toml
[outputs]
  # <baseURL>/atom.xml
  home = ["html", "rss", "atom"]
  # <baseURL>/posts/atom.xml etc.
  section = ["html", "rss", "atom"]
  # <baseURL>/tags/foo/atom.xml etc.
  term = ["html", "rss", "atom"]
```

If your site uses multiple theme components, you need to merge the `outputs` configuration of all theme components. For example, if your site uses both the `FixIt` and `hugo-atom-feed` theme components, you need to merge the `outputs` configuration of the two theme components:

```toml
[outputs]
  _merge = "shallow"
  home = ["html", "rss", "atom", "archives", "offline", "readme", "baidu_urls", "search"]
  page = ["html", "markdown"]
  section = ["html", "rss", "atom"]
  taxonomy = ["html"]
  term = ["html", "rss", "atom"]
```

### Parameters

You can set the following parameters in your site configuration file:

```toml
[params]
  # Global Feed config for ATOM feed.
  [params.feed]
    # The number of posts to include in the feed. If set to -1, all posts.
    limit = 10
    # whether to show the full text content in feed.
    fullText = true

  # Section page config (all pages in section)
  [params.section]
    # Section feed config for ATOM feed.
    [params.section.feed]
      # The number of posts to include in the feed. If set to -1, all posts.
      limit = -1
      # whether to show the full text content in feed.
      fullText = false

  # Term list (category or tag) page config
  [params.list]
    # Term list feed config for ATOM feed.
    [params.list.feed]
      # The number of posts to include in the feed. If set to -1, all posts.
      limit = -1
      # whether to show the full text content in feed.
      fullText = false
```

### Front Matter

You can set the following parameters in the front matter of the content file:

```yaml
---
title: "Hello World"
date: 2024-08-24T16:06:33+08:00
hiddenFromFeed: true
feed:
  # feed.limit only invalid in section or term page(_index.md).
  limit: 10
  fullText: true
---
```
