---
title: Hexo Customization
mathjax: true
date: 2019-12-31 14:01:47
tags: Hexo
description: How to create a page in the menu?
---

### How to create a new page in the menu?

```shell
hexo new page "about"
```

Then change the `_config.yml` under the theme folder

```shell
menu:
  home: /
  archives: /archives
  tags: /tags
  about: /about
```

If the page is not available in `_config.yml`, e.g. Blog page, the type must be set in the `index.md` file.

```shell
title: Blog
date: 2019-12-31 14:04:49
type: "Blog"
```

