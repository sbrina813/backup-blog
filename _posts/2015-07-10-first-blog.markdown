---
layout: post
title:  "Aha, this is my first blog"
date:   2015-07-10 21:47:49
categories: interests
---
###以下功能还需要修改一下下

### 搜索功能

搜索框目前只是摆设，请使用 [Google Custom Search Engine](https://www.google.com/cse/) 或 [jekyll-lunr-js-search](https://github.com/slashdotdash/jekyll-lunr-js-search) 插件。

### 修改邮箱

通过 [Stop Link Spam Bots](http://www.safeemail.org/) 编辑了邮箱地址，希望能防 spam。

### Embedding Codepen

如果需要插入 Codepen，只需将 embed code 中的 `<p>` 部分粘贴在正文中，而不必粘贴 `<script>` 部分。更多关于插入 Codepen 的解释请查看 http://blog.codepen.io/documentation/features/how-do-i-embed-a-pen-on-another-site/ 。

如果完全不需要这个功能可以将 `/assets/js/script.js` 中的相关代码删除。

### 修改分享链接地址

打开 `/_layouts/post.html` 将分享链接中的 `place_your_url_here` 提换成博客地址。

### 修改许可协议

在 `/_layouts/post.html` 文件的分享链接部分声明博客内容所使用的许可协议，默认使用 [Attribution-NonCommercial-ShareAlike 3.0 Unported](http://creativecommons.org/licenses/by-nc-sa/3.0/)。

### 设置 RSS

请不要忘记编辑 `rss.xml` 文件，语言可填 `zh-cn` 或 `zh-tw`。
